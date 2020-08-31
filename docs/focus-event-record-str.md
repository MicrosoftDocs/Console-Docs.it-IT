---
title: Struttura FOCUS_EVENT_RECORD
description: Descrive un evento di attivazione in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059873"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="e7009-105">Struttura del record dell' \_ evento di attivazione \_</span><span class="sxs-lookup"><span data-stu-id="e7009-105">FOCUS\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="e7009-106">Descrive un evento di attivazione in una struttura di [\*\* \_ record di input\*\*](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="e7009-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="e7009-107">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="e7009-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="e7009-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e7009-108">Syntax</span></span>
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="e7009-109">Membri</span><span class="sxs-lookup"><span data-stu-id="e7009-109">Members</span></span>
-------

<span data-ttu-id="e7009-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="e7009-110">**bSetFocus**</span></span>  
<span data-ttu-id="e7009-111">Riservato.</span><span class="sxs-lookup"><span data-stu-id="e7009-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="e7009-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e7009-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e7009-113">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e7009-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e7009-114">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e7009-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7009-115">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e7009-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e7009-116">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e7009-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7009-117">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e7009-117">Header</span></span></p></td>
<td><span data-ttu-id="e7009-118">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e7009-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e7009-119"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7009-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e7009-120">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="e7009-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




