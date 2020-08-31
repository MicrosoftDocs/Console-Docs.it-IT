---
title: Struttura CONSOLE_CURSOR_INFO
description: Contiene le informazioni sulle dimensioni e sulla visibilità relative al cursore della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060132"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="033a0-104">\_ \_ Struttura informazioni cursore console</span><span class="sxs-lookup"><span data-stu-id="033a0-104">CONSOLE\_CURSOR\_INFO structure</span></span>


<span data-ttu-id="033a0-105">Contiene informazioni sul cursore della console.</span><span class="sxs-lookup"><span data-stu-id="033a0-105">Contains information about the console cursor.</span></span>

<a name="syntax"></a><span data-ttu-id="033a0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="033a0-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a><span data-ttu-id="033a0-107">Membri</span><span class="sxs-lookup"><span data-stu-id="033a0-107">Members</span></span>
-------

<span data-ttu-id="033a0-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="033a0-108">**dwSize**</span></span>  
<span data-ttu-id="033a0-109">Percentuale della cella di tipo carattere compilata dal cursore.</span><span class="sxs-lookup"><span data-stu-id="033a0-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="033a0-110">Questo valore è compreso tra 1 e 100.</span><span class="sxs-lookup"><span data-stu-id="033a0-110">This value is between 1 and 100.</span></span> <span data-ttu-id="033a0-111">L'aspetto del cursore varia a seconda che la cella venga riempita completamente per essere visualizzata come riga orizzontale nella parte inferiore della cella.</span><span class="sxs-lookup"><span data-stu-id="033a0-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

<span data-ttu-id="033a0-112">**Nota**    Anche se il valore **dwSize** è in genere compreso tra 1 e 100, in alcune circostanze potrebbe essere restituito un valore esterno a tale intervallo.</span><span class="sxs-lookup"><span data-stu-id="033a0-112">**Note**  While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="033a0-113">Se, ad esempio, **CursorSize** è impostato su 0 nel registro di sistema, il valore **dwSize** restituito sarà 0.</span><span class="sxs-lookup"><span data-stu-id="033a0-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 

<span data-ttu-id="033a0-114">**bVisible**</span><span class="sxs-lookup"><span data-stu-id="033a0-114">**bVisible**</span></span>  
<span data-ttu-id="033a0-115">Visibilità del cursore.</span><span class="sxs-lookup"><span data-stu-id="033a0-115">The visibility of the cursor.</span></span> <span data-ttu-id="033a0-116">Se il cursore è visibile, questo membro è **true**.</span><span class="sxs-lookup"><span data-stu-id="033a0-116">If the cursor is visible, this member is **TRUE**.</span></span>

<a name="requirements"></a><span data-ttu-id="033a0-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="033a0-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="033a0-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="033a0-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="033a0-119">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="033a0-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="033a0-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="033a0-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="033a0-121">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="033a0-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="033a0-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="033a0-122">Header</span></span></p></td>
<td><span data-ttu-id="033a0-123">Wincon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="033a0-123">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="033a0-124"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="033a0-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="033a0-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="033a0-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="033a0-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="033a0-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




