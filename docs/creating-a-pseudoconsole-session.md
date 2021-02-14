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
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="d233a-104">Creazione di una sessione di pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="d233a-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="d233a-105">Windows Pseudoconsole, talvolta denominato anche pseudoconsole, ConPTY o Windows PTY, è un meccanismo progettato per la creazione di un host esterno per le attività di sottosistema in modalità carattere che sostituiscono la parte di interattività utente della finestra predefinita dell'host della console.</span><span class="sxs-lookup"><span data-stu-id="d233a-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="d233a-106">L'hosting di una sessione di pseudoconsole è leggermente diverso rispetto a quello di una sessione di console tradizionale.</span><span class="sxs-lookup"><span data-stu-id="d233a-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="d233a-107">Mentre le sessioni di console tradizionali vengono avviate automaticamente quando il sistema operativo riconosce l'imminente esecuzione di un'applicazione in modalità carattere,</span><span class="sxs-lookup"><span data-stu-id="d233a-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="d233a-108">l'hosting di una sessione di pseudoconsole e dei rispettivi canali di comunicazione richiede che questi vengano creati dall'applicazione di hosting prima della creazione del processo con l'applicazione figlio in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="d233a-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="d233a-109">Il processo figlio verrà comunque creato tramite la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), ma con alcune informazioni aggiuntive che consentiranno al sistema operativo di mettere a punto l'ambiente appropriato.</span><span class="sxs-lookup"><span data-stu-id="d233a-109">The child process will still be created using the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="d233a-110">Altre informazioni di carattere generale su questo sistema sono disponibili nel [post di blog relativo all'annuncio iniziale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="d233a-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="d233a-111">Esempi completi di utilizzo della pseudoconsole sono disponibili nel repository GitHub [microsoft/terminal](https://github.com/microsoft/terminal) disponibile nella directory degli esempi.</span><span class="sxs-lookup"><span data-stu-id="d233a-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="d233a-112">Preparazione dei canali di comunicazione</span><span class="sxs-lookup"><span data-stu-id="d233a-112">Preparing the communication channels</span></span>

<span data-ttu-id="d233a-113">Il primo passaggio prevede la creazione di una coppia di canali di comunicazione sincrona che verranno messi a disposizione durante la creazione della sessione di pseudoconsole per la comunicazione bidirezionale con l'applicazione ospitata.</span><span class="sxs-lookup"><span data-stu-id="d233a-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="d233a-114">Questi canali vengono elaborati dal sistema di pseudoconsole tramite [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) con [I/O sincrono](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="d233a-114">These channels are processed by the pseudoconsole system using [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="d233a-115">Sono accettati anche handle di file o dispositivi di I/O, ad esempio un flusso di file o una pipe, a condizione che non sia necessaria una struttura [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) per la comunicazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="d233a-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="d233a-116">Per evitare race condition e deadlock, inoltre, è consigliabile che ogni canale di comunicazione venga gestito in un thread separato in grado di mantenere lo stato del buffer client e la coda di messaggistica all'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d233a-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="d233a-117">Se si gestissero tutte le attività della pseudoconsole sullo stesso thread, infatti, potrebbe verificarsi un deadlock in cui uno dei buffer di comunicazione si riempie e resta in attesa di un'azione dell'utente mentre tenta di inviare una richiesta di blocco su un altro canale.</span><span class="sxs-lookup"><span data-stu-id="d233a-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="d233a-118">Creazione di una pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="d233a-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="d233a-119">Con i canali di comunicazione correttamente creati, identificare ora l'estremità "read" del canale di input e l'estremità "write" del canale di output.</span><span class="sxs-lookup"><span data-stu-id="d233a-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="d233a-120">Questa coppia di handle viene fornita quando si chiama [**CreatePseudoConsole**](createpseudoconsole.md) per creare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="d233a-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="d233a-121">Al momento della creazione, è necessario specificare le dimensioni delle assi X e Y (in numero di caratteri).</span><span class="sxs-lookup"><span data-stu-id="d233a-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="d233a-122">Si tratta delle dimensioni che verranno applicate alla superficie di visualizzazione nella finestra di presentazione finale (terminale).</span><span class="sxs-lookup"><span data-stu-id="d233a-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="d233a-123">Quesiti valori vengono usati anche per creare un buffer di memoria all'interno del sistema di pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="d233a-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="d233a-124">Le dimensioni del buffer forniscono risposte alle applicazioni in modalità carattere client che cercano informazioni attraverso le [funzioni della console lato client](console-functions.md) come [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) e stabiliscono il layout e il posizionamento del testo nei casi in cui i client si avvalgano di funzioni come [**WriteConsoleOutput**](writeconsoleoutput.md).</span><span class="sxs-lookup"><span data-stu-id="d233a-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="d233a-125">Durante la creazione di un pseudoconsole, infine, viene fornito un campo Flags per l'esecuzione di funzionalità speciali.</span><span class="sxs-lookup"><span data-stu-id="d233a-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="d233a-126">Per impostazione predefinita, questo campo è impostato su 0 per indicare che non sono disponibili funzionalità speciali.</span><span class="sxs-lookup"><span data-stu-id="d233a-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="d233a-127">A questo punto, è disponibile un solo flag speciale per richiedere l'ereditarietà della posizione del cursore da una sessione della console già collegata al chiamante dell'API della pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="d233a-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="d233a-128">L'utilizzo di questo flag è destinato tuttavia a scenari più avanzati in cui un'applicazione host che prepara una sessione di pseudoconsole è anche un'applicazione in modalità carattere client di un altro ambiente console.</span><span class="sxs-lookup"><span data-stu-id="d233a-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="d233a-129">Di seguito è riportato un frammento di codice di esempio in cui viene usato il comando [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) per mettere a punto una coppia di canali di comunicazione e creare la pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="d233a-129">A sample snippet is provided below utilizing [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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
><span data-ttu-id="d233a-130">Questo frammento di codice è incompleto e viene usato esclusivamente a titolo dimostrativo di questa chiamata specifica.</span><span class="sxs-lookup"><span data-stu-id="d233a-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="d233a-131">Sarà necessario gestire il ciclo di vita degli oggetti **HANDLE** in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="d233a-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="d233a-132">In caso contrario, è possibile che si verifichino scenari di deadlock, soprattutto con chiamate di I/O sincrone.</span><span class="sxs-lookup"><span data-stu-id="d233a-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="d233a-133">Al termine della chiamata [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con cui si crea l'applicazione in modalità carattere client collegata alla pseudoconsole, gli handle specificati durante la creazione devono essere liberati dal processo.</span><span class="sxs-lookup"><span data-stu-id="d233a-133">Upon completion of the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="d233a-134">In questo modo si riduce il conteggio dei riferimenti nell'oggetto dispositivo sottostante e si consente alle operazioni di I/O di rilevare correttamente un canale interrotto nel momento in cui la sessione pseudoconsole chiude la copia degli handle.</span><span class="sxs-lookup"><span data-stu-id="d233a-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="d233a-135">Preparazione per la creazione del processo figlio</span><span class="sxs-lookup"><span data-stu-id="d233a-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="d233a-136">La fase successiva prevede la preparazione della struttura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) che consente la comunicazione di informazioni sulla pseudoconsole durante l'avvio del processo figlio.</span><span class="sxs-lookup"><span data-stu-id="d233a-136">The next phase is to prepare the [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="d233a-137">Questa struttura offre infatti la possibilità di fornire informazioni di avvio complesse, inclusi attributi per la creazione di processi e thread.</span><span class="sxs-lookup"><span data-stu-id="d233a-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="d233a-138">Usare [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in modalità doppia chiamata per calcolare il numero di byte necessari per contenere l'elenco, allocare la memoria necessaria e quindi chiamare di nuovo specificando il puntatore di memoria opaco per impostarlo come elenco di attributi.</span><span class="sxs-lookup"><span data-stu-id="d233a-138">Use [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="d233a-139">Chiamare quindi [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passando l'elenco degli attributi inizializzato con il flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, l'handle della pseudoconsole e le relative dimensioni.</span><span class="sxs-lookup"><span data-stu-id="d233a-139">Next, call [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="d233a-140">Creazione del processo ospitato</span><span class="sxs-lookup"><span data-stu-id="d233a-140">Creating the Hosted Process</span></span>

<span data-ttu-id="d233a-141">A questo punto, chiamare [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) passando la struttura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) contestualmente al percorso del file eseguibile e a eventuali informazioni di configurazione aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="d233a-141">Next, call [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) passing the [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="d233a-142">È importante impostare il flag **EXTENDED_STARTUPINFO_PRESENT** quando si chiama per informare il sistema che il riferimento alla pseudoconsole è contenuto nelle informazioni estese.</span><span class="sxs-lookup"><span data-stu-id="d233a-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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
> <span data-ttu-id="d233a-143">Se si chiude la sessione della pseudoconsole mentre il processo ospitato è ancora in fase di avvio e connessione, è possibile che nell'applicazione client venga visualizzata una finestra di dialogo di errore.</span><span class="sxs-lookup"><span data-stu-id="d233a-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="d233a-144">La stessa finestra di errore viene visualizzata se al processo ospitato viene fornito un handle della pseudoconsole non valido per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="d233a-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="d233a-145">Per il codice di inizializzazione del processo ospitato, le due circostanze sono identiche.</span><span class="sxs-lookup"><span data-stu-id="d233a-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="d233a-146">Nella finestra di dialogo popup visualizzata nell'applicazione client ospitata verrà visualizzato il codice di errore `0xc0000142` con un messaggio localizzato in cui sono riportate informazioni sui motivi dell'errore di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="d233a-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="d233a-147">Comunicazione con la sessione della pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="d233a-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="d233a-148">Una volta completata la creazione del processo, l'applicazione host può usare l'estremità write della pipe di input per inviare informazioni di interazione utente alla pseudoconsole e l'estremità end della pipe di output per ricevere da questa informazioni di presentazione grafica.</span><span class="sxs-lookup"><span data-stu-id="d233a-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="d233a-149">È l'applicazione host a decidere come dovranno essere gestite le attività successive.</span><span class="sxs-lookup"><span data-stu-id="d233a-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="d233a-150">L'applicazione host, ad esempio, può avviare una finestra in un altro thread per raccogliere l'input di interazione utente e serializzarlo nell'estremità write della pipe di input sia per la pseudoconsole che per l'applicazione in modalità carattere ospitata.</span><span class="sxs-lookup"><span data-stu-id="d233a-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="d233a-151">Oppure, può avviare un altro thread per svuotare l'estremità read della pipe di output per la pseudoconsole, decodificare il testo e le informazioni sulla [sequenza di terminale virtuale](console-virtual-terminal-sequences.md) e presentarle sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="d233a-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="d233a-152">I thread possono essere usati anche per inoltrare informazioni dai canali della pseudoconsole a un canale o un dispositivo diverso, inclusa una rete, in modo da inviare informazioni in remoto un altro processo o computer ed evitare così la transcodifica locale delle informazioni.</span><span class="sxs-lookup"><span data-stu-id="d233a-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="d233a-153">Ridimensionamento della pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="d233a-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="d233a-154">Nel corso del runtime è possibile che si creino le circostanze per le quali risulta necessario modificare le dimensioni del buffer a causa di un'interazione utente o una richiesta ricevuta fuori banda da un altro dispositivo di visualizzazione/interazione.</span><span class="sxs-lookup"><span data-stu-id="d233a-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="d233a-155">Questa operazione può essere eseguita mediante la funzione [**ResizePseudoConsole**](resizepseudoconsole.md) specificando l'altezza e la larghezza del buffer in numero di caratteri.</span><span class="sxs-lookup"><span data-stu-id="d233a-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="d233a-156">Conclusione della sessione della pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="d233a-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="d233a-157">Per terminare la sessione, chiamare la funzione [**ClosePseudoConsole**](closepseudoconsole.md) con l'handle usato per la creazione della pseudoconsole originale.</span><span class="sxs-lookup"><span data-stu-id="d233a-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="d233a-158">Eventuali applicazioni in modalità carattere client collegate, ad esempio quelle create con il comando [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), verranno terminate nel momento in cui viene chiusa la sessione.</span><span class="sxs-lookup"><span data-stu-id="d233a-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="d233a-159">Se l'elemento figlio originale era un'applicazione di tipo Shell da cui vengono creati altri processi, verranno terminati anche tutti gli eventuali processi collegati presenti nell'albero.</span><span class="sxs-lookup"><span data-stu-id="d233a-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="d233a-160">La chiusura della sessione presenta diversi effetti collaterali che possono determinare una condizione di deadlock se la pseudoconsole viene usata in modalità sincrona a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="d233a-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="d233a-161">L'operazione di chiusura della sessione di pseudoconsole può generare un aggiornamento finale dei frame per `hOutput`, che deve essere rimosso dal buffer del canale di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="d233a-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="d233a-162">Se, inoltre, è stato selezionato `PSEUDOCONSOLE_INHERIT_CURSOR` durante la creazione della pseudoconsole, il tentativo di chiudere la pseudoconsole senza rispondere al messaggio di query sull'ereditarietà del cursore (ricevuto su `hOutput` e a cui è stata inviata una risposta tramite `hInput`) può generare un'altra condizione di deadlock.</span><span class="sxs-lookup"><span data-stu-id="d233a-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="d233a-163">È questo il motivo per cui è consigliabile che i canali di comunicazione della pseudoconsole vengano gestiti su singoli thread e rimangano svuotati ed elaborati fino a quando non vengono interrotti dall'applicazione client in uscita o dal completamento delle attività di disinstallazione durante la chiamata della funzione [**ClosePseudoConsole**](closepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="d233a-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>