---
title: SetConsoleCtrlHandler (funzione)
description: Aggiunge o rimuove una funzione HandlerRoutine definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060292"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="6d247-104">SetConsoleCtrlHandler (funzione)</span><span class="sxs-lookup"><span data-stu-id="6d247-104">SetConsoleCtrlHandler function</span></span>


<span data-ttu-id="6d247-105">Aggiunge o rimuove una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="6d247-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="6d247-106">Se non viene specificata alcuna funzione del gestore, la funzione imposta un attributo ereditabile che determina se il processo chiamante ignora i segnali CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="6d247-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores CTRL+C signals.</span></span>

<a name="syntax"></a><span data-ttu-id="6d247-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6d247-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a><span data-ttu-id="6d247-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="6d247-108">Parameters</span></span>
----------

<span data-ttu-id="6d247-109">*HandlerRoutine* \[ in, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="6d247-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="6d247-110">Puntatore alla funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione da aggiungere o rimuovere.</span><span class="sxs-lookup"><span data-stu-id="6d247-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="6d247-111">Questo parametro può essere **null**.</span><span class="sxs-lookup"><span data-stu-id="6d247-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="6d247-112">*Aggiungi* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6d247-112">*Add* \[in\]</span></span>  
<span data-ttu-id="6d247-113">Se questo parametro è **true**, viene aggiunto il gestore; Se è **false**, il gestore viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="6d247-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="6d247-114">Se il parametro *HandlerRoutine* è **null**, un valore **true** fa in modo che il processo chiamante ignori l'input di CTRL + c e un valore **false** ripristini l'elaborazione normale dell'input di CTRL + c.</span><span class="sxs-lookup"><span data-stu-id="6d247-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore CTRL+C input, and a **FALSE** value restores normal processing of CTRL+C input.</span></span> <span data-ttu-id="6d247-115">Questo attributo di ignorare o elaborare CTRL + C viene ereditato dai processi figlio.</span><span class="sxs-lookup"><span data-stu-id="6d247-115">This attribute of ignoring or processing CTRL+C is inherited by child processes.</span></span>

<a name="return-value"></a><span data-ttu-id="6d247-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6d247-116">Return value</span></span>
------------

<span data-ttu-id="6d247-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="6d247-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6d247-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="6d247-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6d247-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6d247-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="6d247-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6d247-120">Remarks</span></span>
-------

<span data-ttu-id="6d247-121">Questa funzione fornisce una notifica simile per l'applicazione console e i servizi forniti da [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) per le applicazioni grafiche con un message pump.</span><span class="sxs-lookup"><span data-stu-id="6d247-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="6d247-122">È anche possibile usare questa funzione da un'applicazione grafica, ma non vi è alcuna garanzia che arrivi prima della notifica da **WM \_ QUERYENDSESSION**.</span><span class="sxs-lookup"><span data-stu-id="6d247-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="6d247-123">Ogni processo della console dispone di un proprio elenco di funzioni [**HandlerRoutine**](handlerroutine.md) definite dall'applicazione che gestiscono i segnali CTRL + C e CTRL + INTERR.</span><span class="sxs-lookup"><span data-stu-id="6d247-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle CTRL+C and CTRL+BREAK signals.</span></span> <span data-ttu-id="6d247-124">Le funzioni del gestore gestiscono inoltre i segnali generati dal sistema quando l'utente chiude la console, si disconnette o arresta il sistema.</span><span class="sxs-lookup"><span data-stu-id="6d247-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="6d247-125">Inizialmente, l'elenco dei gestori per ogni processo contiene solo una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="6d247-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="6d247-126">Un processo console consente di aggiungere o rimuovere funzioni aggiuntive del gestore chiamando la funzione **SetConsoleCtrlHandler** , che non influisce sull'elenco di funzioni del gestore per altri processi.</span><span class="sxs-lookup"><span data-stu-id="6d247-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="6d247-127">Quando un processo della console riceve uno dei segnali di controllo, le relative funzioni di gestione vengono chiamate in base a un'ultima chiamata registrata prima che uno dei gestori restituisca TRUE.</span><span class="sxs-lookup"><span data-stu-id="6d247-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns TRUE.</span></span> <span data-ttu-id="6d247-128">Se nessuno dei gestori restituisce TRUE, viene chiamato il gestore predefinito.</span><span class="sxs-lookup"><span data-stu-id="6d247-128">If none of the handlers returns TRUE, the default handler is called.</span></span>

<span data-ttu-id="6d247-129">Per i processi della console, le combinazioni di tasti CTRL + C e CTRL + INTERr vengono in genere considerate come segnali (evento**CTRL \_ C \_ \*\* e \*\* \_ \_ evento di rottura CTRL**).</span><span class="sxs-lookup"><span data-stu-id="6d247-129">For console processes, the CTRL+C and CTRL+BREAK key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="6d247-130">Quando una finestra della console con lo stato attivo riceve la combinazione di tasti CTRL + C o CTRL + INTERr, il segnale viene in genere passato a tutti i processi che condividono tale console.</span><span class="sxs-lookup"><span data-stu-id="6d247-130">When a console window with the keyboard focus receives CTRL+C or CTRL+BREAK, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="6d247-131">CTRL + INTERr viene sempre considerato come un segnale, ma è possibile modificare il comportamento tipico di CTRL + C in tre modi che impediscono la chiamata delle funzioni del gestore:</span><span class="sxs-lookup"><span data-stu-id="6d247-131">CTRL+BREAK is always treated as a signal, but typical CTRL+C behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="6d247-132">La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la **modalità \_ Abilita \_ input elaborato** per il buffer di input di una console, quindi CTRL + C viene segnalato come input da tastiera anziché come segnale.</span><span class="sxs-lookup"><span data-stu-id="6d247-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="6d247-133">La chiamata di **SetConsoleCtrlHandler** con gli argomenti **null** e **true** fa sì che il processo chiamante ignori i segnali CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="6d247-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="6d247-134">Questo attributo viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.</span><span class="sxs-lookup"><span data-stu-id="6d247-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="6d247-135">Se è in corso il debug di un processo console e i segnali CTRL + C non sono stati disabilitati, il sistema genera un'eccezione di \*\* \_ controllo dbg \_ C\*\* .</span><span class="sxs-lookup"><span data-stu-id="6d247-135">If a console process is being debugged and CTRL+C signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="6d247-136">Questa eccezione viene generata solo per il vantaggio del debugger e un'applicazione non deve mai usare un gestore di eccezioni per gestirla.</span><span class="sxs-lookup"><span data-stu-id="6d247-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="6d247-137">Se l'eccezione viene gestita dal debugger, un'applicazione non noterà la combinazione di tasti CTRL + C, con una sola eccezione: le attese avvisi vengono terminate.</span><span class="sxs-lookup"><span data-stu-id="6d247-137">If the debugger handles the exception, an application will not notice the CTRL+C, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="6d247-138">Se il debugger passa l'eccezione su non gestito, CTRL + C viene passato al processo della console e considerato come un segnale, come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="6d247-138">If the debugger passes the exception on unhandled, CTRL+C is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="6d247-139">Un processo console può usare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale CTRL + C o Ctrl + Break a un gruppo di processi della console.</span><span class="sxs-lookup"><span data-stu-id="6d247-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to a console process group.</span></span>

<span data-ttu-id="6d247-140">Il sistema genera l'evento di \*\* \_ chiusura \_ CTRL**, l' \*\* \_ \_ evento di disconnessione**CTRL e i segnali \*\* \_ \_ evento di chiusura CTRL\*\* quando l'utente chiude la console, si disconnette o arresta il sistema in modo che il processo abbia la possibilità di eseguire la pulizia prima della terminazione.</span><span class="sxs-lookup"><span data-stu-id="6d247-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="6d247-141">Le funzioni console, o qualsiasi funzione di runtime del linguaggio C che chiama funzioni console, potrebbero non funzionare in modo affidabile durante l'elaborazione di uno dei tre segnali citati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="6d247-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="6d247-142">Il motivo è che è possibile che alcune o tutte le routine di pulitura della console interna siano state chiamate prima di eseguire il gestore del segnale di processo.</span><span class="sxs-lookup"><span data-stu-id="6d247-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="6d247-143">**Windows 7, Windows 8, Windows 8.1 e Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="6d247-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="6d247-144">Se un'applicazione console carica la libreria gdi32.dll o user32.dll, la funzione [**HandlerRoutine**](handlerroutine.md) specificata quando si chiama **SetConsoleCtrlHandler** non viene chiamata per l' \*\* \_ \_ evento di disconnessione CTRL\*\* e per gli eventi di \*\* \_ arresto \_ di CTRL\*\* .</span><span class="sxs-lookup"><span data-stu-id="6d247-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="6d247-145">Il sistema operativo riconosce i processi che caricano gdi32.dll o user32.dll come applicazioni Windows anziché come applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="6d247-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="6d247-146">Questo comportamento si verifica anche per le applicazioni console che non chiamano funzioni direttamente in gdi32.dll o user32.dll, ma chiamano funzioni quali le funzioni [Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) che eseguono chiamate a loro volta in gdi32.dll o user32.dll.</span><span class="sxs-lookup"><span data-stu-id="6d247-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="6d247-147">Per ricevere eventi quando un utente si disconnette o il dispositivo si arresta in questi casi, creare una finestra nascosta nell'applicazione console e quindi gestire i messaggi della finestra [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) e [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) che la finestra nascosta riceve.</span><span class="sxs-lookup"><span data-stu-id="6d247-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="6d247-148">È possibile creare una finestra nascosta chiamando il metodo [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con il parametro *dwExStyle* impostato su 0.</span><span class="sxs-lookup"><span data-stu-id="6d247-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

<a name="examples"></a><span data-ttu-id="6d247-149">Esempi</span><span class="sxs-lookup"><span data-stu-id="6d247-149">Examples</span></span>
--------

<span data-ttu-id="6d247-150">Per un esempio, vedere [registrazione di una funzione di gestione del controllo](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="6d247-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

<a name="requirements"></a><span data-ttu-id="6d247-151">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6d247-151">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6d247-152">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6d247-152">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6d247-153">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6d247-153">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6d247-154">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6d247-154">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6d247-155">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6d247-155">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6d247-156">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6d247-156">Header</span></span></p></td>
<td><span data-ttu-id="6d247-157">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6d247-157">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6d247-158">Libreria</span><span class="sxs-lookup"><span data-stu-id="6d247-158">Library</span></span></p></td>
<td><span data-ttu-id="6d247-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6d247-159">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6d247-160">DLL</span><span class="sxs-lookup"><span data-stu-id="6d247-160">DLL</span></span></p></td>
<td><span data-ttu-id="6d247-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6d247-161">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6d247-162"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6d247-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6d247-163">Gestori di controlli console</span><span class="sxs-lookup"><span data-stu-id="6d247-163">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="6d247-164">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="6d247-164">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6d247-165">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="6d247-165">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="6d247-166">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="6d247-166">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="6d247-167">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6d247-167">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="6d247-168">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="6d247-168">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="6d247-169">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6d247-169">**SetConsoleMode**</span></span>](setconsolemode.md)

 

 




