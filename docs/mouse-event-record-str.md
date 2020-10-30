---
title: Struttura MOUSE_EVENT_RECORD
description: Vedere informazioni di riferimento sulla struttura MOUSE_EVENT_RECORD, che descrive un evento di input del mouse in una struttura di INPUT_RECORD della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038519"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="58b09-104">Struttura del record dell' \_ evento del mouse \_</span><span class="sxs-lookup"><span data-stu-id="58b09-104">MOUSE\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="58b09-105">Descrive un evento di input del mouse in una struttura di [**\_ record di input**](input-record-str.md) della console.</span><span class="sxs-lookup"><span data-stu-id="58b09-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="58b09-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="58b09-106">Syntax</span></span>

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="58b09-107">Members</span><span class="sxs-lookup"><span data-stu-id="58b09-107">Members</span></span>

<span data-ttu-id="58b09-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="58b09-108">**dwMousePosition**</span></span>  
<span data-ttu-id="58b09-109">Struttura [**Coord**](coord-str.md) che contiene la posizione del cursore, in termini di coordinate delle celle dei caratteri del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="58b09-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="58b09-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="58b09-110">**dwButtonState**</span></span>  
<span data-ttu-id="58b09-111">Stato dei pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-111">The status of the mouse buttons.</span></span> <span data-ttu-id="58b09-112">Il bit meno significativo corrisponde al pulsante del mouse più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="58b09-113">Il bit meno significativo successivo corrisponde al pulsante del mouse più a destra.</span><span class="sxs-lookup"><span data-stu-id="58b09-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="58b09-114">Il bit successivo indica il pulsante del mouse successivo a quello più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="58b09-115">I bit corrispondono quindi da sinistra a destra ai pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="58b09-116">Un bit è 1 se è stato premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="58b09-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="58b09-117">Le costanti seguenti sono definite per i primi cinque pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-117">The following constants are defined for the first five mouse buttons.</span></span>

| <span data-ttu-id="58b09-118">Valore</span><span class="sxs-lookup"><span data-stu-id="58b09-118">Value</span></span> | <span data-ttu-id="58b09-119">Significato</span><span class="sxs-lookup"><span data-stu-id="58b09-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="58b09-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="58b09-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span></span> | <span data-ttu-id="58b09-121">Pulsante del mouse più a sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-121">The leftmost mouse button.</span></span> |
| <span data-ttu-id="58b09-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="58b09-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span></span> | <span data-ttu-id="58b09-123">Secondo pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-123">The second button fom the left.</span></span> |
| <span data-ttu-id="58b09-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="58b09-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span></span> | <span data-ttu-id="58b09-125">Terzo pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-125">The third button from the left.</span></span> |
| <span data-ttu-id="58b09-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="58b09-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span></span> | <span data-ttu-id="58b09-127">Quarto pulsante da sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-127">The fourth button from the left.</span></span> |
| <span data-ttu-id="58b09-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="58b09-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span></span> | <span data-ttu-id="58b09-129">Pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-129">The rightmost mouse button.</span></span> |

<span data-ttu-id="58b09-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="58b09-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="58b09-131">Stato delle chiavi del controllo.</span><span class="sxs-lookup"><span data-stu-id="58b09-131">The state of the control keys.</span></span> <span data-ttu-id="58b09-132">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="58b09-132">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="58b09-133">Valore</span><span class="sxs-lookup"><span data-stu-id="58b09-133">Value</span></span> | <span data-ttu-id="58b09-134">Significato</span><span class="sxs-lookup"><span data-stu-id="58b09-134">Meaning</span></span> |
|-|-|
| <span data-ttu-id="58b09-135">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="58b09-135">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="58b09-136">La luce del blocco è attiva.</span><span class="sxs-lookup"><span data-stu-id="58b09-136">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="58b09-137">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="58b09-137">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="58b09-138">La chiave è stata migliorata.</span><span class="sxs-lookup"><span data-stu-id="58b09-138">The key is enhanced.</span></span> <span data-ttu-id="58b09-139">Vedere la [sezione Osservazioni](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="58b09-139">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="58b09-140">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="58b09-140">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="58b09-141">Viene premuto il tasto ALT sinistro.</span><span class="sxs-lookup"><span data-stu-id="58b09-141">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="58b09-142">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="58b09-142">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="58b09-143">Viene premuto il tasto CTRL sinistro.</span><span class="sxs-lookup"><span data-stu-id="58b09-143">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="58b09-144">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="58b09-144">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="58b09-145">Il BLOC NUM Light è on.</span><span class="sxs-lookup"><span data-stu-id="58b09-145">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="58b09-146">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="58b09-146">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="58b09-147">Viene premuto il tasto ALT destro.</span><span class="sxs-lookup"><span data-stu-id="58b09-147">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="58b09-148">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="58b09-148">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="58b09-149">Viene premuto il tasto CTRL destro.</span><span class="sxs-lookup"><span data-stu-id="58b09-149">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="58b09-150">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="58b09-150">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="58b09-151">La luce del blocco di scorrimento è attiva.</span><span class="sxs-lookup"><span data-stu-id="58b09-151">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="58b09-152">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="58b09-152">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="58b09-153">Il tasto MAIUSC è premuto.</span><span class="sxs-lookup"><span data-stu-id="58b09-153">The SHIFT key is pressed.</span></span> |

<span data-ttu-id="58b09-154">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="58b09-154">**dwEventFlags**</span></span>  
<span data-ttu-id="58b09-155">Tipo di evento del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-155">The type of mouse event.</span></span> <span data-ttu-id="58b09-156">Se questo valore è zero, indica che un pulsante del mouse viene premuto o rilasciato.</span><span class="sxs-lookup"><span data-stu-id="58b09-156">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="58b09-157">In caso contrario, questo membro è uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="58b09-157">Otherwise, this member is one of the following values.</span></span>

| <span data-ttu-id="58b09-158">Valore</span><span class="sxs-lookup"><span data-stu-id="58b09-158">Value</span></span> | <span data-ttu-id="58b09-159">Significato</span><span class="sxs-lookup"><span data-stu-id="58b09-159">Meaning</span></span> |
|-|-|
| <span data-ttu-id="58b09-160">**DOUBLE_CLICK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="58b09-160">**DOUBLE_CLICK** 0x0002</span></span> | <span data-ttu-id="58b09-161">Si è verificato il secondo clic (premere il pulsante) di un doppio clic.</span><span class="sxs-lookup"><span data-stu-id="58b09-161">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="58b09-162">Il primo clic viene restituito come evento normale di pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="58b09-162">The first click is returned as a regular button-press event.</span></span> |
| <span data-ttu-id="58b09-163">**MOUSE_HWHEELED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="58b09-163">**MOUSE_HWHEELED** 0x0008</span></span> | <span data-ttu-id="58b09-164">La rotellina del mouse orizzontale è stata spostata.</span><span class="sxs-lookup"><span data-stu-id="58b09-164">The horizontal mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="58b09-165">Se la parola alta del membro **dwButtonState** contiene un valore positivo, la rotellina è stata ruotata a destra.</span><span class="sxs-lookup"><span data-stu-id="58b09-165">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="58b09-166">In caso contrario, la rotellina è stata ruotata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="58b09-166">Otherwise, the wheel was rotated to the left.</span></span> |
| <span data-ttu-id="58b09-167">**Mouse_Moved** 0x0001</span><span class="sxs-lookup"><span data-stu-id="58b09-167">**MOUSE_MOVED** 0x0001</span></span> | <span data-ttu-id="58b09-168">È stata apportata una modifica alla posizione del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-168">A change in mouse position occurred.</span></span> |
| <span data-ttu-id="58b09-169">**MOUSE_WHEELED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="58b09-169">**MOUSE_WHEELED** 0x0004</span></span> | <span data-ttu-id="58b09-170">La rotellina del mouse verticale è stata spostata.</span><span class="sxs-lookup"><span data-stu-id="58b09-170">The vertical mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="58b09-171">Se la parola alta del membro **dwButtonState** contiene un valore positivo, la rotellina è stata ruotata verso l'alto, lontano dall'utente.</span><span class="sxs-lookup"><span data-stu-id="58b09-171">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="58b09-172">In caso contrario, la rotellina è stata ruotata indietro verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="58b09-172">Otherwise, the wheel was rotated backward, toward the user.</span></span> |

## <a name="remarks"></a><span data-ttu-id="58b09-173">Commenti</span><span class="sxs-lookup"><span data-stu-id="58b09-173">Remarks</span></span>

<span data-ttu-id="58b09-174">Gli eventi del mouse vengono inseriti nel buffer di input quando la console di è in modalità mouse ( **Abilita \_ \_ input del mouse** ).</span><span class="sxs-lookup"><span data-stu-id="58b09-174">Mouse events are placed in the input buffer when the console is in mouse mode ( **ENABLE\_MOUSE\_INPUT** ).</span></span>

<span data-ttu-id="58b09-175">Gli eventi del mouse vengono generati ogni volta che l'utente sposta il mouse oppure preme o rilascia uno dei pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="58b09-175">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="58b09-176">Gli eventi del mouse vengono inseriti nel buffer di input di una console solo quando il gruppo di console dispone dello stato attivo della tastiera e il cursore si trova all'interno dei bordi della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="58b09-176">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

## <a name="examples"></a><span data-ttu-id="58b09-177">Esempio</span><span class="sxs-lookup"><span data-stu-id="58b09-177">Examples</span></span>

<span data-ttu-id="58b09-178">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="58b09-178">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="58b09-179">Requisiti</span><span class="sxs-lookup"><span data-stu-id="58b09-179">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="58b09-180">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="58b09-180">Minimum supported client</span></span> | <span data-ttu-id="58b09-181">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="58b09-181">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="58b09-182">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="58b09-182">Minimum supported server</span></span> | <span data-ttu-id="58b09-183">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="58b09-183">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="58b09-184">Intestazione</span><span class="sxs-lookup"><span data-stu-id="58b09-184">Header</span></span> | <span data-ttu-id="58b09-185">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="58b09-185">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="58b09-186">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="58b09-186">See also</span></span>

[<span data-ttu-id="58b09-187">**COORD**</span><span class="sxs-lookup"><span data-stu-id="58b09-187">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="58b09-188">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="58b09-188">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="58b09-189">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="58b09-189">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="58b09-190">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="58b09-190">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="58b09-191">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="58b09-191">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
