---
title: Struttura WINDOW_BUFFER_SIZE_RECORD
description: Vedere le informazioni di riferimento sulla struttura WINDOW_BUFFER_SIZE_RECORD, che descrive una modifica delle dimensioni del buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060545"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="bbd0c-104">\_ \_ Struttura record dimensioni buffer finestra \_</span><span class="sxs-lookup"><span data-stu-id="bbd0c-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>


<span data-ttu-id="bbd0c-105">Descrive una modifica delle dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-105">Describes a change in the size of the console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="bbd0c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bbd0c-106">Syntax</span></span>
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a><span data-ttu-id="bbd0c-107">Membri</span><span class="sxs-lookup"><span data-stu-id="bbd0c-107">Members</span></span>
-------

<span data-ttu-id="bbd0c-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="bbd0c-108">**dwSize**</span></span>  
<span data-ttu-id="bbd0c-109">Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne e righe di celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="bbd0c-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

<a name="remarks"></a><span data-ttu-id="bbd0c-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bbd0c-110">Remarks</span></span>
-------

<span data-ttu-id="bbd0c-111">Gli eventi di dimensioni del buffer vengono inseriti nel buffer di input quando la console di è in modalità compatibile con la finestra (**Abilita \_ \_ input finestra**).</span><span class="sxs-lookup"><span data-stu-id="bbd0c-111">Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).</span></span>

<a name="examples"></a><span data-ttu-id="bbd0c-112">Esempi</span><span class="sxs-lookup"><span data-stu-id="bbd0c-112">Examples</span></span>
--------

<span data-ttu-id="bbd0c-113">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="bbd0c-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="bbd0c-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bbd0c-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bbd0c-115">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="bbd0c-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bbd0c-116">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="bbd0c-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bbd0c-117">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="bbd0c-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bbd0c-118">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="bbd0c-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bbd0c-119">Intestazione</span><span class="sxs-lookup"><span data-stu-id="bbd0c-119">Header</span></span></p></td>
<td><span data-ttu-id="bbd0c-120">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bbd0c-120">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bbd0c-121"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbd0c-121"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bbd0c-122">**COORD**</span><span class="sxs-lookup"><span data-stu-id="bbd0c-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="bbd0c-123">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="bbd0c-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="bbd0c-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bbd0c-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

 

 




