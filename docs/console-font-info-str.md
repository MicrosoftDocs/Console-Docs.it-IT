---
title: Struttura CONSOLE_FONT_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFO, che contiene l'indice e le dimensioni per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037139"
---
# <a name="console_font_info-structure"></a>Struttura delle informazioni sul tipo di carattere della CONSOLE \_ \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene informazioni per un tipo di carattere della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a>Members

**nFont**  
Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.

**dwFontSize**  
Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche. Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.

## <a name="remarks"></a>Commenti

Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | WinCon. h (include Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
