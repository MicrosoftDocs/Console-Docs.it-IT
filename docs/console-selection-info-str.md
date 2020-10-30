---
title: Struttura CONSOLE_SELECTION_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SELECTION_INFO, che contiene informazioni per la selezione di una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038369"
---
# <a name="console_selection_info-structure"></a>Struttura delle informazioni di \_ selezione della console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene informazioni per la selezione di una console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a>Members

**dwFlags**  
Indicatore di selezione. Il membro può essere costituito da uno o più dei valori seguenti.

| Valore | Significato |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | Il mouse è inattivo. L'utente sta modificando attivamente il rettangolo di selezione con il mouse. |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | Selezione con il mouse. Se è disattivata, l'utente è la `conhost.exe` selezione della modalità contrassegno operativo con la tastiera. |
| **CONSOLE_NO_SELECTION** 0x0000 | Nessuna selezione. |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | La selezione è iniziata. Se una selezione del mouse non si verifica in genere senza il `CONSOLE_SELECTION_NOT_EMPTY` flag. Se si seleziona una tastiera, questo può verificarsi quando è stata immessa la modalità contrassegno, ma l'utente continua a spostarsi nella posizione iniziale. |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | Rettangolo di selezione non vuoto. Il payload di *dwSelectionAnchor* e *srSelection* sono validi.  |

**dwSelectionAnchor**  
Struttura [**Coord**](coord-str.md) che specifica l'ancoraggio di selezione, in caratteri.

**srSelection**  
Struttura [**\_ Rect piccola**](small-rect-str.md) che specifica il rettangolo di selezione.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**\_Rect piccolo**](small-rect-str.md)
