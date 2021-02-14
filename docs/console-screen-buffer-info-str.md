---
title: Struttura CONSOLE_SCREEN_BUFFER_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SCREEN_BUFFER_INFO, che contiene informazioni su un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 31ef1cf8e78029be48d5217cbc82f84663d627b5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358121"
---
# <a name="console_screen_buffer_info-structure"></a>\_Struttura delle \_ informazioni sul buffer dello schermo della console \_

Contiene informazioni su un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a>Members

**dwSize**  
Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne di tipo carattere e righe.

**dwCursorPosition**  
Struttura [**Coord**](coord-str.md) che contiene le coordinate di riga e di colonna del cursore nel buffer dello schermo della console.

**wAttributes**  
Attributi dei caratteri scritti in un buffer dello schermo dalle funzioni [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) e [**WriteConsole**](writeconsole.md) oppure restituiti a un buffer dello schermo dalle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**ReadConsole**](readconsole.md) . Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).

**srWindow**  
Una [**piccola struttura \_ Rect**](small-rect-str.md) che contiene le coordinate del buffer dello schermo della console degli angoli superiore sinistro e inferiore destro della finestra di visualizzazione.

**dwMaximumWindowSize**  
Struttura [**Coord**](coord-str.md) che contiene la dimensione massima della finestra della console, in colonne di tipo carattere e righe, date le dimensioni correnti del buffer dello schermo e il tipo di carattere e le dimensioni dello schermo.

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**\_Rect piccolo**](small-rect-str.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)