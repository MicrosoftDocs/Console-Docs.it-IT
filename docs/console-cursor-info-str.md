---
title: Struttura CONSOLE_CURSOR_INFO
description: Contiene le informazioni sulle dimensioni e sulla visibilità relative al cursore della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037014"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="1d7c9-104">\_ \_ Struttura informazioni cursore console</span><span class="sxs-lookup"><span data-stu-id="1d7c9-104">CONSOLE\_CURSOR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1d7c9-105">Contiene informazioni sul cursore della console.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-105">Contains information about the console cursor.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d7c9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1d7c9-106">Syntax</span></span>

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a><span data-ttu-id="1d7c9-107">Members</span><span class="sxs-lookup"><span data-stu-id="1d7c9-107">Members</span></span>

<span data-ttu-id="1d7c9-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="1d7c9-108">**dwSize**</span></span>  
<span data-ttu-id="1d7c9-109">Percentuale della cella di tipo carattere compilata dal cursore.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="1d7c9-110">Questo valore è compreso tra 1 e 100.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-110">This value is between 1 and 100.</span></span> <span data-ttu-id="1d7c9-111">L'aspetto del cursore varia a seconda che la cella venga riempita completamente per essere visualizzata come riga orizzontale nella parte inferiore della cella.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

> [!NOTE]
><span data-ttu-id="1d7c9-112">Anche se il valore **dwSize** è in genere compreso tra 1 e 100, in alcune circostanze potrebbe essere restituito un valore esterno a tale intervallo.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-112">While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="1d7c9-113">Se, ad esempio, **CursorSize** è impostato su 0 nel registro di sistema, il valore **dwSize** restituito sarà 0.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 <span data-ttu-id="1d7c9-114">**bVisible**</span><span class="sxs-lookup"><span data-stu-id="1d7c9-114">**bVisible**</span></span>  
<span data-ttu-id="1d7c9-115">Visibilità del cursore.</span><span class="sxs-lookup"><span data-stu-id="1d7c9-115">The visibility of the cursor.</span></span> <span data-ttu-id="1d7c9-116">Se il cursore è visibile, questo membro è **true** .</span><span class="sxs-lookup"><span data-stu-id="1d7c9-116">If the cursor is visible, this member is **TRUE** .</span></span>

## <a name="requirements"></a><span data-ttu-id="1d7c9-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1d7c9-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1d7c9-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1d7c9-118">Minimum supported client</span></span> | <span data-ttu-id="1d7c9-119">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="1d7c9-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1d7c9-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1d7c9-120">Minimum supported server</span></span> | <span data-ttu-id="1d7c9-121">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="1d7c9-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1d7c9-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="1d7c9-122">Header</span></span> | <span data-ttu-id="1d7c9-123">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1d7c9-123">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1d7c9-124">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1d7c9-124">See also</span></span>

[<span data-ttu-id="1d7c9-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="1d7c9-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="1d7c9-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="1d7c9-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
