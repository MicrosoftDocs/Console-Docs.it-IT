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
ms.openlocfilehash: 3ab4424be99ba9eceda54db1ebf7c7e13560f722
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358151"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="aa29e-104">\_Struttura INFOEX del tipo di carattere della console \_</span><span class="sxs-lookup"><span data-stu-id="aa29e-104">CONSOLE\_FONT\_INFOEX structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="aa29e-105">Contiene informazioni estese per un tipo di carattere della console.</span><span class="sxs-lookup"><span data-stu-id="aa29e-105">Contains extended information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa29e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa29e-106">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="aa29e-107">Members</span><span class="sxs-lookup"><span data-stu-id="aa29e-107">Members</span></span>

<span data-ttu-id="aa29e-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="aa29e-108">**cbSize**</span></span>  
<span data-ttu-id="aa29e-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="aa29e-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="aa29e-110">Questo membro deve essere impostato su `sizeof(CONSOLE_FONT_INFOEX)` prima di chiamare [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="aa29e-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="aa29e-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="aa29e-111">**nFont**</span></span>  
<span data-ttu-id="aa29e-112">Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.</span><span class="sxs-lookup"><span data-stu-id="aa29e-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="aa29e-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="aa29e-113">**dwFontSize**</span></span>  
<span data-ttu-id="aa29e-114">Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="aa29e-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="aa29e-115">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="aa29e-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="aa29e-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="aa29e-116">**FontFamily**</span></span>  
<span data-ttu-id="aa29e-117">Il passo del carattere e la famiglia.</span><span class="sxs-lookup"><span data-stu-id="aa29e-117">The font pitch and family.</span></span> <span data-ttu-id="aa29e-118">Per informazioni sui valori possibili per questo membro, vedere la descrizione del membro **tmPitchAndFamily** della struttura [**TEXTMETRIC**](/windows/win32/api/wingdi/ns-wingdi-textmetrica) .</span><span class="sxs-lookup"><span data-stu-id="aa29e-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](/windows/win32/api/wingdi/ns-wingdi-textmetrica) structure.</span></span>

<span data-ttu-id="aa29e-119">**SpessoreCarattere**</span><span class="sxs-lookup"><span data-stu-id="aa29e-119">**FontWeight**</span></span>  
<span data-ttu-id="aa29e-120">Spessore del carattere.</span><span class="sxs-lookup"><span data-stu-id="aa29e-120">The font weight.</span></span> <span data-ttu-id="aa29e-121">Il peso può variare da 100 a 1000, in multipli di 100.</span><span class="sxs-lookup"><span data-stu-id="aa29e-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="aa29e-122">Ad esempio, il peso normale è 400, mentre 700 è in grassetto.</span><span class="sxs-lookup"><span data-stu-id="aa29e-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="aa29e-123">**Contemplato**</span><span class="sxs-lookup"><span data-stu-id="aa29e-123">**FaceName**</span></span>  
<span data-ttu-id="aa29e-124">Nome del carattere tipografico, ad esempio Courier o Arial.</span><span class="sxs-lookup"><span data-stu-id="aa29e-124">The name of the typeface (such as Courier or Arial).</span></span>

## <a name="remarks"></a><span data-ttu-id="aa29e-125">Commenti</span><span class="sxs-lookup"><span data-stu-id="aa29e-125">Remarks</span></span>

<span data-ttu-id="aa29e-126">Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="aa29e-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa29e-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aa29e-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="aa29e-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa29e-128">Minimum supported client</span></span> | <span data-ttu-id="aa29e-129">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="aa29e-129">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa29e-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa29e-130">Minimum supported server</span></span> | <span data-ttu-id="aa29e-131">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="aa29e-131">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa29e-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="aa29e-132">Header</span></span> | <span data-ttu-id="aa29e-133">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="aa29e-133">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="aa29e-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="aa29e-134">See also</span></span>

[<span data-ttu-id="aa29e-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="aa29e-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)