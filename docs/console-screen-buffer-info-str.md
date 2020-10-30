---
title: Struttura CONSOLE_SCREEN_BUFFER_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SCREEN_BUFFER_INFO, che contiene informazioni su un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039179"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="a1983-104">\_Struttura delle \_ informazioni sul buffer dello schermo della console \_</span><span class="sxs-lookup"><span data-stu-id="a1983-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="a1983-105">Contiene informazioni su un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="a1983-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1983-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a1983-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="a1983-107">Members</span><span class="sxs-lookup"><span data-stu-id="a1983-107">Members</span></span>

<span data-ttu-id="a1983-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="a1983-108">**dwSize**</span></span>  
<span data-ttu-id="a1983-109">Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne di tipo carattere e righe.</span><span class="sxs-lookup"><span data-stu-id="a1983-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="a1983-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="a1983-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="a1983-111">Struttura [**Coord**](coord-str.md) che contiene le coordinate di riga e di colonna del cursore nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="a1983-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="a1983-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="a1983-112">**wAttributes**</span></span>  
<span data-ttu-id="a1983-113">Attributi dei caratteri scritti in un buffer dello schermo dalle funzioni [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) e [**WriteConsole**](writeconsole.md) oppure restituiti a un buffer dello schermo dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="a1983-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="a1983-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="a1983-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="a1983-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="a1983-115">**srWindow**</span></span>  
<span data-ttu-id="a1983-116">Una [**piccola struttura \_ Rect**](small-rect-str.md) che contiene le coordinate del buffer dello schermo della console degli angoli superiore sinistro e inferiore destro della finestra di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a1983-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="a1983-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="a1983-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="a1983-118">Struttura [**Coord**](coord-str.md) che contiene la dimensione massima della finestra della console, in colonne di tipo carattere e righe, date le dimensioni correnti del buffer dello schermo e il tipo di carattere e le dimensioni dello schermo.</span><span class="sxs-lookup"><span data-stu-id="a1983-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="a1983-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="a1983-119">Examples</span></span>

<span data-ttu-id="a1983-120">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="a1983-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="a1983-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a1983-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="a1983-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a1983-122">Minimum supported client</span></span> | <span data-ttu-id="a1983-123">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="a1983-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="a1983-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a1983-124">Minimum supported server</span></span> | <span data-ttu-id="a1983-125">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="a1983-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="a1983-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="a1983-126">Header</span></span> | <span data-ttu-id="a1983-127">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a1983-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="a1983-128">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a1983-128">See also</span></span>

[<span data-ttu-id="a1983-129">**COORD**</span><span class="sxs-lookup"><span data-stu-id="a1983-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="a1983-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="a1983-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="a1983-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="a1983-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="a1983-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="a1983-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="a1983-133">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="a1983-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="a1983-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="a1983-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="a1983-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="a1983-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
