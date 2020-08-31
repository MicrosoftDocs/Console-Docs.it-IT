---
title: Struttura MOUSE_EVENT_RECORD
description: Vedere informazioni di riferimento sulla struttura MOUSE_EVENT_RECORD, che descrive un evento di input del mouse in una struttura di INPUT_RECORD della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059585"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="e8221-104">Struttura del record dell' \_ evento del mouse \_</span><span class="sxs-lookup"><span data-stu-id="e8221-104">MOUSE\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="e8221-105">Descrive un evento di input del mouse in una struttura di [\*\* \_ record di input\*\*](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="e8221-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

<a name="syntax"></a><span data-ttu-id="e8221-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8221-106">Syntax</span></span>
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="e8221-107">Membri</span><span class="sxs-lookup"><span data-stu-id="e8221-107">Members</span></span>
-------

<span data-ttu-id="e8221-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="e8221-108">**dwMousePosition**</span></span>  
<span data-ttu-id="e8221-109">Struttura [**Coord**](coord-str.md) che contiene la posizione del cursore, in termini di coordinate delle celle dei caratteri del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="e8221-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="e8221-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="e8221-110">**dwButtonState**</span></span>  
<span data-ttu-id="e8221-111">Stato dei pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-111">The status of the mouse buttons.</span></span> <span data-ttu-id="e8221-112">Il bit meno significativo corrisponde al pulsante del mouse più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="e8221-113">Il bit meno significativo successivo corrisponde al pulsante del mouse più a destra.</span><span class="sxs-lookup"><span data-stu-id="e8221-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="e8221-114">Il bit successivo indica il pulsante del mouse successivo a quello più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="e8221-115">I bit corrispondono quindi da sinistra a destra ai pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="e8221-116">Un bit è 1 se è stato premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="e8221-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="e8221-117">Le costanti seguenti sono definite per i primi cinque pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-117">The following constants are defined for the first five mouse buttons.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e8221-118">valore</span><span class="sxs-lookup"><span data-stu-id="e8221-118">Value</span></span></th>
<th><span data-ttu-id="e8221-119">Significato</span><span class="sxs-lookup"><span data-stu-id="e8221-119">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e8221-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e8221-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e8221-121">Pulsante del mouse più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-121">The leftmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e8221-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e8221-123">Secondo pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-123">The second button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e8221-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e8221-125">Terzo pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-125">The third button from the left.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="e8221-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="e8221-127">Quarto pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-127">The fourth button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e8221-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e8221-129">Pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-129">The rightmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="e8221-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="e8221-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="e8221-131">Stato delle chiavi del controllo.</span><span class="sxs-lookup"><span data-stu-id="e8221-131">The state of the control keys.</span></span> <span data-ttu-id="e8221-132">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="e8221-132">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e8221-133">valore</span><span class="sxs-lookup"><span data-stu-id="e8221-133">Value</span></span></th>
<th><span data-ttu-id="e8221-134">Significato</span><span class="sxs-lookup"><span data-stu-id="e8221-134">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e8221-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="e8221-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="e8221-136">La luce del blocco è attiva.</span><span class="sxs-lookup"><span data-stu-id="e8221-136">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="e8221-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="e8221-138">La chiave è stata migliorata.</span><span class="sxs-lookup"><span data-stu-id="e8221-138">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e8221-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e8221-140">Viene premuto il tasto ALT sinistro.</span><span class="sxs-lookup"><span data-stu-id="e8221-140">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e8221-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e8221-142">Viene premuto il tasto CTRL sinistro.</span><span class="sxs-lookup"><span data-stu-id="e8221-142">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="e8221-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="e8221-144">Il BLOC NUM Light è on.</span><span class="sxs-lookup"><span data-stu-id="e8221-144">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e8221-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e8221-146">Viene premuto il tasto ALT destro.</span><span class="sxs-lookup"><span data-stu-id="e8221-146">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e8221-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e8221-148">Viene premuto il tasto CTRL destro.</span><span class="sxs-lookup"><span data-stu-id="e8221-148">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="e8221-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="e8221-150">La luce del blocco di scorrimento è attiva.</span><span class="sxs-lookup"><span data-stu-id="e8221-150">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="e8221-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="e8221-152">Il tasto MAIUSC è premuto.</span><span class="sxs-lookup"><span data-stu-id="e8221-152">The SHIFT key is pressed.</span></span></p></td>
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

 

<span data-ttu-id="e8221-153">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="e8221-153">**dwEventFlags**</span></span>  
<span data-ttu-id="e8221-154">Tipo di evento del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-154">The type of mouse event.</span></span> <span data-ttu-id="e8221-155">Se questo valore è zero, indica che un pulsante del mouse viene premuto o rilasciato.</span><span class="sxs-lookup"><span data-stu-id="e8221-155">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="e8221-156">In caso contrario, questo membro è uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="e8221-156">Otherwise, this member is one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e8221-157">valore</span><span class="sxs-lookup"><span data-stu-id="e8221-157">Value</span></span></th>
<th><span data-ttu-id="e8221-158">Significato</span><span class="sxs-lookup"><span data-stu-id="e8221-158">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e8221-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e8221-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e8221-160">Si è verificato il secondo clic (premere il pulsante) di un doppio clic.</span><span class="sxs-lookup"><span data-stu-id="e8221-160">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="e8221-161">Il primo clic viene restituito come evento normale di pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="e8221-161">The first click is returned as a regular button-press event.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e8221-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e8221-163">La rotellina del mouse orizzontale è stata spostata.</span><span class="sxs-lookup"><span data-stu-id="e8221-163">The horizontal mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="e8221-164">Se la parola alta del membro <strong>dwButtonState</strong> contiene un valore positivo, la rotellina è stata ruotata a destra.</span><span class="sxs-lookup"><span data-stu-id="e8221-164">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="e8221-165">In caso contrario, la rotellina è stata ruotata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="e8221-165">Otherwise, the wheel was rotated to the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e8221-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>Mouse_Moved</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e8221-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e8221-167">È stata apportata una modifica alla posizione del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-167">A change in mouse position occurred.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e8221-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e8221-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e8221-169">La rotellina del mouse verticale è stata spostata.</span><span class="sxs-lookup"><span data-stu-id="e8221-169">The vertical mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="e8221-170">Se la parola alta del membro <strong>dwButtonState</strong> contiene un valore positivo, la rotellina è stata ruotata verso l'alto, lontano dall'utente.</span><span class="sxs-lookup"><span data-stu-id="e8221-170">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="e8221-171">In caso contrario, la rotellina è stata ruotata indietro verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="e8221-171">Otherwise, the wheel was rotated backward, toward the user.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a><span data-ttu-id="e8221-172">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e8221-172">Remarks</span></span>
-------

<span data-ttu-id="e8221-173">Gli eventi del mouse vengono inseriti nel buffer di input quando la console di è in modalità mouse (**Abilita \_ \_ input del mouse**).</span><span class="sxs-lookup"><span data-stu-id="e8221-173">Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).</span></span>

<span data-ttu-id="e8221-174">Gli eventi del mouse vengono generati ogni volta che l'utente sposta il mouse oppure preme o rilascia uno dei pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="e8221-174">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="e8221-175">Gli eventi del mouse vengono inseriti nel buffer di input di una console solo quando il gruppo di console dispone dello stato attivo della tastiera e il cursore si trova all'interno dei bordi della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="e8221-175">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

<a name="examples"></a><span data-ttu-id="e8221-176">Esempi</span><span class="sxs-lookup"><span data-stu-id="e8221-176">Examples</span></span>
--------

<span data-ttu-id="e8221-177">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="e8221-177">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="e8221-178">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e8221-178">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e8221-179">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e8221-179">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e8221-180">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e8221-180">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e8221-181">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e8221-181">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e8221-182">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e8221-182">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e8221-183">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e8221-183">Header</span></span></p></td>
<td><span data-ttu-id="e8221-184">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e8221-184">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e8221-185"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8221-185"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e8221-186">**COORD**</span><span class="sxs-lookup"><span data-stu-id="e8221-186">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e8221-187">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="e8221-187">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="e8221-188">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e8221-188">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="e8221-189">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e8221-189">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e8221-190">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e8221-190">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




