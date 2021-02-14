---
title: Struttura CONSOLE_FONT_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFOEX, che contiene informazioni estese per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 3ab4424be99ba9eceda54db1ebf7c7e13560f722
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358151"
---
# <a name="console_font_infoex-structure"></a>\_Struttura INFOEX del tipo di carattere della console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene informazioni estese per un tipo di carattere della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a>Members

**cbSize**  
Dimensioni, in byte, della struttura. Questo membro deve essere impostato su `sizeof(CONSOLE_FONT_INFOEX)` prima di chiamare [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o avrà esito negativo.

**nFont**  
Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.

**dwFontSize**  
Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche. Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.

**FontFamily**  
Il passo del carattere e la famiglia. Per informazioni sui valori possibili per questo membro, vedere la descrizione del membro **tmPitchAndFamily** della struttura [**TEXTMETRIC**](/windows/win32/api/wingdi/ns-wingdi-textmetrica) .

**SpessoreCarattere**  
Spessore del carattere. Il peso può variare da 100 a 1000, in multipli di 100. Ad esempio, il peso normale è 400, mentre 700 è in grassetto.

**Contemplato**  
Nome del carattere tipografico, ad esempio Courier o Arial.

## <a name="remarks"></a>Commenti

Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | WinCon. h (include Windows. h) |

## <a name="see-also"></a>Vedi anche

[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)