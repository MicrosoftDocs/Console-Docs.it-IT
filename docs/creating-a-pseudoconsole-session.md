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
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="734b3-104">Creazione di una sessione Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="734b3-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="734b3-105">Windows Pseudoconsole, talvolta noto anche come pseudo-console, ConPTY o Windows PTY, è un meccanismo progettato per la creazione di un host esterno per le attività del sottosistema in modalità carattere che sostituiscono la parte dell'interattività utente della finestra host della console predefinita.</span><span class="sxs-lookup"><span data-stu-id="734b3-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="734b3-106">L'hosting di una sessione pseudoconsole è leggermente diverso rispetto a una sessione console tradizionale.</span><span class="sxs-lookup"><span data-stu-id="734b3-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="734b3-107">Le sessioni console tradizionali vengono avviate automaticamente quando il sistema operativo riconosce l'esecuzione di un'applicazione in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="734b3-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="734b3-108">Al contrario, una sessione pseudoconsole e i canali di comunicazione devono essere creati dall'applicazione host prima di creare il processo con l'applicazione in modalità carattere figlio da ospitare.</span><span class="sxs-lookup"><span data-stu-id="734b3-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="734b3-109">Il processo figlio verrà comunque creato utilizzando la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , ma con alcune informazioni aggiuntive che configureranno il sistema operativo per stabilire l'ambiente appropriato.</span><span class="sxs-lookup"><span data-stu-id="734b3-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="734b3-110">Per ulteriori informazioni complementari sul sistema, vedere il post di [Blog relativo all'annuncio iniziale](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="734b3-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="734b3-111">Esempi completi di uso di Pseudoconsole sono disponibili nel repository GitHub [Microsoft/console](https://github.com/Microsoft/console) nella directory degli esempi.</span><span class="sxs-lookup"><span data-stu-id="734b3-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [Microsoft/console](https://github.com/Microsoft/console) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="734b3-112">Preparazione dei canali di comunicazione</span><span class="sxs-lookup"><span data-stu-id="734b3-112">Preparing the communication channels</span></span>

<span data-ttu-id="734b3-113">Il primo passaggio consiste nel creare una coppia di canali di comunicazione sincrona che verranno forniti durante la creazione della sessione pseudoconsole per la comunicazione bidirezionale con l'applicazione ospitata.</span><span class="sxs-lookup"><span data-stu-id="734b3-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="734b3-114">Questi canali vengono elaborati dal sistema pseudoconsole usando [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) con [i/O sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="734b3-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="734b3-115">Gli handle di un file o di un dispositivo di I/O come un flusso di file o una pipe sono accettabili purché non sia necessaria una struttura [**sovrapposta**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) per la comunicazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="734b3-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

<span data-ttu-id="734b3-116">**Si noti**</span><span class="sxs-lookup"><span data-stu-id="734b3-116">**NOTE:**</span></span>

<span data-ttu-id="734b3-117">Per evitare race condition e deadlock, è consigliabile che ogni canale di comunicazione venga servito in un thread separato che gestisce lo stato del buffer client e la coda di messaggistica all'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="734b3-117">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="734b3-118">La manutenzione di tutte le attività pseudoconsole sullo stesso thread può comportare un deadlock in cui uno dei buffer di comunicazione viene riempito e in attesa dell'azione quando si tenta di inviare una richiesta di blocco su un altro canale.</span><span class="sxs-lookup"><span data-stu-id="734b3-118">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="734b3-119">Creazione di Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="734b3-119">Creating the Pseudoconsole</span></span>

<span data-ttu-id="734b3-120">Con i canali di comunicazione che sono stati stabiliti, identificare la fine "lettura" del canale di input e l'estremità "Write" del canale di output.</span><span class="sxs-lookup"><span data-stu-id="734b3-120">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="734b3-121">Questa coppia di handle viene fornita nella chiamata a [**CreatePseudoConsole**](createpseudoconsole.md) per creare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="734b3-121">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="734b3-122">Quando si crea, viene fornita anche una dimensione che rappresenta le dimensioni X e Y (in Count of characters).</span><span class="sxs-lookup"><span data-stu-id="734b3-122">When creating, a size representing the X and Y dimensions (in count of characters) is also provided.</span></span> <span data-ttu-id="734b3-123">Si tratta delle dimensioni che verranno applicate alla superficie di visualizzazione per la finestra di presentazione finale (terminale).</span><span class="sxs-lookup"><span data-stu-id="734b3-123">This is the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="734b3-124">I valori vengono usati per creare un buffer in memoria all'interno del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="734b3-124">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span> 

<span data-ttu-id="734b3-125">Le dimensioni del buffer forniscono risposte alle applicazioni in modalità carattere client che verificano le informazioni usando le [funzioni console lato client](console-functions.md) come [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) e stabiliscono il layout e il posizionamento del testo quando i client usano funzioni come [**WriteConsoleOutput**](writeconsoleoutput.md).</span><span class="sxs-lookup"><span data-stu-id="734b3-125">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="734b3-126">Infine, viene fornito un campo Flags durante la creazione di un pseudoconsole per eseguire funzionalità speciali.</span><span class="sxs-lookup"><span data-stu-id="734b3-126">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="734b3-127">Per impostazione predefinita, impostare questa opzione su 0 per non avere funzionalità speciali.</span><span class="sxs-lookup"><span data-stu-id="734b3-127">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="734b3-128">A questo punto, è disponibile un solo flag speciale per richiedere il eredità della posizione del cursore da una sessione della console già associata al chiamante dell'API pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="734b3-128">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="734b3-129">Questa operazione è destinata all'uso in scenari più avanzati in cui un'applicazione host che prepara una sessione pseudoconsole è anche un'applicazione in modalità carattere client di un altro ambiente console.</span><span class="sxs-lookup"><span data-stu-id="734b3-129">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span> 

<span data-ttu-id="734b3-130">Di seguito è riportato un frammento di codice di esempio che usa [**non**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) per stabilire una coppia di canali di comunicazione e creare il pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="734b3-130">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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


<span data-ttu-id="734b3-131">**NOTA**:</span><span class="sxs-lookup"><span data-stu-id="734b3-131">**NOTE**:</span></span> 

<span data-ttu-id="734b3-132">Questo frammento di codice è incompleto e viene utilizzato solo per la dimostrazione di questa specifica chiamata.</span><span class="sxs-lookup"><span data-stu-id="734b3-132">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="734b3-133">Sarà necessario gestire la durata dell' **handle**in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="734b3-133">You will need to manage the lifetime of the **HANDLE**s appropriately.</span></span> <span data-ttu-id="734b3-134">La mancata gestione corretta della durata degli **handle**può causare scenari di deadlock, soprattutto con le chiamate di I/O sincrone.</span><span class="sxs-lookup"><span data-stu-id="734b3-134">Failure to manage the lifetime of **HANDLE**s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="734b3-135">Al termine della chiamata a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) per creare l'applicazione in modalità carattere client collegata a pseudoconsole, gli handle specificati durante la creazione devono essere liberati da questo processo.</span><span class="sxs-lookup"><span data-stu-id="734b3-135">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="734b3-136">In questo modo si riduce il conteggio dei riferimenti nell'oggetto dispositivo sottostante e si consentono alle operazioni di I/O di rilevare correttamente un canale interrotto quando la sessione pseudoconsole chiude la copia degli handle.</span><span class="sxs-lookup"><span data-stu-id="734b3-136">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="734b3-137">Preparazione per la creazione del processo figlio</span><span class="sxs-lookup"><span data-stu-id="734b3-137">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="734b3-138">La fase successiva consiste nel preparare la struttura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) che comunicherà le informazioni di pseudoconsole durante l'avvio del processo figlio.</span><span class="sxs-lookup"><span data-stu-id="734b3-138">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="734b3-139">Questa struttura contiene la possibilità di fornire informazioni di avvio complesse, inclusi attributi per la creazione di processi e thread.</span><span class="sxs-lookup"><span data-stu-id="734b3-139">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="734b3-140">Usare [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) con una doppia chiamata per calcolare prima di tutto il numero di byte necessari per contenere l'elenco, allocare la memoria richiesta, quindi chiamare di nuovo fornendo il puntatore a memoria opaca per impostarlo come elenco di attributi.</span><span class="sxs-lookup"><span data-stu-id="734b3-140">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="734b3-141">Chiamare quindi [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passando l'elenco degli attributi inizializzato con il flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, l'handle PSEUDOCONSOLE e le dimensioni dell'handle PSEUDOCONSOLE.</span><span class="sxs-lookup"><span data-stu-id="734b3-141">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="734b3-142">Creazione del processo ospitato</span><span class="sxs-lookup"><span data-stu-id="734b3-142">Creating the Hosted Process</span></span>

<span data-ttu-id="734b3-143">Chiamare quindi [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passando la struttura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) insieme al percorso del file eseguibile ed eventuali informazioni di configurazione aggiuntive, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="734b3-143">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="734b3-144">È importante impostare il flag di **EXTENDED_STARTUPINFO_PRESENT** quando si chiama per avvisare il sistema che il riferimento pseudoconsole è contenuto nelle informazioni estese.</span><span class="sxs-lookup"><span data-stu-id="734b3-144">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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

<span data-ttu-id="734b3-145">**Si noti**</span><span class="sxs-lookup"><span data-stu-id="734b3-145">**NOTE:**</span></span>

<span data-ttu-id="734b3-146">La chiusura della sessione pseudoconsole mentre il processo ospitato è ancora in fase di avvio e la connessione può causare la visualizzazione di una finestra di dialogo di errore da parte dell'applicazione client.</span><span class="sxs-lookup"><span data-stu-id="734b3-146">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="734b3-147">La stessa finestra di dialogo di errore viene visualizzata se al processo ospitato viene assegnato un handle pseudoconsole non valido per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="734b3-147">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="734b3-148">Per il codice di inizializzazione del processo ospitato, le due circostanze sono identiche.</span><span class="sxs-lookup"><span data-stu-id="734b3-148">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="734b3-149">La finestra di dialogo popup dall'applicazione client ospitata in caso di errore viene letta `0xc0000142` con un messaggio localizzato che illustra in dettaglio l'errore di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="734b3-149">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="734b3-150">Comunicazione con la sessione Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="734b3-150">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="734b3-151">Una volta creato il processo, l'applicazione host può usare l'estremità di scrittura della pipe di input per inviare le informazioni sull'interazione utente in pseudoconsole e la fine di lettura della pipe di output per ricevere informazioni sulla presentazione grafica dalla pseudo-console.</span><span class="sxs-lookup"><span data-stu-id="734b3-151">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span> 

<span data-ttu-id="734b3-152">Per decidere come gestire ulteriori attività, l'applicazione host è completamente attiva.</span><span class="sxs-lookup"><span data-stu-id="734b3-152">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="734b3-153">L'applicazione host potrebbe avviare una finestra in un altro thread per raccogliere l'input interazione utente e serializzarlo nell'estremità di scrittura della pipe di input per pseudoconsole e l'applicazione in modalità carattere ospitata.</span><span class="sxs-lookup"><span data-stu-id="734b3-153">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="734b3-154">È possibile avviare un altro thread per svuotare l'estremità di lettura della pipe di output per pseudoconsole, decodificare il testo e le informazioni sulla [sequenza di terminali virtuali](console-virtual-terminal-sequences.md) e presentarlo sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="734b3-154">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span> 

<span data-ttu-id="734b3-155">I thread possono anche essere usati per inoltrare le informazioni dai canali pseudoconsole a un canale o a un dispositivo diverso, inclusa una rete per le informazioni remote a un altro processo o computer ed evitando la transcodifica locale delle informazioni.</span><span class="sxs-lookup"><span data-stu-id="734b3-155">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="734b3-156">Ridimensionamento di Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="734b3-156">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="734b3-157">Nel corso del runtime è possibile che si verifichi una circostanza in base alla quale è necessario modificare le dimensioni del buffer a causa di un'interazione dell'utente o di una richiesta ricevuta fuori banda da un altro dispositivo di visualizzazione/interazione.</span><span class="sxs-lookup"><span data-stu-id="734b3-157">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="734b3-158">Questa operazione può essere eseguita con la funzione [**ResizePseudoConsole**](resizepseudoconsole.md) specificando sia l'altezza che la larghezza del buffer in un conteggio di caratteri.</span><span class="sxs-lookup"><span data-stu-id="734b3-158">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="734b3-159">Fine della sessione Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="734b3-159">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="734b3-160">Per terminare la sessione, chiamare la funzione [**ClosePseudoConsole**](closepseudoconsole.md) con l'handle della creazione di pseudoconsole originale.</span><span class="sxs-lookup"><span data-stu-id="734b3-160">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="734b3-161">Qualsiasi applicazione in modalità carattere client collegata, ad esempio quella della chiamata [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , verrà terminata quando la sessione viene chiusa.</span><span class="sxs-lookup"><span data-stu-id="734b3-161">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="734b3-162">Se l'elemento figlio originale era un'applicazione di tipo Shell che crea altri processi, verranno terminati anche eventuali processi associati correlati nell'albero.</span><span class="sxs-lookup"><span data-stu-id="734b3-162">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

<span data-ttu-id="734b3-163">**Si noti**</span><span class="sxs-lookup"><span data-stu-id="734b3-163">**NOTE:**</span></span>

<span data-ttu-id="734b3-164">La chiusura della sessione presenta diversi effetti collaterali che possono determinare una condizione di deadlock se il pseudoconsole viene usato in modalità sincrona a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="734b3-164">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="734b3-165">L'operazione di chiusura della sessione pseudoconsole può generare un aggiornamento finale del frame a `hOutput` cui deve essere svuotato dal buffer del canale di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="734b3-165">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="734b3-166">Se, inoltre, `PSEUDOCONSOLE_INHERIT_CURSOR` è stato selezionato durante la creazione del pseudoconsole, il tentativo di chiudere il pseudoconsole senza rispondere al messaggio di query eredità del cursore (ricevuto `hOutput` e risposto a tramite `hInput` ) può causare un'altra condizione di deadlock.</span><span class="sxs-lookup"><span data-stu-id="734b3-166">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="734b3-167">È consigliabile che i canali di comunicazione per i pseudoconsole siano serviti su singoli thread e rimangano svuotati ed elaborati fino a quando non vengono interrotti dall'applicazione client in uscita o dal completamento delle attività di teardown durante la chiamata della funzione [**ClosePseudoConsole**](closepseudoconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="734b3-167">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>
