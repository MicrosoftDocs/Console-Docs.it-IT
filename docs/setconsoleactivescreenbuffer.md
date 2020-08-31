---
title: SetConsoleActiveScreenBuffer (funzione)
description: Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f3fa9d79705c95fc0737597886b5562ce1045c45
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060300"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="2934a-104">SetConsoleActiveScreenBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="2934a-104">SetConsoleActiveScreenBuffer function</span></span>


<span data-ttu-id="2934a-105">Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.</span><span class="sxs-lookup"><span data-stu-id="2934a-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="2934a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2934a-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="2934a-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="2934a-107">Parameters</span></span>
----------

<span data-ttu-id="2934a-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2934a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2934a-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2934a-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="2934a-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2934a-110">Return value</span></span>
------------

<span data-ttu-id="2934a-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2934a-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2934a-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2934a-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2934a-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2934a-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2934a-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2934a-114">Remarks</span></span>
-------

<span data-ttu-id="2934a-115">Una console può avere più buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="2934a-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="2934a-116">**SetConsoleActiveScreenBuffer** determina quale viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="2934a-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="2934a-117">È possibile scrivere in un buffer dello schermo inattivo e quindi usare **SetConsoleActiveScreenBuffer** per visualizzare il contenuto del buffer.</span><span class="sxs-lookup"><span data-stu-id="2934a-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

<a name="examples"></a><span data-ttu-id="2934a-118">Esempi</span><span class="sxs-lookup"><span data-stu-id="2934a-118">Examples</span></span>
--------

<span data-ttu-id="2934a-119">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2934a-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="2934a-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2934a-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2934a-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2934a-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2934a-122">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2934a-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2934a-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2934a-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2934a-124">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2934a-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2934a-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2934a-125">Header</span></span></p></td>
<td><span data-ttu-id="2934a-126">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2934a-126">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2934a-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="2934a-127">Library</span></span></p></td>
<td><span data-ttu-id="2934a-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2934a-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2934a-129">DLL</span><span class="sxs-lookup"><span data-stu-id="2934a-129">DLL</span></span></p></td>
<td><span data-ttu-id="2934a-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2934a-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2934a-131"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2934a-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2934a-132">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="2934a-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2934a-133">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="2934a-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="2934a-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="2934a-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)

 

 




