---
title: Struttura MENU_EVENT_RECORD
description: Descrive un evento di menu in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039519"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="5eb84-105">Struttura del record dell' \_ evento menu \_</span><span class="sxs-lookup"><span data-stu-id="5eb84-105">MENU\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5eb84-106">Descrive un evento di menu in una struttura di [**\_ record di input**](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="5eb84-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="5eb84-107">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="5eb84-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="5eb84-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5eb84-108">Syntax</span></span>

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="5eb84-109">Members</span><span class="sxs-lookup"><span data-stu-id="5eb84-109">Members</span></span>

<span data-ttu-id="5eb84-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="5eb84-110">**dwCommandId**</span></span>  
<span data-ttu-id="5eb84-111">Riservato.</span><span class="sxs-lookup"><span data-stu-id="5eb84-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="5eb84-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5eb84-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5eb84-113">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5eb84-113">Minimum supported client</span></span> | <span data-ttu-id="5eb84-114">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="5eb84-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5eb84-115">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5eb84-115">Minimum supported server</span></span> | <span data-ttu-id="5eb84-116">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="5eb84-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5eb84-117">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5eb84-117">Header</span></span> | <span data-ttu-id="5eb84-118">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5eb84-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5eb84-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5eb84-119">See also</span></span>

[<span data-ttu-id="5eb84-120">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="5eb84-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
