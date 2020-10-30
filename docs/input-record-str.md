---
title: Struttura INPUT_RECORD
description: Vedere le informazioni di riferimento sulla struttura INPUT_RECORD, che descrive un evento di input nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038539"
---
# <a name="input_record-structure"></a>\_Struttura record di input

Descrive un evento di input nel buffer di input della console. Questi record possono essere letti dal buffer di input usando la funzione [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) o scritti nel buffer di input usando la funzione [**WriteConsoleInput**](writeconsoleinput.md) .

## <a name="syntax"></a>Sintassi

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a>Members

**EventType**  
Handle per il tipo di evento di input e il record dell'evento archiviato nel membro dell' **evento** .

Il membro può essere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **FOCUS_EVENT** 0x0010 | Il membro dell' **evento** contiene una struttura **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** . Questi eventi vengono usati internamente e devono essere ignorati. |
| **KEY_EVENT** 0x0001 | Il membro dell' **evento** contiene una struttura **[KEY_EVENT_RECORD](key-event-record-str.md)** con informazioni su un evento di tastiera. |
| **MENU_EVENT** 0x0008 | Il membro dell' **evento** contiene una struttura **[MENU_EVENT_RECORD](menu-event-record-str.md)** . Questi eventi vengono usati internamente e devono essere ignorati. |
| **Mouse_event** 0x0002 | Il membro dell' **evento** contiene una struttura di **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** con informazioni su un evento di spostamento o di un pulsante del mouse. |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | Il membro dell' **evento** contiene una struttura **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** con informazioni sulle nuove dimensioni del buffer dello schermo della console. |

**Event**  
Informazioni sull'evento. Il formato di questo membro dipende dal tipo di evento specificato dal membro **eventType** .

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**\_record evento \_ attivo**](focus-event-record-str.md)

[**\_record evento \_ chiave**](key-event-record-str.md)

[**\_record evento \_ menu**](menu-event-record-str.md)

[**\_record evento \_ mouse**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
