---
title: Struttura COORD
description: Definisce le coordinate di una cella di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059940"
---
# <a name="coord-structure"></a><span data-ttu-id="f7afa-104">Struttura COORD</span><span class="sxs-lookup"><span data-stu-id="f7afa-104">COORD structure</span></span>


<span data-ttu-id="f7afa-105">Definisce le coordinate di una cella di tipo carattere in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f7afa-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="f7afa-106">L'origine del sistema di coordinate (0, 0) si trova nella parte superiore della cella sinistra del buffer.</span><span class="sxs-lookup"><span data-stu-id="f7afa-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="f7afa-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f7afa-107">Syntax</span></span>
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a><span data-ttu-id="f7afa-108">Membri</span><span class="sxs-lookup"><span data-stu-id="f7afa-108">Members</span></span>
-------

<span data-ttu-id="f7afa-109">**X**</span><span class="sxs-lookup"><span data-stu-id="f7afa-109">**X**</span></span>  
<span data-ttu-id="f7afa-110">Il valore della colonna o della coordinata orizzontale.</span><span class="sxs-lookup"><span data-stu-id="f7afa-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="f7afa-111">Le unità dipendono dalla chiamata di funzione.</span><span class="sxs-lookup"><span data-stu-id="f7afa-111">The units depend on the function call.</span></span>

<span data-ttu-id="f7afa-112">**S**</span><span class="sxs-lookup"><span data-stu-id="f7afa-112">**Y**</span></span>  
<span data-ttu-id="f7afa-113">Il valore della riga o della coordinata verticale.</span><span class="sxs-lookup"><span data-stu-id="f7afa-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="f7afa-114">Le unità dipendono dalla chiamata di funzione.</span><span class="sxs-lookup"><span data-stu-id="f7afa-114">The units depend on the function call.</span></span>

<a name="examples"></a><span data-ttu-id="f7afa-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="f7afa-115">Examples</span></span>
--------

<span data-ttu-id="f7afa-116">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="f7afa-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="f7afa-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f7afa-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f7afa-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f7afa-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f7afa-119">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f7afa-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f7afa-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f7afa-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f7afa-121">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f7afa-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f7afa-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="f7afa-122">Header</span></span></p></td>
<td><span data-ttu-id="f7afa-123">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f7afa-123">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f7afa-124"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f7afa-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f7afa-125">**informazioni sul tipo di carattere della CONSOLE \_ \_**</span><span class="sxs-lookup"><span data-stu-id="f7afa-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="f7afa-126">**\_informazioni sul \_ buffer dello schermo della console \_**</span><span class="sxs-lookup"><span data-stu-id="f7afa-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="f7afa-127">**\_informazioni selezione \_ console**</span><span class="sxs-lookup"><span data-stu-id="f7afa-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="f7afa-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f7afa-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="f7afa-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f7afa-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="f7afa-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="f7afa-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="f7afa-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="f7afa-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="f7afa-132">**\_record evento \_ mouse**</span><span class="sxs-lookup"><span data-stu-id="f7afa-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="f7afa-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f7afa-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="f7afa-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f7afa-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="f7afa-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f7afa-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="f7afa-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="f7afa-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="f7afa-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="f7afa-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="f7afa-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="f7afa-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="f7afa-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="f7afa-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="f7afa-140">**\_ \_ record dimensioni buffer \_ finestra**</span><span class="sxs-lookup"><span data-stu-id="f7afa-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="f7afa-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f7afa-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="f7afa-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f7afa-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="f7afa-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f7afa-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




