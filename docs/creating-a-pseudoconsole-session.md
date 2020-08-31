---
title: Creazione di una sessione Pseudoconsole
description: Una sessione pseudoconsole consentirà a un'applicazione di ospitare le attività di un'applicazione in modalità carattere
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole, Windows Pty, pseudo console
ms.openlocfilehash: ec63cf4bfc1502aa37b0b336f1ffdc7bab2be07e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059905"
---
# <a name="creating-a-pseudoconsole-session"></a>Creazione di una sessione Pseudoconsole

Windows Pseudoconsole, talvolta noto anche come pseudo-console, ConPTY o Windows PTY, è un meccanismo progettato per la creazione di un host esterno per le attività del sottosistema in modalità carattere che sostituiscono la parte dell'interattività utente della finestra host della console predefinita.

L'hosting di una sessione pseudoconsole è leggermente diverso rispetto a una sessione console tradizionale. Le sessioni console tradizionali vengono avviate automaticamente quando il sistema operativo riconosce l'esecuzione di un'applicazione in modalità carattere. Al contrario, una sessione pseudoconsole e i canali di comunicazione devono essere creati dall'applicazione host prima di creare il processo con l'applicazione in modalità carattere figlio da ospitare. Il processo figlio verrà comunque creato utilizzando la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , ma con alcune informazioni aggiuntive che configureranno il sistema operativo per stabilire l'ambiente appropriato.

Per ulteriori informazioni complementari sul sistema, vedere il post di [Blog relativo all'annuncio iniziale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Esempi completi di uso di Pseudoconsole sono disponibili nel repository GitHub [Microsoft/console](https://github.com/Microsoft/console) nella directory degli esempi.

## <a name="preparing-the-communication-channels"></a>Preparazione dei canali di comunicazione

Il primo passaggio consiste nel creare una coppia di canali di comunicazione sincrona che verranno forniti durante la creazione della sessione pseudoconsole per la comunicazione bidirezionale con l'applicazione ospitata. Questi canali vengono elaborati dal sistema pseudoconsole usando [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) con [i/O sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Gli handle di un file o di un dispositivo di I/O come un flusso di file o una pipe sono accettabili purché non sia necessaria una struttura [**sovrapposta**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) per la comunicazione asincrona.

**Si noti**

Per evitare race condition e deadlock, è consigliabile che ogni canale di comunicazione venga servito in un thread separato che gestisce lo stato del buffer client e la coda di messaggistica all'interno dell'applicazione. La manutenzione di tutte le attività pseudoconsole sullo stesso thread può comportare un deadlock in cui uno dei buffer di comunicazione viene riempito e in attesa dell'azione quando si tenta di inviare una richiesta di blocco su un altro canale.

## <a name="creating-the-pseudoconsole"></a>Creazione di Pseudoconsole

Con i canali di comunicazione che sono stati stabiliti, identificare la fine "lettura" del canale di input e l'estremità "Write" del canale di output. Questa coppia di handle viene fornita nella chiamata a [**CreatePseudoConsole**](createpseudoconsole.md) per creare l'oggetto.

Quando si crea, viene fornita anche una dimensione che rappresenta le dimensioni X e Y (in Count of characters). Si tratta delle dimensioni che verranno applicate alla superficie di visualizzazione per la finestra di presentazione finale (terminale). I valori vengono usati per creare un buffer in memoria all'interno del sistema pseudoconsole. 

Le dimensioni del buffer forniscono risposte alle applicazioni in modalità carattere client che verificano le informazioni usando le [funzioni console lato client](console-functions.md) come [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) e stabiliscono il layout e il posizionamento del testo quando i client usano funzioni come [**WriteConsoleOutput**](writeconsoleoutput.md).

Infine, viene fornito un campo Flags durante la creazione di un pseudoconsole per eseguire funzionalità speciali. Per impostazione predefinita, impostare questa opzione su 0 per non avere funzionalità speciali.

A questo punto, è disponibile un solo flag speciale per richiedere il eredità della posizione del cursore da una sessione della console già associata al chiamante dell'API pseudoconsole. Questa operazione è destinata all'uso in scenari più avanzati in cui un'applicazione host che prepara una sessione pseudoconsole è anche un'applicazione in modalità carattere client di un altro ambiente console. 

Di seguito è riportato un frammento di codice di esempio che usa [**non**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) per stabilire una coppia di canali di comunicazione e creare il pseudoconsole.

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


**NOTA**: 

Questo frammento di codice è incompleto e viene utilizzato solo per la dimostrazione di questa specifica chiamata. Sarà necessario gestire la durata dell' **handle**in modo appropriato. La mancata gestione corretta della durata degli **handle**può causare scenari di deadlock, soprattutto con le chiamate di I/O sincrone.

Al termine della chiamata a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) per creare l'applicazione in modalità carattere client collegata a pseudoconsole, gli handle specificati durante la creazione devono essere liberati da questo processo. In questo modo si riduce il conteggio dei riferimenti nell'oggetto dispositivo sottostante e si consentono alle operazioni di I/O di rilevare correttamente un canale interrotto quando la sessione pseudoconsole chiude la copia degli handle.

## <a name="preparing-for-creation-of-the-child-process"></a>Preparazione per la creazione del processo figlio

La fase successiva consiste nel preparare la struttura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) che comunicherà le informazioni di pseudoconsole durante l'avvio del processo figlio.

Questa struttura contiene la possibilità di fornire informazioni di avvio complesse, inclusi attributi per la creazione di processi e thread.

Usare [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) con una doppia chiamata per calcolare prima di tutto il numero di byte necessari per contenere l'elenco, allocare la memoria richiesta, quindi chiamare di nuovo fornendo il puntatore a memoria opaca per impostarlo come elenco di attributi.

Chiamare quindi [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passando l'elenco degli attributi inizializzato con il flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, l'handle PSEUDOCONSOLE e le dimensioni dell'handle PSEUDOCONSOLE.

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

Chiamare quindi [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passando la struttura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) insieme al percorso del file eseguibile ed eventuali informazioni di configurazione aggiuntive, se applicabile. È importante impostare il flag di **EXTENDED_STARTUPINFO_PRESENT** quando si chiama per avvisare il sistema che il riferimento pseudoconsole è contenuto nelle informazioni estese.

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

**Si noti**

La chiusura della sessione pseudoconsole mentre il processo ospitato è ancora in fase di avvio e la connessione può causare la visualizzazione di una finestra di dialogo di errore da parte dell'applicazione client. La stessa finestra di dialogo di errore viene visualizzata se al processo ospitato viene assegnato un handle pseudoconsole non valido per l'avvio. Per il codice di inizializzazione del processo ospitato, le due circostanze sono identiche. La finestra di dialogo popup dall'applicazione client ospitata in caso di errore viene letta `0xc0000142` con un messaggio localizzato che illustra in dettaglio l'errore di inizializzazione.

## <a name="communicating-with-the-pseudoconsole-session"></a>Comunicazione con la sessione Pseudoconsole

Una volta creato il processo, l'applicazione host può usare l'estremità di scrittura della pipe di input per inviare le informazioni sull'interazione utente in pseudoconsole e la fine di lettura della pipe di output per ricevere informazioni sulla presentazione grafica dalla pseudo-console. 

Per decidere come gestire ulteriori attività, l'applicazione host è completamente attiva. L'applicazione host potrebbe avviare una finestra in un altro thread per raccogliere l'input interazione utente e serializzarlo nell'estremità di scrittura della pipe di input per pseudoconsole e l'applicazione in modalità carattere ospitata. È possibile avviare un altro thread per svuotare l'estremità di lettura della pipe di output per pseudoconsole, decodificare il testo e le informazioni sulla [sequenza di terminali virtuali](console-virtual-terminal-sequences.md) e presentarlo sullo schermo. 

I thread possono anche essere usati per inoltrare le informazioni dai canali pseudoconsole a un canale o a un dispositivo diverso, inclusa una rete per le informazioni remote a un altro processo o computer ed evitando la transcodifica locale delle informazioni.

## <a name="resizing-the-pseudoconsole"></a>Ridimensionamento di Pseudoconsole

Nel corso del runtime è possibile che si verifichi una circostanza in base alla quale è necessario modificare le dimensioni del buffer a causa di un'interazione dell'utente o di una richiesta ricevuta fuori banda da un altro dispositivo di visualizzazione/interazione.

Questa operazione può essere eseguita con la funzione [**ResizePseudoConsole**](resizepseudoconsole.md) specificando sia l'altezza che la larghezza del buffer in un conteggio di caratteri.

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

## <a name="ending-the-pseudoconsole-session"></a>Fine della sessione Pseudoconsole

Per terminare la sessione, chiamare la funzione [**ClosePseudoConsole**](closepseudoconsole.md) con l'handle della creazione di pseudoconsole originale. Qualsiasi applicazione in modalità carattere client collegata, ad esempio quella della chiamata [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , verrà terminata quando la sessione viene chiusa. Se l'elemento figlio originale era un'applicazione di tipo Shell che crea altri processi, verranno terminati anche eventuali processi associati correlati nell'albero.

**Si noti**

La chiusura della sessione presenta diversi effetti collaterali che possono determinare una condizione di deadlock se il pseudoconsole viene usato in modalità sincrona a thread singolo. L'operazione di chiusura della sessione pseudoconsole può generare un aggiornamento finale del frame a `hOutput` cui deve essere svuotato dal buffer del canale di comunicazione. Se, inoltre, `PSEUDOCONSOLE_INHERIT_CURSOR` è stato selezionato durante la creazione del pseudoconsole, il tentativo di chiudere il pseudoconsole senza rispondere al messaggio di query eredità del cursore (ricevuto `hOutput` e risposto a tramite `hInput` ) può causare un'altra condizione di deadlock. È consigliabile che i canali di comunicazione per i pseudoconsole siano serviti su singoli thread e rimangano svuotati ed elaborati fino a quando non vengono interrotti dall'applicazione client in uscita o dal completamento delle attività di teardown durante la chiamata della funzione [**ClosePseudoConsole**](closepseudoconsole.md) .
