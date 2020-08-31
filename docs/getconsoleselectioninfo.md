---
title: GetConsoleSelectionInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleSelectionInfo, che recupera le informazioni sulla selezione corrente della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d29a960bc6b8d96d98e0667084e31354f2aa9653
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059705"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="1b274-104">GetConsoleSelectionInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="1b274-104">GetConsoleSelectionInfo function</span></span>


<span data-ttu-id="1b274-105">Recupera le informazioni sulla selezione corrente della console.</span><span class="sxs-lookup"><span data-stu-id="1b274-105">Retrieves information about the current console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="1b274-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1b274-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

<a name="parameters"></a><span data-ttu-id="1b274-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="1b274-107">Parameters</span></span>
----------

<span data-ttu-id="1b274-108">*lpConsoleSelectionInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="1b274-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="1b274-109">Puntatore a una struttura [**di \_ \_ informazioni di selezione della console**](console-selection-info-str.md) che riceve le informazioni di selezione.</span><span class="sxs-lookup"><span data-stu-id="1b274-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

<a name="return-value"></a><span data-ttu-id="1b274-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1b274-110">Return value</span></span>
------------

<span data-ttu-id="1b274-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="1b274-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1b274-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="1b274-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1b274-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1b274-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1b274-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1b274-114">Remarks</span></span>
-------

<span data-ttu-id="1b274-115">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="1b274-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="1b274-116">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1b274-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="1b274-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1b274-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1b274-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1b274-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1b274-119">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="1b274-119">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1b274-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1b274-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1b274-121">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="1b274-121">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1b274-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="1b274-122">Header</span></span></p></td>
<td><span data-ttu-id="1b274-123">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1b274-123">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1b274-124">Libreria</span><span class="sxs-lookup"><span data-stu-id="1b274-124">Library</span></span></p></td>
<td><span data-ttu-id="1b274-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1b274-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1b274-126">DLL</span><span class="sxs-lookup"><span data-stu-id="1b274-126">DLL</span></span></p></td>
<td><span data-ttu-id="1b274-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1b274-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1b274-128"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1b274-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1b274-129">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="1b274-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1b274-130">Selezione della console</span><span class="sxs-lookup"><span data-stu-id="1b274-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="1b274-131">**\_informazioni selezione \_ console**</span><span class="sxs-lookup"><span data-stu-id="1b274-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

 

 




