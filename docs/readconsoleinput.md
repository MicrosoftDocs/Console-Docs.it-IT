---
title: ReadConsoleInput (funzione)
description: Legge i dati da un buffer di input della console e li rimuove dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060401"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="c2299-104">ReadConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="c2299-104">ReadConsoleInput function</span></span>


<span data-ttu-id="c2299-105">Legge i dati da un buffer di input della console e li rimuove dal buffer.</span><span class="sxs-lookup"><span data-stu-id="c2299-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="c2299-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c2299-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="c2299-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c2299-107">Parameters</span></span>
----------

<span data-ttu-id="c2299-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c2299-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="c2299-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="c2299-109">A handle to the console input buffer.</span></span> <span data-ttu-id="c2299-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="c2299-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c2299-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c2299-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c2299-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="c2299-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="c2299-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.</span><span class="sxs-lookup"><span data-stu-id="c2299-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="c2299-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c2299-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="c2299-115">Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="c2299-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="c2299-116">*lpNumberOfEventsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="c2299-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="c2299-117">Puntatore a una variabile che riceve il numero di record di input letti.</span><span class="sxs-lookup"><span data-stu-id="c2299-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="c2299-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c2299-118">Return value</span></span>
------------

<span data-ttu-id="c2299-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="c2299-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c2299-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="c2299-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c2299-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c2299-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c2299-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c2299-122">Remarks</span></span>
-------

<span data-ttu-id="c2299-123">Se il numero di record richiesti nel parametro *nLength* supera il numero di record disponibili nel buffer, viene letto il numero disponibile.</span><span class="sxs-lookup"><span data-stu-id="c2299-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="c2299-124">La funzione non restituisce alcun risultato finché non viene letto almeno un record di input.</span><span class="sxs-lookup"><span data-stu-id="c2299-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="c2299-125">Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](https://msdn.microsoft.com/library/windows/desktop/ms687069) per determinare quando l'input della console non è stato letto.</span><span class="sxs-lookup"><span data-stu-id="c2299-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="c2299-126">Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="c2299-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="c2299-127">Per determinare il numero di record di input non letti nel buffer di input di una console, usare la funzione [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="c2299-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="c2299-128">Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="c2299-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="c2299-129">Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="c2299-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<span data-ttu-id="c2299-130">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="c2299-130">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="c2299-131">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="c2299-131">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="c2299-132">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="c2299-132">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="c2299-133">Esempi</span><span class="sxs-lookup"><span data-stu-id="c2299-133">Examples</span></span>
--------

<span data-ttu-id="c2299-134">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="c2299-134">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="c2299-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c2299-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c2299-136">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c2299-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c2299-137">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="c2299-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2299-138">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c2299-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c2299-139">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="c2299-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2299-140">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c2299-140">Header</span></span></p></td>
<td><span data-ttu-id="c2299-141">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c2299-141">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2299-142">Libreria</span><span class="sxs-lookup"><span data-stu-id="c2299-142">Library</span></span></p></td>
<td><span data-ttu-id="c2299-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c2299-143">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2299-144">DLL</span><span class="sxs-lookup"><span data-stu-id="c2299-144">DLL</span></span></p></td>
<td><span data-ttu-id="c2299-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c2299-145">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2299-146">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="c2299-146">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="c2299-147"><strong>ReadConsoleInputW</strong> (Unicode) e <strong>ReadConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="c2299-147"><strong>ReadConsoleInputW</strong> (Unicode) and <strong>ReadConsoleInputA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c2299-148"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c2299-148"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c2299-149">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="c2299-149">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c2299-150">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="c2299-150">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="c2299-151">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="c2299-151">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="c2299-152">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="c2299-152">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="c2299-153">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="c2299-153">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="c2299-154">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c2299-154">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="c2299-155">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="c2299-155">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="c2299-156">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="c2299-156">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="c2299-157">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="c2299-157">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="c2299-158">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="c2299-158">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="c2299-159">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c2299-159">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




