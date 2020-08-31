---
title: Struttura MENU_EVENT_RECORD
description: Descrive un evento di menu in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059617"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="95155-105">Struttura del record dell' \_ evento menu \_</span><span class="sxs-lookup"><span data-stu-id="95155-105">MENU\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="95155-106">Descrive un evento di menu in una struttura di [\*\* \_ record di input\*\*](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="95155-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="95155-107">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="95155-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="95155-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="95155-108">Syntax</span></span>
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="95155-109">Membri</span><span class="sxs-lookup"><span data-stu-id="95155-109">Members</span></span>
-------

<span data-ttu-id="95155-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="95155-110">**dwCommandId**</span></span>  
<span data-ttu-id="95155-111">Riservato.</span><span class="sxs-lookup"><span data-stu-id="95155-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="95155-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="95155-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="95155-113">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="95155-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="95155-114">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="95155-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="95155-115">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="95155-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="95155-116">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="95155-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="95155-117">Intestazione</span><span class="sxs-lookup"><span data-stu-id="95155-117">Header</span></span></p></td>
<td><span data-ttu-id="95155-118">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="95155-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="95155-119"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="95155-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="95155-120">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="95155-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




