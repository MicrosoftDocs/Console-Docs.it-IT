---
title: Struttura FOCUS_EVENT_RECORD
description: Descrive un evento di attivazione in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038169"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="d68d0-105">Struttura del record dell' \_ evento di attivazione \_</span><span class="sxs-lookup"><span data-stu-id="d68d0-105">FOCUS\_EVENT\_RECORD structure</span></span>

<span data-ttu-id="d68d0-106">Descrive un evento di attivazione in una struttura di [**\_ record di input**](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="d68d0-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="d68d0-107">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="d68d0-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="d68d0-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d68d0-108">Syntax</span></span>

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="d68d0-109">Members</span><span class="sxs-lookup"><span data-stu-id="d68d0-109">Members</span></span>

<span data-ttu-id="d68d0-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="d68d0-110">**bSetFocus**</span></span>  
<span data-ttu-id="d68d0-111">Riservato.</span><span class="sxs-lookup"><span data-stu-id="d68d0-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="d68d0-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d68d0-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d68d0-113">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d68d0-113">Minimum supported client</span></span> | <span data-ttu-id="d68d0-114">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="d68d0-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d68d0-115">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d68d0-115">Minimum supported server</span></span> | <span data-ttu-id="d68d0-116">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="d68d0-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d68d0-117">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d68d0-117">Header</span></span> | <span data-ttu-id="d68d0-118">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d68d0-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="d68d0-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d68d0-119">See also</span></span>

[<span data-ttu-id="d68d0-120">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="d68d0-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
