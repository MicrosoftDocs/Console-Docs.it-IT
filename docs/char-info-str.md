---
title: Struttura CHAR_INFO
description: Specifica un carattere Unicode o ANSI e i relativi attributi. Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037379"
---
# <a name="char_info-structure"></a><span data-ttu-id="de450-105">\_Struttura info char</span><span class="sxs-lookup"><span data-stu-id="de450-105">CHAR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="de450-106">Specifica un carattere Unicode o ANSI e i relativi attributi.</span><span class="sxs-lookup"><span data-stu-id="de450-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="de450-107">Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="de450-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="de450-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="de450-108">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="de450-109">Members</span><span class="sxs-lookup"><span data-stu-id="de450-109">Members</span></span>

<span data-ttu-id="de450-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="de450-110">**Char**</span></span>  
<span data-ttu-id="de450-111">Unione dei membri seguenti.</span><span class="sxs-lookup"><span data-stu-id="de450-111">A union of the following members.</span></span>

<span data-ttu-id="de450-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="de450-112">**UnicodeChar**</span></span>  
<span data-ttu-id="de450-113">Carattere Unicode di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="de450-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="de450-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="de450-114">**AsciiChar**</span></span>  
<span data-ttu-id="de450-115">Carattere ANSI di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="de450-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="de450-116">**Attributes (Attributi)**</span><span class="sxs-lookup"><span data-stu-id="de450-116">**Attributes**</span></span>  
<span data-ttu-id="de450-117">Attributi carattere.</span><span class="sxs-lookup"><span data-stu-id="de450-117">The character attributes.</span></span> <span data-ttu-id="de450-118">Questo membro può essere zero o una qualsiasi combinazione dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="de450-118">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="de450-119">Valore</span><span class="sxs-lookup"><span data-stu-id="de450-119">Value</span></span> | <span data-ttu-id="de450-120">Significato</span><span class="sxs-lookup"><span data-stu-id="de450-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="de450-121">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="de450-121">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="de450-122">Il colore del testo contiene il blu.</span><span class="sxs-lookup"><span data-stu-id="de450-122">Text color contains blue.</span></span> |
| <span data-ttu-id="de450-123">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="de450-123">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="de450-124">Il colore del testo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="de450-124">Text color contains green.</span></span> |
| <span data-ttu-id="de450-125">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="de450-125">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="de450-126">Il colore del testo contiene rosso.</span><span class="sxs-lookup"><span data-stu-id="de450-126">Text color contains red.</span></span> |
| <span data-ttu-id="de450-127">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="de450-127">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="de450-128">Il colore del testo viene intensificato.</span><span class="sxs-lookup"><span data-stu-id="de450-128">Text color is intensified.</span></span> |
| <span data-ttu-id="de450-129">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="de450-129">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="de450-130">Il colore di sfondo contiene blu.</span><span class="sxs-lookup"><span data-stu-id="de450-130">Background color contains blue.</span></span> |
| <span data-ttu-id="de450-131">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="de450-131">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="de450-132">Il colore di sfondo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="de450-132">Background color contains green.</span></span> |
| <span data-ttu-id="de450-133">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="de450-133">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="de450-134">Il colore di sfondo contiene rosso.</span><span class="sxs-lookup"><span data-stu-id="de450-134">Background color contains red.</span></span> |
| <span data-ttu-id="de450-135">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="de450-135">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="de450-136">Il colore di sfondo viene intensificato.</span><span class="sxs-lookup"><span data-stu-id="de450-136">Background color is intensified.</span></span> |
| <span data-ttu-id="de450-137">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="de450-137">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="de450-138">Byte iniziali.</span><span class="sxs-lookup"><span data-stu-id="de450-138">Leading byte.</span></span> |
| <span data-ttu-id="de450-139">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="de450-139">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="de450-140">Byte finale.</span><span class="sxs-lookup"><span data-stu-id="de450-140">Trailing byte.</span></span> |
| <span data-ttu-id="de450-141">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="de450-141">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="de450-142">Orizzontale superiore.</span><span class="sxs-lookup"><span data-stu-id="de450-142">Top horizontal.</span></span> |
| <span data-ttu-id="de450-143">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="de450-143">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="de450-144">Sinistra verticale.</span><span class="sxs-lookup"><span data-stu-id="de450-144">Left vertical.</span></span> |
| <span data-ttu-id="de450-145">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="de450-145">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="de450-146">Diritto verticale.</span><span class="sxs-lookup"><span data-stu-id="de450-146">Right vertical.</span></span> |
| <span data-ttu-id="de450-147">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="de450-147">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="de450-148">Inverso in primo piano e in background.</span><span class="sxs-lookup"><span data-stu-id="de450-148">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="de450-149">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="de450-149">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="de450-150">Sottolineatura.</span><span class="sxs-lookup"><span data-stu-id="de450-150">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="de450-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="de450-151">Examples</span></span>

<span data-ttu-id="de450-152">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="de450-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="de450-153">Requisiti</span><span class="sxs-lookup"><span data-stu-id="de450-153">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="de450-154">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="de450-154">Minimum supported client</span></span> | <span data-ttu-id="de450-155">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="de450-155">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="de450-156">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="de450-156">Minimum supported server</span></span> | <span data-ttu-id="de450-157">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="de450-157">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="de450-158">Intestazione</span><span class="sxs-lookup"><span data-stu-id="de450-158">Header</span></span> | <span data-ttu-id="de450-159">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="de450-159">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="de450-160">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="de450-160">See also</span></span>

[<span data-ttu-id="de450-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="de450-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="de450-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="de450-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="de450-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="de450-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
