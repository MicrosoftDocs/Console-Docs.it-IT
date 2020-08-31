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
# <a name="mouse_event_record-structure"></a>Struttura del record dell' \_ evento del mouse \_


Descrive un evento di input del mouse in una struttura di [** \_ record di input**](input-record-str.md) della console.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a>Membri
-------

**dwMousePosition**  
Struttura [**Coord**](coord-str.md) che contiene la posizione del cursore, in termini di coordinate delle celle dei caratteri del buffer dello schermo della console.

**dwButtonState**  
Stato dei pulsanti del mouse. Il bit meno significativo corrisponde al pulsante del mouse più a sinistra. Il bit meno significativo successivo corrisponde al pulsante del mouse più a destra. Il bit successivo indica il pulsante del mouse successivo a quello più a sinistra. I bit corrispondono quindi da sinistra a destra ai pulsanti del mouse. Un bit è 1 se è stato premuto il pulsante.

Le costanti seguenti sono definite per i primi cinque pulsanti del mouse.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</td>
<td><p>Pulsante del mouse più a sinistra.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</td>
<td><p>Secondo pulsante da sinistra.</p></td>
</tr>
<tr class="odd">
<td><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</td>
<td><p>Terzo pulsante da sinistra.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</td>
<td><p>Quarto pulsante da sinistra.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</td>
<td><p>Pulsante destro del mouse.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwControlKeyState**  
Stato delle chiavi del controllo. Il membro può essere costituito da uno o più dei valori seguenti.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</td>
<td><p>La luce del blocco è attiva.</p></td>
</tr>
<tr class="even">
<td><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</td>
<td><p>La chiave è stata migliorata.</p></td>
</tr>
<tr class="odd">
<td><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</td>
<td><p>Viene premuto il tasto ALT sinistro.</p></td>
</tr>
<tr class="even">
<td><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</td>
<td><p>Viene premuto il tasto CTRL sinistro.</p></td>
</tr>
<tr class="odd">
<td><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</td>
<td><p>Il BLOC NUM Light è on.</p></td>
</tr>
<tr class="even">
<td><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</td>
<td><p>Viene premuto il tasto ALT destro.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</td>
<td><p>Viene premuto il tasto CTRL destro.</p></td>
</tr>
<tr class="even">
<td><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</td>
<td><p>La luce del blocco di scorrimento è attiva.</p></td>
</tr>
<tr class="odd">
<td><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</td>
<td><p>Il tasto MAIUSC è premuto.</p></td>
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

 

**dwEventFlags**  
Tipo di evento del mouse. Se questo valore è zero, indica che un pulsante del mouse viene premuto o rilasciato. In caso contrario, questo membro è uno dei valori seguenti.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</td>
<td><p>Si è verificato il secondo clic (premere il pulsante) di un doppio clic. Il primo clic viene restituito come evento normale di pressione del pulsante.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</td>
<td><p>La rotellina del mouse orizzontale è stata spostata.</p>
<p>Se la parola alta del membro <strong>dwButtonState</strong> contiene un valore positivo, la rotellina è stata ruotata a destra. In caso contrario, la rotellina è stata ruotata a sinistra.</p></td>
</tr>
<tr class="odd">
<td><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>Mouse_Moved</strong> 0x0001</td>
<td><p>È stata apportata una modifica alla posizione del mouse.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</td>
<td><p>La rotellina del mouse verticale è stata spostata.</p>
<p>Se la parola alta del membro <strong>dwButtonState</strong> contiene un valore positivo, la rotellina è stata ruotata verso l'alto, lontano dall'utente. In caso contrario, la rotellina è stata ruotata indietro verso l'utente.</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Osservazioni
-------

Gli eventi del mouse vengono inseriti nel buffer di input quando la console di è in modalità mouse (**Abilita \_ \_ input del mouse**).

Gli eventi del mouse vengono generati ogni volta che l'utente sposta il mouse oppure preme o rilascia uno dei pulsanti del mouse. Gli eventi del mouse vengono inseriti nel buffer di input di una console solo quando il gruppo di console dispone dello stato attivo della tastiera e il cursore si trova all'interno dei bordi della finestra della console.

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

<a name="requirements"></a>Requisiti
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimo supportato</p></td>
<td><p>Windows 2000 Professional [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows 2000 Server [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>WinConTypes. h (tramite wincon. h, Includi Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[**COORD**](coord-str.md)

[**RECORD di INPUT \_**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




