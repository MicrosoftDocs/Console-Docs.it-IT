---
title: Struttura CHAR_INFO
description: Specifica un carattere Unicode o ANSI e i relativi attributi. Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037379"
---
# <a name="char_info-structure"></a>\_Struttura info char

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Specifica un carattere Unicode o ANSI e i relativi attributi. Questa struttura viene utilizzata dalle funzioni console per la lettura e la scrittura in un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a>Members

**Char**  
Unione dei membri seguenti.

**UnicodeChar**  
Carattere Unicode di una cella del carattere del buffer dello schermo.

**AsciiChar**  
Carattere ANSI di una cella del carattere del buffer dello schermo.

**Attributes (Attributi)**  
Attributi carattere. Questo membro può essere zero o una qualsiasi combinazione dei valori seguenti.

| Valore | Significato |
|-|-|
| **FOREGROUND_BLUE**`0x0001` | Il colore del testo contiene il blu. |
| **FOREGROUND_GREEN**`0x0002` | Il colore del testo contiene verde. |
| **FOREGROUND_RED**`0x0004` | Il colore del testo contiene rosso. |
| **FOREGROUND_INTENSITY**`0x0008` | Il colore del testo viene intensificato. |
| **BACKGROUND_BLUE**`0x0010` | Il colore di sfondo contiene blu. |
| **BACKGROUND_GREEN**`0x0020` | Il colore di sfondo contiene verde. |
| **BACKGROUND_RED**`0x0040` | Il colore di sfondo contiene rosso. |
| **BACKGROUND_INTENSITY**`0x0080` | Il colore di sfondo viene intensificato. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Byte iniziali. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Byte finale. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Orizzontale superiore. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Sinistra verticale. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Diritto verticale. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Inverso in primo piano e in background. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Sottolineatura. |

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinCon. h (include Windows. h) |

## <a name="see-also"></a>Vedi anche

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
