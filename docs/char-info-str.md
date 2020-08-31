---
title: Struttura CHAR_INFO
description: Specifica un carattere Unicode o ANSI e i relativi attributi. Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060209"
---
# <a name="char_info-structure"></a><span data-ttu-id="c4fae-105">\_Struttura info char</span><span class="sxs-lookup"><span data-stu-id="c4fae-105">CHAR\_INFO structure</span></span>


<span data-ttu-id="c4fae-106">Specifica un carattere Unicode o ANSI e i relativi attributi.</span><span class="sxs-lookup"><span data-stu-id="c4fae-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="c4fae-107">Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c4fae-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="c4fae-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c4fae-108">Syntax</span></span>
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a><span data-ttu-id="c4fae-109">Membri</span><span class="sxs-lookup"><span data-stu-id="c4fae-109">Members</span></span>
-------

<span data-ttu-id="c4fae-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="c4fae-110">**Char**</span></span>  
<span data-ttu-id="c4fae-111">Unione dei membri seguenti.</span><span class="sxs-lookup"><span data-stu-id="c4fae-111">A union of the following members.</span></span>

<span data-ttu-id="c4fae-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="c4fae-112">**UnicodeChar**</span></span>  
<span data-ttu-id="c4fae-113">Carattere Unicode di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="c4fae-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="c4fae-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="c4fae-114">**AsciiChar**</span></span>  
<span data-ttu-id="c4fae-115">Carattere ANSI di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="c4fae-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="c4fae-116">**Attributes (Attributi)**</span><span class="sxs-lookup"><span data-stu-id="c4fae-116">**Attributes**</span></span>  
<span data-ttu-id="c4fae-117">Attributi carattere.</span><span class="sxs-lookup"><span data-stu-id="c4fae-117">The character attributes.</span></span> <span data-ttu-id="c4fae-118">Questo membro può essere zero o una qualsiasi combinazione dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="c4fae-118">This member can be zero or any combination of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="c4fae-119">valore</span><span class="sxs-lookup"><span data-stu-id="c4fae-119">Value</span></span></th>
<th><span data-ttu-id="c4fae-120">Significato</span><span class="sxs-lookup"><span data-stu-id="c4fae-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="c4fae-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="c4fae-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="c4fae-122">Il colore del testo contiene il blu.</span><span class="sxs-lookup"><span data-stu-id="c4fae-122">Text color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="c4fae-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="c4fae-124">Il colore del testo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="c4fae-124">Text color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="c4fae-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="c4fae-126">Il colore del testo contiene rosso.</span><span class="sxs-lookup"><span data-stu-id="c4fae-126">Text color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="c4fae-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="c4fae-128">Il colore del testo viene intensificato.</span><span class="sxs-lookup"><span data-stu-id="c4fae-128">Text color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="c4fae-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="c4fae-130">Il colore di sfondo contiene blu.</span><span class="sxs-lookup"><span data-stu-id="c4fae-130">Background color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="c4fae-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="c4fae-132">Il colore di sfondo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="c4fae-132">Background color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="c4fae-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="c4fae-134">Il colore di sfondo contiene rosso.</span><span class="sxs-lookup"><span data-stu-id="c4fae-134">Background color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="c4fae-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="c4fae-136">Il colore di sfondo viene intensificato.</span><span class="sxs-lookup"><span data-stu-id="c4fae-136">Background color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="c4fae-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="c4fae-138">Byte iniziali.</span><span class="sxs-lookup"><span data-stu-id="c4fae-138">Leading byte.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="c4fae-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="c4fae-140">Byte finale.</span><span class="sxs-lookup"><span data-stu-id="c4fae-140">Trailing byte.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span><span class="sxs-lookup"><span data-stu-id="c4fae-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span></span></td>
<td><p><span data-ttu-id="c4fae-142">Orizzontale superiore</span><span class="sxs-lookup"><span data-stu-id="c4fae-142">Top horizontal</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span><span class="sxs-lookup"><span data-stu-id="c4fae-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span></span></td>
<td><p><span data-ttu-id="c4fae-144">Sinistra verticale.</span><span class="sxs-lookup"><span data-stu-id="c4fae-144">Left vertical.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span><span class="sxs-lookup"><span data-stu-id="c4fae-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span></span></td>
<td><p><span data-ttu-id="c4fae-146">Diritto verticale.</span><span class="sxs-lookup"><span data-stu-id="c4fae-146">Right vertical.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="c4fae-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span><span class="sxs-lookup"><span data-stu-id="c4fae-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span></span></td>
<td><p><span data-ttu-id="c4fae-148">Inverso in primo piano e in background.</span><span class="sxs-lookup"><span data-stu-id="c4fae-148">Reverse foreground and background attribute.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="c4fae-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span><span class="sxs-lookup"><span data-stu-id="c4fae-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span></span></td>
<td><p><span data-ttu-id="c4fae-150">Sottolineatura.</span><span class="sxs-lookup"><span data-stu-id="c4fae-150">Underscore.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="examples"></a><span data-ttu-id="c4fae-151">Esempi</span><span class="sxs-lookup"><span data-stu-id="c4fae-151">Examples</span></span>
--------

<span data-ttu-id="c4fae-152">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="c4fae-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="c4fae-153">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c4fae-153">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c4fae-154">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c4fae-154">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c4fae-155">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="c4fae-155">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c4fae-156">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c4fae-156">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c4fae-157">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="c4fae-157">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c4fae-158">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c4fae-158">Header</span></span></p></td>
<td><span data-ttu-id="c4fae-159">Wincon. h (include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c4fae-159">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c4fae-160"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c4fae-160"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c4fae-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c4fae-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="c4fae-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="c4fae-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="c4fae-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="c4fae-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

 

 




