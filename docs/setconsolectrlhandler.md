---
title: SetConsoleCtrlHandler (funzione)
description: Aggiunge o rimuove una funzione HandlerRoutine definita dall'applicazione nell'elenco di funzioni gestore per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 208eebc92b718fed9856a48dfaf5cbebdaddc1e1
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420270"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="2846c-104">SetConsoleCtrlHandler (funzione)</span><span class="sxs-lookup"><span data-stu-id="2846c-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="2846c-105">Aggiunge o rimuove una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione nell'elenco di funzioni di gestione per il processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="2846c-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="2846c-106">Se non viene specificata alcuna funzione gestore, la funzione imposta un attributo ereditabile che determina se il processo chiamante ignora i segnali <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2846c-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="2846c-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2846c-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="2846c-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="2846c-108">Parameters</span></span>

<span data-ttu-id="2846c-109">*HandlerRoutine* \[in, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="2846c-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="2846c-110">Un puntatore alla funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione da aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="2846c-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="2846c-111">Questo parametro può essere **NULL**.</span><span class="sxs-lookup"><span data-stu-id="2846c-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="2846c-112">*Add* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2846c-112">*Add* \[in\]</span></span>  
<span data-ttu-id="2846c-113">Se questo parametro è **TRUE**, il gestore viene aggiunto; se è **FALSE**, il gestore viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="2846c-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="2846c-114">Se il parametro *HandlerRoutine* è **NULL**, il valore **TRUE** fa in modo che il processo chiamante ignori l'input <kbd>CTRL</kbd>+<kbd>C</kbd> e il valore **FALSE** ripristina la normale elaborazione dell'input <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2846c-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="2846c-115">Questo attributo che determina se <kbd>CTRL</kbd>+<kbd>C</kbd> viene ignorato o elaborato viene ereditato dai processi figlio.</span><span class="sxs-lookup"><span data-stu-id="2846c-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="2846c-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2846c-116">Return value</span></span>

<span data-ttu-id="2846c-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2846c-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2846c-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2846c-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2846c-119">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2846c-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="2846c-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2846c-120">Remarks</span></span>

<span data-ttu-id="2846c-121">Questa funzione fornisce una notifica simile per l'applicazione console e i servizi che [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) fornisce per le applicazioni grafiche con un message pump.</span><span class="sxs-lookup"><span data-stu-id="2846c-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="2846c-122">È anche possibile usare questa funzione da un'applicazione grafica, ma non è garantito che arrivi prima della notifica da **WM\_QUERYENDSESSION**.</span><span class="sxs-lookup"><span data-stu-id="2846c-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="2846c-123">Ogni processo della console dispone di un elenco specifico di funzioni [**HandlerRoutine**](handlerroutine.md) definite dall'applicazione che gestiscono i segnali <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>BREAK</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2846c-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="2846c-124">Le funzioni gestore gestiscono anche i segnali generati dal sistema quando l'utente chiude la console, si disconnette o arresta il sistema.</span><span class="sxs-lookup"><span data-stu-id="2846c-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="2846c-125">Inizialmente, l'elenco dei gestori per ogni processo contiene solo una funzione gestore predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658).</span><span class="sxs-lookup"><span data-stu-id="2846c-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="2846c-126">Un processo della console aggiunge o rimuove ulteriori funzioni gestore chiamando la funzione **SetConsoleCtrlHandler**, che non influisce sull'elenco di funzioni gestore per altri processi.</span><span class="sxs-lookup"><span data-stu-id="2846c-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="2846c-127">Quando un processo della console riceve uno dei segnali di controllo, vengono chiamate le relative funzioni gestore, partendo dall'ultima registrata, finché uno dei gestori non restituisce `TRUE`.</span><span class="sxs-lookup"><span data-stu-id="2846c-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="2846c-128">Se nessuno dei gestori restituisce `TRUE`, viene chiamato il gestore predefinito.</span><span class="sxs-lookup"><span data-stu-id="2846c-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="2846c-129">Per i processi della console, le combinazioni di tasti <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>INTERR</kbd> in genere vengono considerate come segnali (**CTRL\_C\_EVENT** e **CTRL\_BREAK\_EVENT**).</span><span class="sxs-lookup"><span data-stu-id="2846c-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="2846c-130">Quando una finestra della console con lo stato attivo della tastiera riceve <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd>, il segnale viene generalmente passato a tutti i processi che condividono tale console.</span><span class="sxs-lookup"><span data-stu-id="2846c-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="2846c-131"><kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene sempre considerato come segnale, ma è possibile modificare il comportamento tipico di <kbd>CTRL</kbd>+<kbd>C</kbd> in tre modi che impediscono la chiamata delle funzioni gestore:</span><span class="sxs-lookup"><span data-stu-id="2846c-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="2846c-132">La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità **ENABLE\_PROCESSED\_INPUT** per il buffer di input di una console, in modo che <kbd>CTRL</kbd>+<kbd>C</kbd> venga segnalato come input di tastiera anziché come segnale.</span><span class="sxs-lookup"><span data-stu-id="2846c-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="2846c-133">Se si chiama **SetConsoleCtrlHandler** con gli argomenti **NULL** e **TRUE**, il processo chiamante ignora i segnali <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2846c-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="2846c-134">Questo attributo viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.</span><span class="sxs-lookup"><span data-stu-id="2846c-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="2846c-135">Se è in corso il debug di un processo della console e i segnali <kbd>CTRL</kbd>+<kbd>C</kbd> segnali non sono stati disabilitati, il sistema genera un'eccezione **DBG\_CONTROL\_C**.</span><span class="sxs-lookup"><span data-stu-id="2846c-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="2846c-136">Questa eccezione viene generata solo a vantaggio del debugger e un'applicazione non deve mai usare un gestore di eccezioni per gestirla.</span><span class="sxs-lookup"><span data-stu-id="2846c-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="2846c-137">Se l'eccezione viene gestita dal debugger, un'applicazione non noterà la combinazione <kbd>CTRL</kbd>+<kbd>C</kbd>, con un'eccezione: le attese con avvisi vengono terminate.</span><span class="sxs-lookup"><span data-stu-id="2846c-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="2846c-138">Se il debugger imposta l'eccezione su non gestita, <kbd>CTRL</kbd>+<kbd>C</kbd> viene passato al processo della console e considerato come un segnale, come indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="2846c-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="2846c-139">Un processo della console può usare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd> a un gruppo di processi della console.</span><span class="sxs-lookup"><span data-stu-id="2846c-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="2846c-140">Il sistema genera i segnali **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** e **CTRL\_SHUTDOWN\_EVENT** quando l'utente chiude la console, si disconnette o arresta il sistema, per consentire al processo di eseguire la pulizia prima della terminazione.</span><span class="sxs-lookup"><span data-stu-id="2846c-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="2846c-141">Le funzioni della console, o qualsiasi funzione di runtime C che chiama funzioni della console, potrebbero non funzionare in modo affidabile durante l'elaborazione di uno dei tre segnali citati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="2846c-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="2846c-142">Questo perché alcune o tutte le routine di pulitura della console interna potrebbero essere state chiamate prima dell'esecuzione del gestore di segnale del processo.</span><span class="sxs-lookup"><span data-stu-id="2846c-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="2846c-143">**Windows 7, Windows 8, Windows 8.1 e Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="2846c-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="2846c-144">Se un'applicazione console carica la libreria gdi32.dll o user32.dll, la funzione [**HandlerRoutine**](handlerroutine.md) specificata chiamando **SetConsoleCtrlHandler** non viene chiamata per gli eventi **CTRL\_LOGOFF\_EVENT** e **CTRL\_SHUTDOWN\_EVENT**.</span><span class="sxs-lookup"><span data-stu-id="2846c-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="2846c-145">Il sistema operativo riconosce i processi che caricano gdi32.dll o user32.dll come applicazioni Windows anziché come applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="2846c-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="2846c-146">Questo comportamento si verifica anche per le applicazioni console che non chiamano direttamente le funzioni in gdi32.dll o user32.dll, ma chiamano funzioni come le [funzioni Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) che a loro volta chiamano le funzioni in gdi32.dll o user32.dll.</span><span class="sxs-lookup"><span data-stu-id="2846c-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="2846c-147">Per ricevere eventi quando un utente si disconnette o il dispositivo si arresta in questi casi, creare una finestra nascosta nell'applicazione console e quindi gestire i messaggi [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) e [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) ricevuti dalla finestra nascosta.</span><span class="sxs-lookup"><span data-stu-id="2846c-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="2846c-148">È possibile creare una finestra nascosta chiamando il metodo [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con il parametro *dwExStyle* impostato su 0.</span><span class="sxs-lookup"><span data-stu-id="2846c-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="2846c-149">Esempi</span><span class="sxs-lookup"><span data-stu-id="2846c-149">Examples</span></span>

<span data-ttu-id="2846c-150">Un esempio è disponibile in [Registrazione di una funzione gestore di controllo](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="2846c-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="2846c-151">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2846c-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2846c-152">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2846c-152">Minimum supported client</span></span> | <span data-ttu-id="2846c-153">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="2846c-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2846c-154">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2846c-154">Minimum supported server</span></span> | <span data-ttu-id="2846c-155">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="2846c-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2846c-156">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2846c-156">Header</span></span> | <span data-ttu-id="2846c-157">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="2846c-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2846c-158">Libreria</span><span class="sxs-lookup"><span data-stu-id="2846c-158">Library</span></span> | <span data-ttu-id="2846c-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="2846c-159">Kernel32.lib</span></span> |
| <span data-ttu-id="2846c-160">DLL</span><span class="sxs-lookup"><span data-stu-id="2846c-160">DLL</span></span> | <span data-ttu-id="2846c-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2846c-161">Kernel32.dll</span></span> |
| <span data-ttu-id="2846c-162">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="2846c-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="2846c-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2846c-163">See also</span></span>

[<span data-ttu-id="2846c-164">Gestori di controllo della console</span><span class="sxs-lookup"><span data-stu-id="2846c-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="2846c-165">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="2846c-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2846c-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="2846c-166">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="2846c-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="2846c-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="2846c-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2846c-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="2846c-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="2846c-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="2846c-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2846c-170">**SetConsoleMode**</span></span>](setconsolemode.md)
