---
title: Struttura CONSOLE_SCREEN_BUFFER_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SCREEN_BUFFER_INFOEX, che contiene informazioni estese su un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060049"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="42de8-104">\_ \_ Struttura INFOEX buffer dello schermo della console \_</span><span class="sxs-lookup"><span data-stu-id="42de8-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>


<span data-ttu-id="42de8-105">Contiene informazioni estese su un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="42de8-105">Contains extended information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="42de8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="42de8-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a><span data-ttu-id="42de8-107">Membri</span><span class="sxs-lookup"><span data-stu-id="42de8-107">Members</span></span>
-------

<span data-ttu-id="42de8-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="42de8-108">**cbSize**</span></span>  
<span data-ttu-id="42de8-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="42de8-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="42de8-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="42de8-110">**dwSize**</span></span>  
<span data-ttu-id="42de8-111">Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne di tipo carattere e righe.</span><span class="sxs-lookup"><span data-stu-id="42de8-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="42de8-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="42de8-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="42de8-113">Struttura [**Coord**](coord-str.md) che contiene le coordinate di riga e di colonna del cursore nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="42de8-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="42de8-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="42de8-114">**wAttributes**</span></span>  
<span data-ttu-id="42de8-115">Attributi dei caratteri scritti in un buffer dello schermo dalle funzioni [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) e [**WriteConsole**](writeconsole.md) oppure restituiti a un buffer dello schermo dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="42de8-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="42de8-116">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="42de8-116">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="42de8-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="42de8-117">**srWindow**</span></span>  
<span data-ttu-id="42de8-118">Una [**piccola struttura \_ Rect**](small-rect-str.md) che contiene le coordinate del buffer dello schermo della console degli angoli superiore sinistro e inferiore destro della finestra di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="42de8-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="42de8-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="42de8-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="42de8-120">Struttura [**Coord**](coord-str.md) che contiene la dimensione massima della finestra della console, in colonne di tipo carattere e righe, date le dimensioni correnti del buffer dello schermo e il tipo di carattere e le dimensioni dello schermo.</span><span class="sxs-lookup"><span data-stu-id="42de8-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="42de8-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="42de8-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="42de8-122">Attributo Fill per i popup della console.</span><span class="sxs-lookup"><span data-stu-id="42de8-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="42de8-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="42de8-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="42de8-124">Se questo membro è TRUE, la modalità schermo intero è supportata. in caso contrario, non lo è.</span><span class="sxs-lookup"><span data-stu-id="42de8-124">If this member is TRUE, full-screen mode is supported; otherwise, it is not.</span></span>

<span data-ttu-id="42de8-125">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="42de8-125">**ColorTable**</span></span>  
<span data-ttu-id="42de8-126">Matrice di valori [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) che descrivono le impostazioni relative ai colori della console.</span><span class="sxs-lookup"><span data-stu-id="42de8-126">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

<a name="requirements"></a><span data-ttu-id="42de8-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="42de8-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="42de8-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="42de8-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="42de8-129">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="42de8-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="42de8-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="42de8-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="42de8-131">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="42de8-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="42de8-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="42de8-132">Header</span></span></p></td>
<td><span data-ttu-id="42de8-133">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="42de8-133">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="42de8-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="42de8-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="42de8-135">**COORD**</span><span class="sxs-lookup"><span data-stu-id="42de8-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="42de8-136">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="42de8-136">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="42de8-137">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="42de8-137">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="42de8-138">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="42de8-138">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




