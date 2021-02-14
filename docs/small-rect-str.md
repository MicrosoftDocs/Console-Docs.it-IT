---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: f9cbe94fff616a93d835f47b618a28bb9f521891
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358491"
---
# <a name="small_rect-structure"></a><span data-ttu-id="aab6d-104">\_Struttura Rect piccola</span><span class="sxs-lookup"><span data-stu-id="aab6d-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="aab6d-105">Definisce le coordinate degli angoli superiore sinistro e inferiore destro di un rettangolo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="aab6d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aab6d-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="aab6d-107">Members</span><span class="sxs-lookup"><span data-stu-id="aab6d-107">Members</span></span>

<span data-ttu-id="aab6d-108">**Sinistra**</span><span class="sxs-lookup"><span data-stu-id="aab6d-108">**Left**</span></span>  
<span data-ttu-id="aab6d-109">Coordinata x dell'angolo superiore sinistro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="aab6d-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="aab6d-110">**Top**</span></span>  
<span data-ttu-id="aab6d-111">Coordinata y dell'angolo superiore sinistro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="aab6d-112">**Ok**</span><span class="sxs-lookup"><span data-stu-id="aab6d-112">**Right**</span></span>  
<span data-ttu-id="aab6d-113">Coordinata x dell'angolo inferiore destro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="aab6d-114">**Ultimo**</span><span class="sxs-lookup"><span data-stu-id="aab6d-114">**Bottom**</span></span>  
<span data-ttu-id="aab6d-115">Coordinata y dell'angolo inferiore destro del rettangolo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="aab6d-116">Commenti</span><span class="sxs-lookup"><span data-stu-id="aab6d-116">Remarks</span></span>

<span data-ttu-id="aab6d-117">Questa struttura viene utilizzata dalle funzioni console per specificare le aree rettangolari dei buffer dello schermo della console, in cui le coordinate specificano le righe e le colonne delle celle dei caratteri del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="aab6d-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="aab6d-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="aab6d-118">Examples</span></span>

<span data-ttu-id="aab6d-119">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="aab6d-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="aab6d-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aab6d-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="aab6d-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aab6d-121">Minimum supported client</span></span> | <span data-ttu-id="aab6d-122">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="aab6d-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="aab6d-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aab6d-123">Minimum supported server</span></span> | <span data-ttu-id="aab6d-124">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="aab6d-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="aab6d-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="aab6d-125">Header</span></span> | <span data-ttu-id="aab6d-126">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="aab6d-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="aab6d-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="aab6d-127">See also</span></span>

<span data-ttu-id="aab6d-128">[**RECT**](/previous-versions//dd162897(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="aab6d-128">[**RECT**](/previous-versions//dd162897(v=vs.85))</span></span>

<span data-ttu-id="aab6d-129">[**RECTL**](/previous-versions//dd162907(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="aab6d-129">[**RECTL**](/previous-versions//dd162907(v=vs.85))</span></span>