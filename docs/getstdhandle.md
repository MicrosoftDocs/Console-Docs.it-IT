---
title: GetStdHandle (funzione)
description: Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420210"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="c0b9e-104">GetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="c0b9e-104">GetStdHandle function</span></span>

<span data-ttu-id="c0b9e-105">Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="c0b9e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c0b9e-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="c0b9e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c0b9e-107">Parameters</span></span>

<span data-ttu-id="c0b9e-108">*nStdHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c0b9e-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="c0b9e-109">Il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-109">The standard device.</span></span> <span data-ttu-id="c0b9e-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="c0b9e-111">Valore</span><span class="sxs-lookup"><span data-stu-id="c0b9e-111">Value</span></span> | <span data-ttu-id="c0b9e-112">Significato</span><span class="sxs-lookup"><span data-stu-id="c0b9e-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c0b9e-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="c0b9e-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="c0b9e-114">Dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-114">The standard input device.</span></span> <span data-ttu-id="c0b9e-115">Inizialmente, si tratta del buffer di input della console `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="c0b9e-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="c0b9e-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="c0b9e-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="c0b9e-117">Dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-117">The standard output device.</span></span> <span data-ttu-id="c0b9e-118">Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="c0b9e-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="c0b9e-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="c0b9e-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="c0b9e-120">Dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-120">The standard error device.</span></span> <span data-ttu-id="c0b9e-121">Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="c0b9e-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="c0b9e-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c0b9e-122">Return value</span></span>

<span data-ttu-id="c0b9e-123">Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente a [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="c0b9e-124">L'handle dispone di diritti di accesso di **\_ lettura** e **\_ scrittura** generici, a meno che l'applicazione non abbia utilizzato **SetStdHandle** per impostare un handle standard con accesso minore.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="c0b9e-125">Se la funzione ha esito negativo, il valore restituito è un **\_ \_ valore di handle non valido**.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="c0b9e-126">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="c0b9e-127">Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo e non è stato reindirizzato, il valore restituito è **null**.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0b9e-128">Commenti</span><span class="sxs-lookup"><span data-stu-id="c0b9e-128">Remarks</span></span>

<span data-ttu-id="c0b9e-129">Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="c0b9e-130">Quando viene creata una console, l'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle del buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="c0b9e-131">Questi handle possono essere usati dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o da qualsiasi funzione console che accede al buffer di input della console o a un buffer dello schermo (ad esempio, le funzioni [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="c0b9e-132">Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="c0b9e-133">Se gli handle standard sono stati reindirizzati, è possibile specificare il `CONIN$` valore in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="c0b9e-134">Analogamente, è possibile specificare il `CONOUT$` valore per ottenere un handle per il buffer dello schermo attivo di una console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="c0b9e-135">Gli handle standard di un processo all'immissione del metodo Main sono determinati dalla configurazione del flag [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) passato al linker quando è stata compilata l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="c0b9e-136">Specificando **/SUBSYSTEM: console** richiede che il sistema operativo riempia gli handle con una sessione della console all'avvio, se l'elemento padre non ha già riempito la tabella di handle standard in base all'ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="c0b9e-137">Al contrario, **/SUBSYSTEM: Windows** implica che l'applicazione non necessita di una console e probabilmente non utilizzerà gli handle standard.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="c0b9e-138">Altre informazioni sull'ereditarietà dell'handle sono reperibili nella documentazione di [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="c0b9e-139">Alcune applicazioni operano all'esterno dei limiti del sottosistema dichiarato; ad esempio, un'applicazione **/SUBSYSTEM: Windows** potrebbe controllare/utilizzare handle standard a scopo di registrazione o di debug, ma funzionare normalmente con un'interfaccia utente grafica.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="c0b9e-140">Queste applicazioni dovranno verificare accuratamente lo stato degli handle standard all'avvio e usare [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md)e [**FreeConsole**](freeconsole.md) per aggiungere o rimuovere una console, se necessario.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="c0b9e-141">Alcune applicazioni possono anche variare il comportamento del tipo di handle ereditato.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="c0b9e-142">Distinguere il tipo tra la console, la pipe, il file e altri possono essere eseguiti con [**FileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="c0b9e-143">Comportamento di collegamento/scollegamento</span><span class="sxs-lookup"><span data-stu-id="c0b9e-143">Attach/detach behavior</span></span>

<span data-ttu-id="c0b9e-144">Quando ci si connette a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF \_ USESTDHANDLES** durante la creazione del processo.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="c0b9e-145">Se il valore esistente dell'handle standard è **null** o il valore esistente dell'handle standard è simile a un pseudohandle della console, l'handle viene sostituito con un handle della console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="c0b9e-146">Quando un elemento padre usa sia **Create \_ New \_ console** che **STARTF \_ USESTDHANDLES** per creare un processo console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia **null** o un pseudohandle console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="c0b9e-147">I processi della console *devono* iniziare con gli handle standard pieni o verranno riempiti automaticamente con handle appropriati per una nuova console.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="c0b9e-148">Le applicazioni GUI (Graphical User Interface) possono essere avviate senza gli handle standard e non verranno compilate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c0b9e-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="c0b9e-149">Esempi</span><span class="sxs-lookup"><span data-stu-id="c0b9e-149">Examples</span></span>

<span data-ttu-id="c0b9e-150">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="c0b9e-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c0b9e-151">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c0b9e-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c0b9e-152">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c0b9e-152">Minimum supported client</span></span> | <span data-ttu-id="c0b9e-153">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="c0b9e-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c0b9e-154">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c0b9e-154">Minimum supported server</span></span> | <span data-ttu-id="c0b9e-155">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="c0b9e-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c0b9e-156">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c0b9e-156">Header</span></span> | <span data-ttu-id="c0b9e-157">ProcessEnv. h (tramite Winbase. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c0b9e-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="c0b9e-158">Libreria</span><span class="sxs-lookup"><span data-stu-id="c0b9e-158">Library</span></span> | <span data-ttu-id="c0b9e-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c0b9e-159">Kernel32.lib</span></span> |
| <span data-ttu-id="c0b9e-160">DLL</span><span class="sxs-lookup"><span data-stu-id="c0b9e-160">DLL</span></span> | <span data-ttu-id="c0b9e-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c0b9e-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c0b9e-162">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c0b9e-162">See also</span></span>

[<span data-ttu-id="c0b9e-163">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="c0b9e-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c0b9e-164">Handle della console</span><span class="sxs-lookup"><span data-stu-id="c0b9e-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="c0b9e-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-165">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="c0b9e-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="c0b9e-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="c0b9e-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-168">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="c0b9e-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="c0b9e-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="c0b9e-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="c0b9e-171">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
