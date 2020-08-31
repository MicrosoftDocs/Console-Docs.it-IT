---
title: PeekConsoleInput (funzione)
description: Legge i dati dal buffer di input della console specificato senza rimuoverlo dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c74df91f3b70827cd0c5410d01b2a165694909f9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059580"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="69b33-104">PeekConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="69b33-104">PeekConsoleInput function</span></span>


<span data-ttu-id="69b33-105">Legge i dati dal buffer di input della console specificato senza rimuoverlo dal buffer.</span><span class="sxs-lookup"><span data-stu-id="69b33-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="69b33-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69b33-106">Syntax</span></span>
------

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="69b33-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="69b33-107">Parameters</span></span>
----------

<span data-ttu-id="69b33-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="69b33-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="69b33-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="69b33-109">A handle to the console input buffer.</span></span> <span data-ttu-id="69b33-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="69b33-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="69b33-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="69b33-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="69b33-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="69b33-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="69b33-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.</span><span class="sxs-lookup"><span data-stu-id="69b33-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="69b33-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="69b33-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="69b33-115">Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="69b33-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="69b33-116">*lpNumberOfEventsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="69b33-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="69b33-117">Puntatore a una variabile che riceve il numero di record di input letti.</span><span class="sxs-lookup"><span data-stu-id="69b33-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="69b33-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="69b33-118">Return value</span></span>
------------

<span data-ttu-id="69b33-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="69b33-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="69b33-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="69b33-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="69b33-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="69b33-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="69b33-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="69b33-122">Remarks</span></span>
-------

<span data-ttu-id="69b33-123">Se il numero di record richiesti supera il numero di record disponibili nel buffer, viene letto il numero disponibile.</span><span class="sxs-lookup"><span data-stu-id="69b33-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="69b33-124">Se non sono disponibili dati, la funzione restituisce immediatamente il risultato.</span><span class="sxs-lookup"><span data-stu-id="69b33-124">If no data is available, the function returns immediately.</span></span>

<span data-ttu-id="69b33-125">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="69b33-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="69b33-126">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="69b33-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="69b33-127">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="69b33-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="69b33-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="69b33-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="69b33-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="69b33-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="69b33-130">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="69b33-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69b33-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="69b33-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="69b33-132">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="69b33-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69b33-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="69b33-133">Header</span></span></p></td>
<td><span data-ttu-id="69b33-134">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="69b33-134">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69b33-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="69b33-135">Library</span></span></p></td>
<td><span data-ttu-id="69b33-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="69b33-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69b33-137">DLL</span><span class="sxs-lookup"><span data-stu-id="69b33-137">DLL</span></span></p></td>
<td><span data-ttu-id="69b33-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="69b33-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69b33-139">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="69b33-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="69b33-140"><strong>PeekConsoleInputW</strong> (Unicode) e <strong>PeekConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="69b33-140"><strong>PeekConsoleInputW</strong> (Unicode) and <strong>PeekConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="69b33-141"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69b33-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="69b33-142">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="69b33-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="69b33-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="69b33-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="69b33-144">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="69b33-144">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="69b33-145">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="69b33-145">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="69b33-146">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="69b33-146">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="69b33-147">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="69b33-147">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




