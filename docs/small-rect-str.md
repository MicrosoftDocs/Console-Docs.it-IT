---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Struttura SMALL_RECT
description: Definisce le coordinate degli angoli superiore sinistro e inferiore destro di un rettangolo.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060556"
---
# <a name="small_rect-structure"></a><span data-ttu-id="60fac-104">\_Struttura Rect piccola</span><span class="sxs-lookup"><span data-stu-id="60fac-104">SMALL\_RECT structure</span></span>


<span data-ttu-id="60fac-105">Definisce le coordinate degli angoli superiore sinistro e inferiore destro di un rettangolo.</span><span class="sxs-lookup"><span data-stu-id="60fac-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

<a name="syntax"></a><span data-ttu-id="60fac-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="60fac-106">Syntax</span></span>
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a><span data-ttu-id="60fac-107">Membri</span><span class="sxs-lookup"><span data-stu-id="60fac-107">Members</span></span>
-------

<span data-ttu-id="60fac-108">**Sinistra**</span><span class="sxs-lookup"><span data-stu-id="60fac-108">**Left**</span></span>  
<span data-ttu-id="60fac-109">Coordinata x dell'angolo superiore sinistro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="60fac-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="60fac-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="60fac-110">**Top**</span></span>  
<span data-ttu-id="60fac-111">Coordinata y dell'angolo superiore sinistro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="60fac-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="60fac-112">**Ok**</span><span class="sxs-lookup"><span data-stu-id="60fac-112">**Right**</span></span>  
<span data-ttu-id="60fac-113">Coordinata x dell'angolo inferiore destro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="60fac-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="60fac-114">**Ultimo**</span><span class="sxs-lookup"><span data-stu-id="60fac-114">**Bottom**</span></span>  
<span data-ttu-id="60fac-115">Coordinata y dell'angolo inferiore destro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="60fac-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

<a name="remarks"></a><span data-ttu-id="60fac-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="60fac-116">Remarks</span></span>
-------

<span data-ttu-id="60fac-117">Questa struttura viene utilizzata dalle funzioni console per specificare le aree rettangolari dei buffer dello schermo della console, in cui le coordinate specificano le righe e le colonne delle celle dei caratteri del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="60fac-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

<a name="examples"></a><span data-ttu-id="60fac-118">Esempi</span><span class="sxs-lookup"><span data-stu-id="60fac-118">Examples</span></span>
--------

<span data-ttu-id="60fac-119">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="60fac-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="60fac-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="60fac-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="60fac-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="60fac-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="60fac-122">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="60fac-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="60fac-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="60fac-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="60fac-124">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="60fac-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="60fac-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="60fac-125">Header</span></span></p></td>
<td><span data-ttu-id="60fac-126">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="60fac-126">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="60fac-127"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="60fac-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="60fac-128">**RECT**</span><span class="sxs-lookup"><span data-stu-id="60fac-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="60fac-129">**RECTL**</span><span class="sxs-lookup"><span data-stu-id="60fac-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




