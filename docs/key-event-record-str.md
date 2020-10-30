---
title: Struttura KEY_EVENT_RECORD
description: Descrive un evento di input da tastiera in una struttura di record di INPUT della console \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0a2ba8ecf8b07a83db54642c2399bb93d99b7aa2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039529"
---
# <a name="key_event_record-structure"></a>Struttura del record dell' \_ evento chiave \_

Descrive un evento di input da tastiera in una struttura di [**\_ record di input**](input-record-str.md) della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

## <a name="members"></a>Members

**bKeyDown**  
Se il tasto è premuto, questo membro è **true** . In caso contrario, questo membro è **false** (la chiave viene rilasciata).

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

## <a name="remarks"></a>Commenti

Le chiavi avanzate per le tastiere IBM® 101 e 102-Key sono i tasti INS, CANC, HOME, END, PGSU, PGGIÙ e Direction nei cluster a sinistra del tastierino; e la divisione (/) e immettere le chiavi nella tastiera.

Gli eventi di input da tastiera vengono generati quando viene premuto o rilasciato un tasto qualsiasi, incluse le chiavi del controllo. Tuttavia, quando il tasto ALT viene premuto e rilasciato senza essere combinato con un altro carattere, ha un significato speciale per il sistema e non viene passato all'applicazione. Inoltre, la combinazione di tasti CTRL + C non viene passata se l'handle di input è in modalità elaborata ( **Abilita \_ \_ input elaborato** ).

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**RECORD di INPUT \_**](input-record-str.md)
