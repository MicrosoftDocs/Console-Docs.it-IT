---
title: Struttura CONSOLE_SELECTION_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SELECTION_INFO, che contiene informazioni per la selezione di una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038369"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="a3dd0-104">Struttura delle informazioni di \_ selezione della console \_</span><span class="sxs-lookup"><span data-stu-id="a3dd0-104">CONSOLE\_SELECTION\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="a3dd0-105">Contiene informazioni per la selezione di una console.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-105">Contains information for a console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3dd0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a3dd0-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a><span data-ttu-id="a3dd0-107">Members</span><span class="sxs-lookup"><span data-stu-id="a3dd0-107">Members</span></span>

<span data-ttu-id="a3dd0-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-108">**dwFlags**</span></span>  
<span data-ttu-id="a3dd0-109">Indicatore di selezione.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-109">The selection indicator.</span></span> <span data-ttu-id="a3dd0-110">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-110">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="a3dd0-111">Valore</span><span class="sxs-lookup"><span data-stu-id="a3dd0-111">Value</span></span> | <span data-ttu-id="a3dd0-112">Significato</span><span class="sxs-lookup"><span data-stu-id="a3dd0-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="a3dd0-113">**CONSOLE_MOUSE_DOWN** 0x0008</span><span class="sxs-lookup"><span data-stu-id="a3dd0-113">**CONSOLE_MOUSE_DOWN** 0x0008</span></span> | <span data-ttu-id="a3dd0-114">Il mouse è inattivo.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-114">Mouse is down.</span></span> <span data-ttu-id="a3dd0-115">L'utente sta modificando attivamente il rettangolo di selezione con il mouse.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-115">The user is actively adjusting the selection rectangle with a mouse.</span></span> |
| <span data-ttu-id="a3dd0-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span><span class="sxs-lookup"><span data-stu-id="a3dd0-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span></span> | <span data-ttu-id="a3dd0-117">Selezione con il mouse.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-117">Selecting with the mouse.</span></span> <span data-ttu-id="a3dd0-118">Se è disattivata, l'utente è la `conhost.exe` selezione della modalità contrassegno operativo con la tastiera.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-118">If off, the user is operating `conhost.exe` mark mode selection with the keyboard.</span></span> |
| <span data-ttu-id="a3dd0-119">**CONSOLE_NO_SELECTION** 0x0000</span><span class="sxs-lookup"><span data-stu-id="a3dd0-119">**CONSOLE_NO_SELECTION** 0x0000</span></span> | <span data-ttu-id="a3dd0-120">Nessuna selezione.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-120">No selection.</span></span> |
| <span data-ttu-id="a3dd0-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span><span class="sxs-lookup"><span data-stu-id="a3dd0-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span></span> | <span data-ttu-id="a3dd0-122">La selezione è iniziata.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-122">Selection has begun.</span></span> <span data-ttu-id="a3dd0-123">Se una selezione del mouse non si verifica in genere senza il `CONSOLE_SELECTION_NOT_EMPTY` flag.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-123">If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag.</span></span> <span data-ttu-id="a3dd0-124">Se si seleziona una tastiera, questo può verificarsi quando è stata immessa la modalità contrassegno, ma l'utente continua a spostarsi nella posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-124">If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position.</span></span> |
| <span data-ttu-id="a3dd0-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span><span class="sxs-lookup"><span data-stu-id="a3dd0-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span></span> | <span data-ttu-id="a3dd0-126">Rettangolo di selezione non vuoto.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-126">Selection rectangle not empty.</span></span> <span data-ttu-id="a3dd0-127">Il payload di *dwSelectionAnchor* e *srSelection* sono validi.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-127">The payload of *dwSelectionAnchor* and *srSelection* are valid.</span></span>  |

<span data-ttu-id="a3dd0-128">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-128">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="a3dd0-129">Struttura [**Coord**](coord-str.md) che specifica l'ancoraggio di selezione, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-129">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="a3dd0-130">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-130">**srSelection**</span></span>  
<span data-ttu-id="a3dd0-131">Struttura [**\_ Rect piccola**](small-rect-str.md) che specifica il rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a3dd0-131">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3dd0-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a3dd0-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="a3dd0-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a3dd0-133">Minimum supported client</span></span> | <span data-ttu-id="a3dd0-134">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="a3dd0-134">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="a3dd0-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a3dd0-135">Minimum supported server</span></span> | <span data-ttu-id="a3dd0-136">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="a3dd0-136">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="a3dd0-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="a3dd0-137">Header</span></span> | <span data-ttu-id="a3dd0-138">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a3dd0-138">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="a3dd0-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a3dd0-139">See also</span></span>

[<span data-ttu-id="a3dd0-140">**COORD**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-140">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="a3dd0-141">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-141">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="a3dd0-142">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="a3dd0-142">**SMALL\_RECT**</span></span>](small-rect-str.md)
