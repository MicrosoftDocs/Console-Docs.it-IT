---
title: Struttura CONSOLE_FONT_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFOEX, che contiene informazioni estese per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060100"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="fc62f-104">\_Struttura INFOEX del tipo di carattere della console \_</span><span class="sxs-lookup"><span data-stu-id="fc62f-104">CONSOLE\_FONT\_INFOEX structure</span></span>


<span data-ttu-id="fc62f-105">Contiene informazioni estese per un tipo di carattere della console.</span><span class="sxs-lookup"><span data-stu-id="fc62f-105">Contains extended information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="fc62f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fc62f-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a><span data-ttu-id="fc62f-107">Membri</span><span class="sxs-lookup"><span data-stu-id="fc62f-107">Members</span></span>
-------

<span data-ttu-id="fc62f-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="fc62f-108">**cbSize**</span></span>  
<span data-ttu-id="fc62f-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="fc62f-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="fc62f-110">Questo membro deve essere impostato su `sizeof(CONSOLE_FONT_INFOEX)` prima di chiamare [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="fc62f-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="fc62f-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="fc62f-111">**nFont**</span></span>  
<span data-ttu-id="fc62f-112">Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.</span><span class="sxs-lookup"><span data-stu-id="fc62f-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="fc62f-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="fc62f-113">**dwFontSize**</span></span>  
<span data-ttu-id="fc62f-114">Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="fc62f-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="fc62f-115">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="fc62f-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="fc62f-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="fc62f-116">**FontFamily**</span></span>  
<span data-ttu-id="fc62f-117">Il passo del carattere e la famiglia.</span><span class="sxs-lookup"><span data-stu-id="fc62f-117">The font pitch and family.</span></span> <span data-ttu-id="fc62f-118">Per informazioni sui valori possibili per questo membro, vedere la descrizione del membro **tmPitchAndFamily** della struttura [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .</span><span class="sxs-lookup"><span data-stu-id="fc62f-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="fc62f-119">**SpessoreCarattere**</span><span class="sxs-lookup"><span data-stu-id="fc62f-119">**FontWeight**</span></span>  
<span data-ttu-id="fc62f-120">Spessore del carattere.</span><span class="sxs-lookup"><span data-stu-id="fc62f-120">The font weight.</span></span> <span data-ttu-id="fc62f-121">Il peso può variare da 100 a 1000, in multipli di 100.</span><span class="sxs-lookup"><span data-stu-id="fc62f-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="fc62f-122">Ad esempio, il peso normale è 400, mentre 700 è in grassetto.</span><span class="sxs-lookup"><span data-stu-id="fc62f-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="fc62f-123">**Contemplato**</span><span class="sxs-lookup"><span data-stu-id="fc62f-123">**FaceName**</span></span>  
<span data-ttu-id="fc62f-124">Nome del carattere tipografico, ad esempio Courier o Arial.</span><span class="sxs-lookup"><span data-stu-id="fc62f-124">The name of the typeface (such as Courier or Arial).</span></span>

<a name="remarks"></a><span data-ttu-id="fc62f-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fc62f-125">Remarks</span></span>
-------

<span data-ttu-id="fc62f-126">Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="fc62f-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="fc62f-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fc62f-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="fc62f-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fc62f-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="fc62f-129">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="fc62f-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fc62f-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fc62f-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="fc62f-131">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="fc62f-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fc62f-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fc62f-132">Header</span></span></p></td>
<td><span data-ttu-id="fc62f-133">Wincon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fc62f-133">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="fc62f-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fc62f-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="fc62f-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="fc62f-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)

 

 




