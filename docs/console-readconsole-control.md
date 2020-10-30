---
title: Struttura CONSOLE_READCONSOLE_CONTROL
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_READCONSOLE_CONTROL, che contiene informazioni per un'operazione di lettura della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039189"
---
# <a name="console_readconsole_control-structure"></a>\_Struttura di \_ controllo READCONSOLE console

Contiene informazioni per un'operazione di lettura della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a>Members

**nLength**  
Dimensione della struttura. Impostare questo membro su `sizeof(CONSOLE_READCONSOLE_CONTROL)` .

**nInitialChars**  
Numero di caratteri da ignorare (e di conseguenza conservati) prima di scrivere un nuovo input di lettura nel buffer passato alla funzione [**ReadConsole**](readconsole.md) . Questo valore deve essere minore del parametro *nNumberOfCharsToRead* della funzione **ReadConsole** .

**dwCtrlWakeupMask**  
Maschera che specifica i caratteri di controllo tra `0x00` e `0x1F` da usare per segnalare che la lettura è stata completata. Ogni bit corrisponde a un carattere con il bit meno significativo che corrisponde a `0x00` o `NUL` e il bit più significativo corrispondente a `0x1F` o `US` . È possibile specificare più bit (caratteri di controllo).

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

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**ReadConsole**](readconsole.md)
