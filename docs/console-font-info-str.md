---
title: Struttura CONSOLE_FONT_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFO, che contiene l'indice e le dimensioni per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060129"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="b6470-104">Struttura delle informazioni sul tipo di carattere della CONSOLE \_ \_</span><span class="sxs-lookup"><span data-stu-id="b6470-104">CONSOLE\_FONT\_INFO structure</span></span>


<span data-ttu-id="b6470-105">Contiene informazioni per un tipo di carattere della console.</span><span class="sxs-lookup"><span data-stu-id="b6470-105">Contains information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="b6470-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b6470-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a><span data-ttu-id="b6470-107">Membri</span><span class="sxs-lookup"><span data-stu-id="b6470-107">Members</span></span>
-------

<span data-ttu-id="b6470-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="b6470-108">**nFont**</span></span>  
<span data-ttu-id="b6470-109">Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.</span><span class="sxs-lookup"><span data-stu-id="b6470-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="b6470-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="b6470-110">**dwFontSize**</span></span>  
<span data-ttu-id="b6470-111">Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="b6470-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="b6470-112">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="b6470-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<a name="remarks"></a><span data-ttu-id="b6470-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b6470-113">Remarks</span></span>
-------

<span data-ttu-id="b6470-114">Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="b6470-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="b6470-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b6470-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b6470-116">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b6470-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b6470-117">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="b6470-117">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b6470-118">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b6470-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b6470-119">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="b6470-119">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b6470-120">Intestazione</span><span class="sxs-lookup"><span data-stu-id="b6470-120">Header</span></span></p></td>
<td><span data-ttu-id="b6470-121">Wincon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b6470-121">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b6470-122"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b6470-122"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b6470-123">**COORD**</span><span class="sxs-lookup"><span data-stu-id="b6470-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="b6470-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="b6470-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




