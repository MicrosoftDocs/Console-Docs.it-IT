---
title: Struttura WINDOW_BUFFER_SIZE_RECORD
description: Vedere le informazioni di riferimento sulla struttura WINDOW_BUFFER_SIZE_RECORD, che descrive una modifica delle dimensioni del buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039269"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="aa956-104">\_ \_ Struttura record dimensioni buffer finestra \_</span><span class="sxs-lookup"><span data-stu-id="aa956-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>

<span data-ttu-id="aa956-105">Descrive una modifica delle dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="aa956-105">Describes a change in the size of the console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa956-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa956-106">Syntax</span></span>

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a><span data-ttu-id="aa956-107">Members</span><span class="sxs-lookup"><span data-stu-id="aa956-107">Members</span></span>

<span data-ttu-id="aa956-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="aa956-108">**dwSize**</span></span>  
<span data-ttu-id="aa956-109">Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne e righe di celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="aa956-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa956-110">Commenti</span><span class="sxs-lookup"><span data-stu-id="aa956-110">Remarks</span></span>

<span data-ttu-id="aa956-111">Gli eventi di dimensioni del buffer vengono inseriti nel buffer di input quando la console di è in modalità compatibile con la finestra ( **Abilita \_ \_ input finestra** ).</span><span class="sxs-lookup"><span data-stu-id="aa956-111">Buffer size events are placed in the input buffer when the console is in window-aware mode ( **ENABLE\_WINDOW\_INPUT** ).</span></span>

## <a name="examples"></a><span data-ttu-id="aa956-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="aa956-112">Examples</span></span>

<span data-ttu-id="aa956-113">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="aa956-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="aa956-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aa956-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="aa956-115">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa956-115">Minimum supported client</span></span> | <span data-ttu-id="aa956-116">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="aa956-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa956-117">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa956-117">Minimum supported server</span></span> | <span data-ttu-id="aa956-118">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="aa956-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa956-119">Intestazione</span><span class="sxs-lookup"><span data-stu-id="aa956-119">Header</span></span> | <span data-ttu-id="aa956-120">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="aa956-120">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="aa956-121">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="aa956-121">See also</span></span>

[<span data-ttu-id="aa956-122">**COORD**</span><span class="sxs-lookup"><span data-stu-id="aa956-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="aa956-123">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="aa956-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="aa956-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="aa956-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)
