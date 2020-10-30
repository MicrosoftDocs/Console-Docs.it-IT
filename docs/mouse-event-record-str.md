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
# <a name="mouse_event_record-structure"></a>Struttura del record dell' \_ evento del mouse \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Descrive un evento di input del mouse in una struttura di [**\_ record di input**](input-record-str.md) della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a>Members

**dwMousePosition**  
Struttura [**Coord**](coord-str.md) che contiene la posizione del cursore, in termini di coordinate delle celle dei caratteri del buffer dello schermo della console.

**dwButtonState**  
Stato dei pulsanti del mouse. Il bit meno significativo corrisponde al pulsante del mouse più a sinistra. Il bit meno significativo successivo corrisponde al pulsante del mouse più a destra. Il bit successivo indica il pulsante del mouse successivo a quello più a sinistra. I bit corrispondono quindi da sinistra a destra ai pulsanti del mouse. Un bit è 1 se è stato premuto il pulsante.

Le costanti seguenti sono definite per i primi cinque pulsanti del mouse.

| Valore | Significato |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | Pulsante del mouse più a sinistra. |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | Secondo pulsante da sinistra. |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | Terzo pulsante da sinistra. |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | Quarto pulsante da sinistra. |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | Pulsante destro del mouse. |

**dwControlKeyState**  
Stato delle chiavi del controllo. Il membro può essere costituito da uno o più dei valori seguenti.

| Valore | Significato |
|-|-|
| **CAPSLOCK_ON** 0x0080 | La luce del blocco è attiva. |
| **ENHANCED_KEY** 0x0100 | La chiave è stata migliorata. Vedere la [sezione Osservazioni](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | Viene premuto il tasto ALT sinistro. |
| **LEFT_CTRL_PRESSED** 0x0008 | Viene premuto il tasto CTRL sinistro. |
| **NUMLOCK_ON** 0x0020 | Il BLOC NUM Light è on. |
| **RIGHT_ALT_PRESSED** 0x0001 | Viene premuto il tasto ALT destro. |
| **RIGHT_CTRL_PRESSED** 0x0004 | Viene premuto il tasto CTRL destro. |
| **SCROLLLOCK_ON** 0x0040 | La luce del blocco di scorrimento è attiva. |
| **SHIFT_PRESSED** 0x0010 | Il tasto MAIUSC è premuto. |

**dwEventFlags**  
Tipo di evento del mouse. Se questo valore è zero, indica che un pulsante del mouse viene premuto o rilasciato. In caso contrario, questo membro è uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **DOUBLE_CLICK** 0x0002 | Si è verificato il secondo clic (premere il pulsante) di un doppio clic. Il primo clic viene restituito come evento normale di pressione del pulsante. |
| **MOUSE_HWHEELED** 0x0008 | La rotellina del mouse orizzontale è stata spostata.<br /><br />Se la parola alta del membro **dwButtonState** contiene un valore positivo, la rotellina è stata ruotata a destra. In caso contrario, la rotellina è stata ruotata a sinistra. |
| **Mouse_Moved** 0x0001 | È stata apportata una modifica alla posizione del mouse. |
| **MOUSE_WHEELED** 0x0004 | La rotellina del mouse verticale è stata spostata.<br /><br />Se la parola alta del membro **dwButtonState** contiene un valore positivo, la rotellina è stata ruotata verso l'alto, lontano dall'utente. In caso contrario, la rotellina è stata ruotata indietro verso l'utente. |

## <a name="remarks"></a>Commenti

Gli eventi del mouse vengono inseriti nel buffer di input quando la console di è in modalità mouse ( **Abilita \_ \_ input del mouse** ).

Gli eventi del mouse vengono generati ogni volta che l'utente sposta il mouse oppure preme o rilascia uno dei pulsanti del mouse. Gli eventi del mouse vengono inseriti nel buffer di input di una console solo quando il gruppo di console dispone dello stato attivo della tastiera e il cursore si trova all'interno dei bordi della finestra della console.

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**RECORD di INPUT \_**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
