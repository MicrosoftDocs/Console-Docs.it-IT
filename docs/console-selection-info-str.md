---
title: Struttura CONSOLE_SELECTION_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SELECTION_INFO, che contiene informazioni per la selezione di una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060001"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="cae84-104">Struttura delle informazioni di \_ selezione della console \_</span><span class="sxs-lookup"><span data-stu-id="cae84-104">CONSOLE\_SELECTION\_INFO structure</span></span>


<span data-ttu-id="cae84-105">Contiene informazioni per la selezione di una console.</span><span class="sxs-lookup"><span data-stu-id="cae84-105">Contains information for a console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="cae84-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cae84-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a><span data-ttu-id="cae84-107">Membri</span><span class="sxs-lookup"><span data-stu-id="cae84-107">Members</span></span>
-------

<span data-ttu-id="cae84-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="cae84-108">**dwFlags**</span></span>  
<span data-ttu-id="cae84-109">Indicatore di selezione.</span><span class="sxs-lookup"><span data-stu-id="cae84-109">The selection indicator.</span></span> <span data-ttu-id="cae84-110">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="cae84-110">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="cae84-111">valore</span><span class="sxs-lookup"><span data-stu-id="cae84-111">Value</span></span></th>
<th><span data-ttu-id="cae84-112">Significato</span><span class="sxs-lookup"><span data-stu-id="cae84-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="cae84-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="cae84-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="cae84-114">Il mouse è inattivo</span><span class="sxs-lookup"><span data-stu-id="cae84-114">Mouse is down</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="cae84-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="cae84-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="cae84-116">Selezione con il mouse</span><span class="sxs-lookup"><span data-stu-id="cae84-116">Selecting with the mouse</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="cae84-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span><span class="sxs-lookup"><span data-stu-id="cae84-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span></span></td>
<td><p><span data-ttu-id="cae84-118">Nessuna selezione</span><span class="sxs-lookup"><span data-stu-id="cae84-118">No selection</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="cae84-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="cae84-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="cae84-120">Selezione iniziata</span><span class="sxs-lookup"><span data-stu-id="cae84-120">Selection has begun</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="cae84-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="cae84-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="cae84-122">Il rettangolo di selezione non è vuoto</span><span class="sxs-lookup"><span data-stu-id="cae84-122">Selection rectangle is not empty</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="cae84-123">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="cae84-123">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="cae84-124">Struttura [**Coord**](coord-str.md) che specifica l'ancoraggio di selezione, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="cae84-124">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="cae84-125">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="cae84-125">**srSelection**</span></span>  
<span data-ttu-id="cae84-126">Struttura [\*\* \_ Rect piccola\*\*](small-rect-str.md) che specifica il rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="cae84-126">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

<a name="requirements"></a><span data-ttu-id="cae84-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cae84-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="cae84-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cae84-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="cae84-129">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="cae84-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cae84-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cae84-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="cae84-131">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="cae84-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cae84-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="cae84-132">Header</span></span></p></td>
<td><span data-ttu-id="cae84-133">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cae84-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="cae84-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cae84-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="cae84-135">**COORD**</span><span class="sxs-lookup"><span data-stu-id="cae84-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="cae84-136">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="cae84-136">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="cae84-137">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="cae84-137">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




