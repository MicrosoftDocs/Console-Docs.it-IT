---
title: Struttura CONSOLE_SCREEN_BUFFER_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SCREEN_BUFFER_INFOEX, che contiene informazioni estese su un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358082"
---
# <a name="console_screen_buffer_infoex-structure"></a>\_ \_ Struttura INFOEX buffer dello schermo della console \_

Contiene informazioni estese su un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a>Members

**cbSize**  
Dimensioni, in byte, della struttura.

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

**wPopupAttributes**  
Attributo Fill per i popup della console.

**bFullscreenSupported**  
Se questo membro è `TRUE` , la modalità schermo intero è supportata; in caso contrario, non lo è. Questa operazione sarà sempre `FALSE` destinata ai sistemi dopo Windows Vista con il [modello di driver WDDM](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , perché l'accesso diretto a VGA diretto al monitor non è più disponibile.

**ColorTable**  
Matrice di valori [**COLORREF**](/windows/win32/gdi/colorref) che descrivono le impostazioni relative ai colori della console.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**\_Rect piccolo**](small-rect-str.md)