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
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357851"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="a7c9e-105">Specifica un carattere Unicode o ANSI e i relativi attributi.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-105">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="a7c9e-106">Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-106">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7c9e-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a7c9e-107">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="a7c9e-108">Members</span><span class="sxs-lookup"><span data-stu-id="a7c9e-108">Members</span></span>

<span data-ttu-id="a7c9e-109">**Char**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-109">**Char**</span></span>  
<span data-ttu-id="a7c9e-110">Unione dei membri seguenti.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-110">A union of the following members.</span></span>

<span data-ttu-id="a7c9e-111">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-111">**UnicodeChar**</span></span>  
<span data-ttu-id="a7c9e-112">Carattere Unicode di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-112">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="a7c9e-113">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-113">**AsciiChar**</span></span>  
<span data-ttu-id="a7c9e-114">Carattere ANSI di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-114">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="a7c9e-115">**Attributes (Attributi)**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-115">**Attributes**</span></span>  
<span data-ttu-id="a7c9e-116">Attributi carattere.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-116">The character attributes.</span></span> <span data-ttu-id="a7c9e-117">Questo membro può essere zero o una qualsiasi combinazione dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-117">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="a7c9e-118">Valore</span><span class="sxs-lookup"><span data-stu-id="a7c9e-118">Value</span></span> | <span data-ttu-id="a7c9e-119">Significato</span><span class="sxs-lookup"><span data-stu-id="a7c9e-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="a7c9e-120">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-120">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="a7c9e-121">Il colore del testo contiene il blu.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-121">Text color contains blue.</span></span> |
| <span data-ttu-id="a7c9e-122">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-122">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="a7c9e-123">Il colore del testo contiene il verde.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-123">Text color contains green.</span></span> |
| <span data-ttu-id="a7c9e-124">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-124">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="a7c9e-125">Il colore del testo contiene il rosso.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-125">Text color contains red.</span></span> |
| <span data-ttu-id="a7c9e-126">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-126">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="a7c9e-127">Il colore del testo è accentuato.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-127">Text color is intensified.</span></span> |
| <span data-ttu-id="a7c9e-128">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-128">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="a7c9e-129">Il colore di sfondo contiene il blu.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-129">Background color contains blue.</span></span> |
| <span data-ttu-id="a7c9e-130">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-130">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="a7c9e-131">Il colore di sfondo contiene il verde.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-131">Background color contains green.</span></span> |
| <span data-ttu-id="a7c9e-132">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-132">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="a7c9e-133">Il colore di sfondo contiene il rosso.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-133">Background color contains red.</span></span> |
| <span data-ttu-id="a7c9e-134">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-134">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="a7c9e-135">Il colore di sfondo è accentuato.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-135">Background color is intensified.</span></span> |
| <span data-ttu-id="a7c9e-136">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-136">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="a7c9e-137">Byte iniziale.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-137">Leading byte.</span></span> |
| <span data-ttu-id="a7c9e-138">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-138">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="a7c9e-139">Byte finale.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-139">Trailing byte.</span></span> |
| <span data-ttu-id="a7c9e-140">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-140">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="a7c9e-141">Orizzontale superiore.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-141">Top horizontal.</span></span> |
| <span data-ttu-id="a7c9e-142">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-142">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="a7c9e-143">Verticale sinistro.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-143">Left vertical.</span></span> |
| <span data-ttu-id="a7c9e-144">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-144">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="a7c9e-145">Verticale destro.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-145">Right vertical.</span></span> |
| <span data-ttu-id="a7c9e-146">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-146">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="a7c9e-147">Inverso in primo piano e in background.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-147">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="a7c9e-148">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="a7c9e-148">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="a7c9e-149">Sottolineatura.</span><span class="sxs-lookup"><span data-stu-id="a7c9e-149">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="a7c9e-150">Esempio</span><span class="sxs-lookup"><span data-stu-id="a7c9e-150">Examples</span></span>

<span data-ttu-id="a7c9e-151">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="a7c9e-151">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="a7c9e-152">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a7c9e-152">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="a7c9e-153">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a7c9e-153">Minimum supported client</span></span> | <span data-ttu-id="a7c9e-154">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="a7c9e-154">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="a7c9e-155">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a7c9e-155">Minimum supported server</span></span> | <span data-ttu-id="a7c9e-156">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="a7c9e-156">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="a7c9e-157">Intestazione</span><span class="sxs-lookup"><span data-stu-id="a7c9e-157">Header</span></span> | <span data-ttu-id="a7c9e-158">WinCon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a7c9e-158">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="a7c9e-159">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a7c9e-159">See also</span></span>

[<span data-ttu-id="a7c9e-160">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-160">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="a7c9e-161">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-161">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="a7c9e-162">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="a7c9e-162">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
