---
title: Struttura KEY_EVENT_RECORD
description: Descrive un evento di input da tastiera in una struttura di record di INPUT della console \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: fd7386d5796442d34cdaa29fcf52831bc6aa1d78
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060420"
---
# <a name="key_event_record-structure"></a>Struttura del record dell' \_ evento chiave \_


Descrive un evento di input da tastiera in una struttura di [** \_ record di input**](input-record-str.md) della console.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

<a name="members"></a>Membri
-------

**bKeyDown**  
Se il tasto è premuto, questo membro è **true**. In caso contrario, questo membro è **false** (la chiave viene rilasciata).

**wRepeatCount**  
Il numero di ripetizioni, che indica che una chiave viene mantenuta inattiva. Ad esempio, quando un tasto è disattivato, è possibile che si ottengano cinque eventi con questo membro uguale a 1, un evento con questo membro uguale a 5 o più eventi con questo membro maggiore o uguale a 1.

**wVirtualKeyCode**  
[Codice a chiave virtuale](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) che identifica la chiave specificata in modo indipendente dal dispositivo.

**wVirtualScanCode**  
Codice di analisi virtuale della chiave specificata che rappresenta il valore dipendente dal dispositivo generato dall'hardware della tastiera.

**uChar**  
Unione dei membri seguenti.

**UnicodeChar**  
Carattere Unicode tradotto.

**AsciiChar**  
Carattere ASCII tradotto.

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

 

<a name="remarks"></a>Osservazioni
-------

Le chiavi avanzate per le tastiere IBM® 101 e 102-Key sono i tasti INS, CANC, HOME, END, PGSU, PGGIÙ e Direction nei cluster a sinistra del tastierino; e la divisione (/) e immettere le chiavi nella tastiera.

Gli eventi di input da tastiera vengono generati quando viene premuto o rilasciato un tasto qualsiasi, incluse le chiavi del controllo. Tuttavia, quando il tasto ALT viene premuto e rilasciato senza essere combinato con un altro carattere, ha un significato speciale per il sistema e non viene passato all'applicazione. Inoltre, la combinazione di tasti CTRL + C non viene passata se l'handle di input è in modalità elaborata (**Abilita \_ \_ input elaborato**).

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


[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**RECORD di INPUT \_**](input-record-str.md)

 

 




