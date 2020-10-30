---
title: Struttura CONSOLE_FONT_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFO, che contiene l'indice e le dimensioni per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037139"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="420a9-104">Struttura delle informazioni sul tipo di carattere della CONSOLE \_ \_</span><span class="sxs-lookup"><span data-stu-id="420a9-104">CONSOLE\_FONT\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="420a9-105">Contiene informazioni per un tipo di carattere della console.</span><span class="sxs-lookup"><span data-stu-id="420a9-105">Contains information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="420a9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="420a9-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a><span data-ttu-id="420a9-107">Members</span><span class="sxs-lookup"><span data-stu-id="420a9-107">Members</span></span>

<span data-ttu-id="420a9-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="420a9-108">**nFont**</span></span>  
<span data-ttu-id="420a9-109">Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.</span><span class="sxs-lookup"><span data-stu-id="420a9-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="420a9-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="420a9-110">**dwFontSize**</span></span>  
<span data-ttu-id="420a9-111">Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="420a9-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="420a9-112">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="420a9-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

## <a name="remarks"></a><span data-ttu-id="420a9-113">Commenti</span><span class="sxs-lookup"><span data-stu-id="420a9-113">Remarks</span></span>

<span data-ttu-id="420a9-114">Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .</span><span class="sxs-lookup"><span data-stu-id="420a9-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="420a9-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="420a9-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="420a9-116">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="420a9-116">Minimum supported client</span></span> | <span data-ttu-id="420a9-117">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="420a9-117">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="420a9-118">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="420a9-118">Minimum supported server</span></span> | <span data-ttu-id="420a9-119">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="420a9-119">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="420a9-120">Intestazione</span><span class="sxs-lookup"><span data-stu-id="420a9-120">Header</span></span> | <span data-ttu-id="420a9-121">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="420a9-121">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="420a9-122">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="420a9-122">See also</span></span>

[<span data-ttu-id="420a9-123">**COORD**</span><span class="sxs-lookup"><span data-stu-id="420a9-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="420a9-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="420a9-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)
