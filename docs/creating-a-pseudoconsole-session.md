---
title: Creazione di una sessione di pseudoconsole
description: Una sessione di pseudoconsole consentirà a un'applicazione di ospitare le attività di un'applicazione in modalità carattere
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console, pseudoconsole, windows pty, pseudo console
ms.localizationpriority: high
ms.openlocfilehash: c1a83b308e4d9a23fdb6b2778561030e619dfdb3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357931"
---
# <a name="creating-a-pseudoconsole-session"></a>Creazione di una sessione di pseudoconsole

Windows Pseudoconsole, talvolta denominato anche pseudoconsole, ConPTY o Windows PTY, è un meccanismo progettato per la creazione di un host esterno per le attività di sottosistema in modalità carattere che sostituiscono la parte di interattività utente della finestra predefinita dell'host della console.

L'hosting di una sessione di pseudoconsole è leggermente diverso rispetto a quello di una sessione di console tradizionale. Mentre le sessioni di console tradizionali vengono avviate automaticamente quando il sistema operativo riconosce l'imminente esecuzione di un'applicazione in modalità carattere, l'hosting di una sessione di pseudoconsole e dei rispettivi canali di comunicazione richiede che questi vengano creati dall'applicazione di hosting prima della creazione del processo con l'applicazione figlio in modalità carattere. Il processo figlio verrà comunque creato tramite la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), ma con alcune informazioni aggiuntive che consentiranno al sistema operativo di mettere a punto l'ambiente appropriato.

Altre informazioni di carattere generale su questo sistema sono disponibili nel [post di blog relativo all'annuncio iniziale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Esempi completi di utilizzo della pseudoconsole sono disponibili nel repository GitHub [microsoft/terminal](https://github.com/microsoft/terminal) disponibile nella directory degli esempi.

## <a name="preparing-the-communication-channels"></a>Preparazione dei canali di comunicazione

Il primo passaggio prevede la creazione di una coppia di canali di comunicazione sincrona che verranno messi a disposizione durante la creazione della sessione di pseudoconsole per la comunicazione bidirezionale con l'applicazione ospitata. Questi canali vengono elaborati dal sistema di pseudoconsole tramite [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) con [I/O sincrono](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Sono accettati anche handle di file o dispositivi di I/O, ad esempio un flusso di file o una pipe, a condizione che non sia necessaria una struttura [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) per la comunicazione asincrona.

> [!WARNING]
>Per evitare race condition e deadlock, inoltre, è consigliabile che ogni canale di comunicazione venga gestito in un thread separato in grado di mantenere lo stato del buffer client e la coda di messaggistica all'interno dell'applicazione. Se si gestissero tutte le attività della pseudoconsole sullo stesso thread, infatti, potrebbe verificarsi un deadlock in cui uno dei buffer di comunicazione si riempie e resta in attesa di un'azione dell'utente mentre tenta di inviare una richiesta di blocco su un altro canale.

## <a name="creating-the-pseudoconsole"></a>Creazione di una pseudoconsole

Con i canali di comunicazione correttamente creati, identificare ora l'estremità "read" del canale di input e l'estremità "write" del canale di output. Questa coppia di handle viene fornita quando si chiama [**CreatePseudoConsole**](createpseudoconsole.md) per creare l'oggetto.

Al momento della creazione, è necessario specificare le dimensioni delle assi X e Y (in numero di caratteri). Si tratta delle dimensioni che verranno applicate alla superficie di visualizzazione nella finestra di presentazione finale (terminale). Quesiti valori vengono usati anche per creare un buffer di memoria all'interno del sistema di pseudoconsole.

Le dimensioni del buffer forniscono risposte alle applicazioni in modalità carattere client che cercano informazioni attraverso le [funzioni della console lato client](console-functions.md) come [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) e stabiliscono il layout e il posizionamento del testo nei casi in cui i client si avvalgano di funzioni come [**WriteConsoleOutput**](writeconsoleoutput.md).

Durante la creazione di un pseudoconsole, infine, viene fornito un campo Flags per l'esecuzione di funzionalità speciali. Per impostazione predefinita, questo campo è impostato su 0 per indicare che non sono disponibili funzionalità speciali.

A questo punto, è disponibile un solo flag speciale per richiedere l'ereditarietà della posizione del cursore da una sessione della console già collegata al chiamante dell'API della pseudoconsole. L'utilizzo di questo flag è destinato tuttavia a scenari più avanzati in cui un'applicazione host che prepara una sessione di pseudoconsole è anche un'applicazione in modalità carattere client di un altro ambiente console.

Di seguito è riportato un frammento di codice di esempio in cui viene usato il comando [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) per mettere a punto una coppia di canali di comunicazione e creare la pseudoconsole.

```C

HRESULT SetUpPseudoConsole(COORD size)
{
    HRESULT hr = S_OK;

    // Create communication channels

    // - Close these after CreateProcess of child application with pseudoconsole object.
    HANDLE inputReadSide, outputWriteSide;

    // - Hold onto these and use them for communication with the child through the pseudoconsole.
    HANDLE outputReadSide, inputWriteSide;

    if (!CreatePipe(&inputReadSide, &inputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    if (!CreatePipe(&outputReadSide, &outputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    HPCON hPC;
    hr = CreatePseudoConsole(size, inputReadSide, outputWriteSide, 0, &hPC);
    if (FAILED(hr))
    {
        return hr;
    }

    // ...

}
```

> [!NOTE]
>Questo frammento di codice è incompleto e viene usato esclusivamente a titolo dimostrativo di questa chiamata specifica. Sarà necessario gestire il ciclo di vita degli oggetti **HANDLE** in modo appropriato. In caso contrario, è possibile che si verifichino scenari di deadlock, soprattutto con chiamate di I/O sincrone.

Al termine della chiamata [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con cui si crea l'applicazione in modalità carattere client collegata alla pseudoconsole, gli handle specificati durante la creazione devono essere liberati dal processo. In questo modo si riduce il conteggio dei riferimenti nell'oggetto dispositivo sottostante e si consente alle operazioni di I/O di rilevare correttamente un canale interrotto nel momento in cui la sessione pseudoconsole chiude la copia degli handle.

## <a name="preparing-for-creation-of-the-child-process"></a>Preparazione per la creazione del processo figlio

La fase successiva prevede la preparazione della struttura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) che consente la comunicazione di informazioni sulla pseudoconsole durante l'avvio del processo figlio.

Questa struttura offre infatti la possibilità di fornire informazioni di avvio complesse, inclusi attributi per la creazione di processi e thread.

Usare [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in modalità doppia chiamata per calcolare il numero di byte necessari per contenere l'elenco, allocare la memoria necessaria e quindi chiamare di nuovo specificando il puntatore di memoria opaco per impostarlo come elenco di attributi.

Chiamare quindi [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passando l'elenco degli attributi inizializzato con il flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, l'handle della pseudoconsole e le relative dimensioni.

```C

HRESULT PrepareStartupInformation(HPCON hpc, STARTUPINFOEX* psi)
{
    // Prepare Startup Information structure
    STARTUPINFOEX si;
    ZeroMemory(&si, sizeof(si));
    si.StartupInfo.cb = sizeof(STARTUPINFOEX);

    // Discover the size required for the list
    size_t bytesRequired;
    InitializeProcThreadAttributeList(NULL, 1, 0, &bytesRequired);

    // Allocate memory to represent the list
    si.lpAttributeList = (PPROC_THREAD_ATTRIBUTE_LIST)HeapAlloc(GetProcessHeap(), 0, bytesRequired);
    if (!si.lpAttributeList)
    {
        return E_OUTOFMEMORY;
    }

    // Initialize the list memory location
    if (!InitializeProcThreadAttributeList(si.lpAttributeList, 1, 0, &bytesRequired))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // Set the pseudoconsole information into the list
    if (!UpdateProcThreadAttribute(attributeList,
                                   0,
                                   PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE,
                                   hpc,
                                   sizeof(hpc),
                                   NULL,
                                   NULL))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    *psi = si;

    return S_OK;
}

```

## <a name="creating-the-hosted-process"></a>Creazione del processo ospitato

A questo punto, chiamare [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) passando la struttura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) contestualmente al percorso del file eseguibile e a eventuali informazioni di configurazione aggiuntive. È importante impostare il flag **EXTENDED_STARTUPINFO_PRESENT** quando si chiama per informare il sistema che il riferimento alla pseudoconsole è contenuto nelle informazioni estese.

```C
HRESULT SetUpPseudoConsole(COORD size)
{
    // ...

    PCWSTR childApplication = L"C:\\windows\\system32\\cmd.exe";

    // Create mutable text string for CreateProcessW command line string.
    const size_t charsRequired = wcslen(childApplication) + 1; // +1 null terminator
    PWSTR cmdLineMutable = (PWSTR)HeapAlloc(GetProcessHeap(), 0, sizeof(wchar_t) * charsRequired);

    if (!cmdLineMutable)
    {
        return E_OUTOFMEMORY;
    }

    wcscpy_s(cmdLineMutable, bytesRequired, childApplication);

    PROCESS_INFORMATION pi;
    ZeroMemory(&pi, sizeof(pi));

    // Call CreateProcess
    if (!CreateProcessW(NULL,
                        cmdLineMutable,
                        NULL,
                        NULL,
                        FALSE,
                        EXTENDED_STARTUPINFO_PRESENT,
                        NULL,
                        NULL,
                        &siEx.StartupInfo,
                        &pi))
    {
        HeapFree(GetProcessHeap(), 0, cmdLineMutable);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // ...
}
```

> [!NOTE]
> Se si chiude la sessione della pseudoconsole mentre il processo ospitato è ancora in fase di avvio e connessione, è possibile che nell'applicazione client venga visualizzata una finestra di dialogo di errore. La stessa finestra di errore viene visualizzata se al processo ospitato viene fornito un handle della pseudoconsole non valido per l'avvio. Per il codice di inizializzazione del processo ospitato, le due circostanze sono identiche. Nella finestra di dialogo popup visualizzata nell'applicazione client ospitata verrà visualizzato il codice di errore `0xc0000142` con un messaggio localizzato in cui sono riportate informazioni sui motivi dell'errore di inizializzazione.

## <a name="communicating-with-the-pseudoconsole-session"></a>Comunicazione con la sessione della pseudoconsole

Una volta completata la creazione del processo, l'applicazione host può usare l'estremità write della pipe di input per inviare informazioni di interazione utente alla pseudoconsole e l'estremità end della pipe di output per ricevere da questa informazioni di presentazione grafica.

È l'applicazione host a decidere come dovranno essere gestite le attività successive. L'applicazione host, ad esempio, può avviare una finestra in un altro thread per raccogliere l'input di interazione utente e serializzarlo nell'estremità write della pipe di input sia per la pseudoconsole che per l'applicazione in modalità carattere ospitata. Oppure, può avviare un altro thread per svuotare l'estremità read della pipe di output per la pseudoconsole, decodificare il testo e le informazioni sulla [sequenza di terminale virtuale](console-virtual-terminal-sequences.md) e presentarle sullo schermo.

I thread possono essere usati anche per inoltrare informazioni dai canali della pseudoconsole a un canale o un dispositivo diverso, inclusa una rete, in modo da inviare informazioni in remoto un altro processo o computer ed evitare così la transcodifica locale delle informazioni.

## <a name="resizing-the-pseudoconsole"></a>Ridimensionamento della pseudoconsole

Nel corso del runtime è possibile che si creino le circostanze per le quali risulta necessario modificare le dimensioni del buffer a causa di un'interazione utente o una richiesta ricevuta fuori banda da un altro dispositivo di visualizzazione/interazione.

Questa operazione può essere eseguita mediante la funzione [**ResizePseudoConsole**](resizepseudoconsole.md) specificando l'altezza e la larghezza del buffer in numero di caratteri.

```C
// Theoretical event handler function with theoretical
// event that has associated display properties
// on Source property.
void OnWindowResize(Event e)
{
    // Retrieve width and height dimensions of display in
    // characters using theoretical height/width functions
    // that can retrieve the properties from the display
    // attached to the event.
    COORD size;
    size.X = GetViewWidth(e.Source);
    size.Y = GetViewHeight(e.Source);

    // Call pseudoconsole API to inform buffer dimension update
    ResizePseudoConsole(m_hpc, size);
}
```

## <a name="ending-the-pseudoconsole-session"></a>Conclusione della sessione della pseudoconsole

Per terminare la sessione, chiamare la funzione [**ClosePseudoConsole**](closepseudoconsole.md) con l'handle usato per la creazione della pseudoconsole originale. Eventuali applicazioni in modalità carattere client collegate, ad esempio quelle create con il comando [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), verranno terminate nel momento in cui viene chiusa la sessione. Se l'elemento figlio originale era un'applicazione di tipo Shell da cui vengono creati altri processi, verranno terminati anche tutti gli eventuali processi collegati presenti nell'albero.

> [!WARNING]
>La chiusura della sessione presenta diversi effetti collaterali che possono determinare una condizione di deadlock se la pseudoconsole viene usata in modalità sincrona a thread singolo. L'operazione di chiusura della sessione di pseudoconsole può generare un aggiornamento finale dei frame per `hOutput`, che deve essere rimosso dal buffer del canale di comunicazione. Se, inoltre, è stato selezionato `PSEUDOCONSOLE_INHERIT_CURSOR` durante la creazione della pseudoconsole, il tentativo di chiudere la pseudoconsole senza rispondere al messaggio di query sull'ereditarietà del cursore (ricevuto su `hOutput` e a cui è stata inviata una risposta tramite `hInput`) può generare un'altra condizione di deadlock. È questo il motivo per cui è consigliabile che i canali di comunicazione della pseudoconsole vengano gestiti su singoli thread e rimangano svuotati ed elaborati fino a quando non vengono interrotti dall'applicazione client in uscita o dal completamento delle attività di disinstallazione durante la chiamata della funzione [**ClosePseudoConsole**](closepseudoconsole.md).