---
title: SetConsoleCursorInfo (funzione)
description: Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 81f16e8c9d9cf90008bbd2e8619c2fa105d04212
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060289"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="33e7c-104">SetConsoleCursorInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="33e7c-104">SetConsoleCursorInfo function</span></span>


<span data-ttu-id="33e7c-105">Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="33e7c-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="33e7c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33e7c-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="33e7c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="33e7c-107">Parameters</span></span>
----------

<span data-ttu-id="33e7c-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="33e7c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="33e7c-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="33e7c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="33e7c-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="33e7c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="33e7c-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="33e7c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="33e7c-112">*lpConsoleCursorInfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="33e7c-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="33e7c-113">Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che fornisce le nuove specifiche per il cursore del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="33e7c-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="33e7c-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="33e7c-114">Return value</span></span>
------------

<span data-ttu-id="33e7c-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="33e7c-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="33e7c-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="33e7c-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="33e7c-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="33e7c-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="33e7c-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="33e7c-118">Remarks</span></span>
-------

<span data-ttu-id="33e7c-119">Quando il cursore di un buffer dello schermo è visibile, l'aspetto può variare, a partire dal riempimento completo di una cella di tipo carattere per essere visualizzata come linea orizzontale nella parte inferiore della cella.</span><span class="sxs-lookup"><span data-stu-id="33e7c-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="33e7c-120">Il membro **dwSize** della struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) specifica la percentuale di una cella di tipo carattere compilata dal cursore.</span><span class="sxs-lookup"><span data-stu-id="33e7c-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="33e7c-121">Se questo membro è minore di 1 o maggiore di 100, **SetConsoleCursorInfo** ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="33e7c-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

<a name="requirements"></a><span data-ttu-id="33e7c-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="33e7c-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="33e7c-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="33e7c-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="33e7c-124">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="33e7c-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33e7c-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="33e7c-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="33e7c-126">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="33e7c-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33e7c-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="33e7c-127">Header</span></span></p></td>
<td><span data-ttu-id="33e7c-128">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="33e7c-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="33e7c-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="33e7c-129">Library</span></span></p></td>
<td><span data-ttu-id="33e7c-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="33e7c-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="33e7c-131">DLL</span><span class="sxs-lookup"><span data-stu-id="33e7c-131">DLL</span></span></p></td>
<td><span data-ttu-id="33e7c-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33e7c-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="33e7c-133"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33e7c-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="33e7c-134">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="33e7c-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="33e7c-135">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="33e7c-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="33e7c-136">**\_informazioni cursore \_ console**</span><span class="sxs-lookup"><span data-stu-id="33e7c-136">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="33e7c-137">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="33e7c-137">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="33e7c-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="33e7c-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

 

 




