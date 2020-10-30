---
title: Struttura CONSOLE_SCREEN_BUFFER_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SCREEN_BUFFER_INFOEX, che contiene informazioni estese su un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: baf6eeb51cbae5ce410c190852c22ae237e6a367
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038349"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="fb73d-104">\_ \_ Struttura INFOEX buffer dello schermo della console \_</span><span class="sxs-lookup"><span data-stu-id="fb73d-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="fb73d-105">Contiene informazioni estese su un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="fb73d-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb73d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fb73d-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a><span data-ttu-id="fb73d-107">Members</span><span class="sxs-lookup"><span data-stu-id="fb73d-107">Members</span></span>

<span data-ttu-id="fb73d-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="fb73d-108">**cbSize**</span></span>  
<span data-ttu-id="fb73d-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="fb73d-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="fb73d-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="fb73d-110">**dwSize**</span></span>  
<span data-ttu-id="fb73d-111">Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne di tipo carattere e righe.</span><span class="sxs-lookup"><span data-stu-id="fb73d-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="fb73d-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="fb73d-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="fb73d-113">Struttura [**Coord**](coord-str.md) che contiene le coordinate di riga e di colonna del cursore nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="fb73d-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="fb73d-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="fb73d-114">**wAttributes**</span></span>  
<span data-ttu-id="fb73d-115">Attributi dei caratteri scritti in un buffer dello schermo dalle funzioni [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) e [**WriteConsole**](writeconsole.md) oppure restituiti a un buffer dello schermo dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="fb73d-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="fb73d-116">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="fb73d-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="fb73d-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="fb73d-117">**srWindow**</span></span>  
<span data-ttu-id="fb73d-118">Una [**piccola struttura \_ Rect**](small-rect-str.md) che contiene le coordinate del buffer dello schermo della console degli angoli superiore sinistro e inferiore destro della finestra di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="fb73d-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="fb73d-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="fb73d-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="fb73d-120">Struttura [**Coord**](coord-str.md) che contiene la dimensione massima della finestra della console, in colonne di tipo carattere e righe, date le dimensioni correnti del buffer dello schermo e il tipo di carattere e le dimensioni dello schermo.</span><span class="sxs-lookup"><span data-stu-id="fb73d-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="fb73d-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="fb73d-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="fb73d-122">Attributo Fill per i popup della console.</span><span class="sxs-lookup"><span data-stu-id="fb73d-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="fb73d-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="fb73d-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="fb73d-124">Se questo membro è `TRUE` , la modalità schermo intero è supportata; in caso contrario, non lo è.</span><span class="sxs-lookup"><span data-stu-id="fb73d-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="fb73d-125">Questa operazione sarà sempre `FALSE` destinata ai sistemi dopo Windows Vista con il [modello di driver WDDM](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , perché l'accesso diretto a VGA diretto al monitor non è più disponibile.</span><span class="sxs-lookup"><span data-stu-id="fb73d-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="fb73d-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="fb73d-126">**ColorTable**</span></span>  
<span data-ttu-id="fb73d-127">Matrice di valori [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) che descrivono le impostazioni relative ai colori della console.</span><span class="sxs-lookup"><span data-stu-id="fb73d-127">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb73d-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fb73d-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fb73d-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fb73d-129">Minimum supported client</span></span> | <span data-ttu-id="fb73d-130">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="fb73d-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="fb73d-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fb73d-131">Minimum supported server</span></span> | <span data-ttu-id="fb73d-132">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="fb73d-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="fb73d-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fb73d-133">Header</span></span> | <span data-ttu-id="fb73d-134">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fb73d-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fb73d-135">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fb73d-135">See also</span></span>

[<span data-ttu-id="fb73d-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="fb73d-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="fb73d-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="fb73d-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="fb73d-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="fb73d-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="fb73d-139">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="fb73d-139">**SMALL\_RECT**</span></span>](small-rect-str.md)
