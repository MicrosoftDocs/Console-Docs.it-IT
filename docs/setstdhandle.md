---
title: SetStdHandle (funzione)
description: Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060532"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="33aca-104">SetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="33aca-104">SetStdHandle function</span></span>


<span data-ttu-id="33aca-105">Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="33aca-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="33aca-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33aca-106">Syntax</span></span>
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a><span data-ttu-id="33aca-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="33aca-107">Parameters</span></span>
----------

<span data-ttu-id="33aca-108">*nStdHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="33aca-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="33aca-109">Dispositivo standard per il quale deve essere impostato l'handle.</span><span class="sxs-lookup"><span data-stu-id="33aca-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="33aca-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="33aca-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="33aca-111">valore</span><span class="sxs-lookup"><span data-stu-id="33aca-111">Value</span></span></th>
<th><span data-ttu-id="33aca-112">Significato</span><span class="sxs-lookup"><span data-stu-id="33aca-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="33aca-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="33aca-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span></span></td>
<td><p><span data-ttu-id="33aca-114">Dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="33aca-114">The standard input device.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="33aca-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="33aca-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span></span></td>
<td><p><span data-ttu-id="33aca-116">Dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="33aca-116">The standard output device.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="33aca-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="33aca-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span></span></td>
<td><p><span data-ttu-id="33aca-118">Dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="33aca-118">The standard error device.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="33aca-119">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="33aca-119">*hHandle* \[in\]</span></span>  
<span data-ttu-id="33aca-120">Handle per il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="33aca-120">The handle for the standard device.</span></span>

<a name="return-value"></a><span data-ttu-id="33aca-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="33aca-121">Return value</span></span>
------------

<span data-ttu-id="33aca-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="33aca-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="33aca-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="33aca-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="33aca-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="33aca-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="33aca-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="33aca-125">Remarks</span></span>
-------

<span data-ttu-id="33aca-126">Gli handle standard di un processo potrebbero essere stati reindirizzati da una chiamata a **SetStdHandle**, nel qual caso [**GetStdHandle**](getstdhandle.md) restituirà l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="33aca-126">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="33aca-127">Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="33aca-127">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="33aca-128">Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="33aca-128">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="33aca-129">Esempi</span><span class="sxs-lookup"><span data-stu-id="33aca-129">Examples</span></span>
--------

<span data-ttu-id="33aca-130">Per un esempio, vedere [creazione di un processo figlio con input e output reindirizzati](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="33aca-130">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

<a name="requirements"></a><span data-ttu-id="33aca-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="33aca-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="33aca-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="33aca-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="33aca-133">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="33aca-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33aca-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="33aca-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="33aca-135">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="33aca-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33aca-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="33aca-136">Header</span></span></p></td>
<td><span data-ttu-id="33aca-137">ProcessEnv. h (tramite Winbase. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="33aca-137">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33aca-138">Libreria</span><span class="sxs-lookup"><span data-stu-id="33aca-138">Library</span></span></p></td>
<td><span data-ttu-id="33aca-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="33aca-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33aca-140">DLL</span><span class="sxs-lookup"><span data-stu-id="33aca-140">DLL</span></span></p></td>
<td><span data-ttu-id="33aca-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33aca-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="33aca-142"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33aca-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="33aca-143">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="33aca-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="33aca-144">Handle della console</span><span class="sxs-lookup"><span data-stu-id="33aca-144">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="33aca-145">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="33aca-145">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="33aca-146">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="33aca-146">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




