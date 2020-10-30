---
title: Struttura CONSOLE_FONT_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFOEX, che contiene informazioni estese per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039259"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="e998a-104">\_Struttura INFOEX del tipo di carattere della console \_</span><span class="sxs-lookup"><span data-stu-id="e998a-104">CONSOLE\_FONT\_INFOEX structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e998a-105">Contiene informazioni estese per un tipo di carattere della console.</span><span class="sxs-lookup"><span data-stu-id="e998a-105">Contains extended information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="e998a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e998a-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a><span data-ttu-id="e998a-107">Members</span><span class="sxs-lookup"><span data-stu-id="e998a-107">Members</span></span>

<span data-ttu-id="e998a-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="e998a-108">**cbSize**</span></span>  
<span data-ttu-id="e998a-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="e998a-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="e998a-110">Questo membro deve essere impostato su `sizeof(CONSOLE_FONT_INFOEX)` prima di chiamare [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="e998a-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="e998a-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="e998a-111">**nFont**</span></span>  
<span data-ttu-id="e998a-112">Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.</span><span class="sxs-lookup"><span data-stu-id="e998a-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="e998a-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="e998a-113">**dwFontSize**</span></span>  
<span data-ttu-id="e998a-114">Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="e998a-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="e998a-115">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="e998a-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="e998a-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="e998a-116">**FontFamily**</span></span>  
<span data-ttu-id="e998a-117">Il passo del carattere e la famiglia.</span><span class="sxs-lookup"><span data-stu-id="e998a-117">The font pitch and family.</span></span> <span data-ttu-id="e998a-118">Per informazioni sui valori possibili per questo membro, vedere la descrizione del membro **tmPitchAndFamily** della struttura [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .</span><span class="sxs-lookup"><span data-stu-id="e998a-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="e998a-119">**SpessoreCarattere**</span><span class="sxs-lookup"><span data-stu-id="e998a-119">**FontWeight**</span></span>  
<span data-ttu-id="e998a-120">Spessore del carattere.</span><span class="sxs-lookup"><span data-stu-id="e998a-120">The font weight.</span></span> <span data-ttu-id="e998a-121">Il peso può variare da 100 a 1000, in multipli di 100.</span><span class="sxs-lookup"><span data-stu-id="e998a-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="e998a-122">Ad esempio, il peso normale è 400, mentre 700 è in grassetto.</span><span class="sxs-lookup"><span data-stu-id="e998a-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="e998a-123">**Contemplato**</span><span class="sxs-lookup"><span data-stu-id="e998a-123">**FaceName**</span></span>  
<span data-ttu-id="e998a-124">Nome del carattere tipografico, ad esempio Courier o Arial.</span><span class="sxs-lookup"><span data-stu-id="e998a-124">The name of the typeface (such as Courier or Arial).</span></span>

## <a name="remarks"></a><span data-ttu-id="e998a-125">Commenti</span><span class="sxs-lookup"><span data-stu-id="e998a-125">Remarks</span></span>

<span data-ttu-id="e998a-126">Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="e998a-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e998a-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e998a-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e998a-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e998a-128">Minimum supported client</span></span> | <span data-ttu-id="e998a-129">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="e998a-129">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="e998a-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e998a-130">Minimum supported server</span></span> | <span data-ttu-id="e998a-131">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="e998a-131">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e998a-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e998a-132">Header</span></span> | <span data-ttu-id="e998a-133">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e998a-133">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e998a-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e998a-134">See also</span></span>

[<span data-ttu-id="e998a-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="e998a-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)
