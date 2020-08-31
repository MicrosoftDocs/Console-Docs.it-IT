---
title: GetStdHandle (funzione)
description: Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059625"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="144ff-104">GetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="144ff-104">GetStdHandle function</span></span>


<span data-ttu-id="144ff-105">Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="144ff-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="144ff-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="144ff-106">Syntax</span></span>
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a><span data-ttu-id="144ff-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="144ff-107">Parameters</span></span>
----------

<span data-ttu-id="144ff-108">*nStdHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="144ff-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="144ff-109">Il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="144ff-109">The standard device.</span></span> <span data-ttu-id="144ff-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="144ff-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="144ff-111">valore</span><span class="sxs-lookup"><span data-stu-id="144ff-111">Value</span></span></th>
<th><span data-ttu-id="144ff-112">Significato</span><span class="sxs-lookup"><span data-stu-id="144ff-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="144ff-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="144ff-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span></span></td>
<td><p><span data-ttu-id="144ff-114">Dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="144ff-114">The standard input device.</span></span> <span data-ttu-id="144ff-115">Inizialmente, si tratta del buffer di input della console, CONIn $.</span><span class="sxs-lookup"><span data-stu-id="144ff-115">Initially, this is the console input buffer, CONIN$.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="144ff-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="144ff-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span></span></td>
<td><p><span data-ttu-id="144ff-117">Dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="144ff-117">The standard output device.</span></span> <span data-ttu-id="144ff-118">Inizialmente, si tratta del buffer dello schermo della console attivo, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="144ff-118">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="144ff-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="144ff-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span></span></td>
<td><p><span data-ttu-id="144ff-120">Dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="144ff-120">The standard error device.</span></span> <span data-ttu-id="144ff-121">Inizialmente, si tratta del buffer dello schermo della console attivo, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="144ff-121">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="144ff-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="144ff-122">Return value</span></span>
------------

<span data-ttu-id="144ff-123">Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente a [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="144ff-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="144ff-124">L'handle dispone di diritti di accesso di \*\* \_ lettura\*\* e \*\* \_ scrittura\*\* generici, a meno che l'applicazione non abbia utilizzato **SetStdHandle** per impostare un handle standard con accesso minore.</span><span class="sxs-lookup"><span data-stu-id="144ff-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="144ff-125">Se la funzione ha esito negativo, il valore restituito è un \*\* \_ \_ valore di handle non valido\*\*.</span><span class="sxs-lookup"><span data-stu-id="144ff-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="144ff-126">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="144ff-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="144ff-127">Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo e non è stato reindirizzato, il valore restituito è **null**.</span><span class="sxs-lookup"><span data-stu-id="144ff-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

<a name="remarks"></a><span data-ttu-id="144ff-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="144ff-128">Remarks</span></span>
-------

<span data-ttu-id="144ff-129">Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console.</span><span class="sxs-lookup"><span data-stu-id="144ff-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="144ff-130">Quando viene creata una console, l'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle del buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="144ff-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="144ff-131">Questi handle possono essere usati dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o da qualsiasi funzione console che accede al buffer di input della console o a un buffer dello schermo (ad esempio, le funzioni [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).</span><span class="sxs-lookup"><span data-stu-id="144ff-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="144ff-132">Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="144ff-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="144ff-133">Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="144ff-133">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="144ff-134">Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo di una console.</span><span class="sxs-lookup"><span data-stu-id="144ff-134">Similarly, you can specify the CONOUT$ value to get a handle to a console's active screen buffer.</span></span>

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span data-ttu-id="144ff-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportamento di collegamento/scollegamento</span><span class="sxs-lookup"><span data-stu-id="144ff-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Attach/detach behavior</span></span>

<span data-ttu-id="144ff-136">Quando ci si connette a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF \_ USESTDHANDLES** durante la creazione del processo.</span><span class="sxs-lookup"><span data-stu-id="144ff-136">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="144ff-137">Se il valore esistente dell'handle standard è **null**o il valore esistente dell'handle standard è simile a un pseudohandle della console, l'handle viene sostituito con un handle della console.</span><span class="sxs-lookup"><span data-stu-id="144ff-137">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="144ff-138">Quando un elemento padre usa sia **Create \_ New \_ console** che **STARTF \_ USESTDHANDLES** per creare un processo console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia null o un pseudohandle console.</span><span class="sxs-lookup"><span data-stu-id="144ff-138">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is NULL or a console pseudohandle.</span></span>

<a name="examples"></a><span data-ttu-id="144ff-139">Esempi</span><span class="sxs-lookup"><span data-stu-id="144ff-139">Examples</span></span>
--------

<span data-ttu-id="144ff-140">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="144ff-140">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="144ff-141">Requisiti</span><span class="sxs-lookup"><span data-stu-id="144ff-141">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="144ff-142">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="144ff-142">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="144ff-143">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="144ff-143">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="144ff-144">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="144ff-144">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="144ff-145">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="144ff-145">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="144ff-146">Intestazione</span><span class="sxs-lookup"><span data-stu-id="144ff-146">Header</span></span></p></td>
<td><span data-ttu-id="144ff-147">ProcessEnv. h (tramite Winbase. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="144ff-147">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="144ff-148">Libreria</span><span class="sxs-lookup"><span data-stu-id="144ff-148">Library</span></span></p></td>
<td><span data-ttu-id="144ff-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="144ff-149">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="144ff-150">DLL</span><span class="sxs-lookup"><span data-stu-id="144ff-150">DLL</span></span></p></td>
<td><span data-ttu-id="144ff-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="144ff-151">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="144ff-152"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="144ff-152"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="144ff-153">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="144ff-153">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="144ff-154">Handle della console</span><span class="sxs-lookup"><span data-stu-id="144ff-154">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="144ff-155">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="144ff-155">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="144ff-156">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="144ff-156">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="144ff-157">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="144ff-157">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="144ff-158">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="144ff-158">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="144ff-159">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="144ff-159">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="144ff-160">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="144ff-160">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="144ff-161">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="144ff-161">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




