---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Struttura SMALL_RECT
description: Definisce le coordinate degli angoli superiore sinistro e inferiore destro di un rettangolo.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: f9cbe94fff616a93d835f47b618a28bb9f521891
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358491"
---
# <a name="small_rect-structure"></a>\_Struttura Rect piccola

Definisce le coordinate degli angoli superiore sinistro e inferiore destro di un rettangolo.

## <a name="syntax"></a>Sintassi

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a>Members

**Sinistra**  
Coordinata x dell'angolo superiore sinistro del rettangolo.

**Top**  
Coordinata y dell'angolo superiore sinistro del rettangolo.

**Ok**  
Coordinata x dell'angolo inferiore destro del rettangolo.

**Ultimo**  
Coordinata y dell'angolo inferiore destro del rettangolo.

## <a name="remarks"></a>Commenti

Questa struttura viene utilizzata dalle funzioni console per specificare le aree rettangolari dei buffer dello schermo della console, in cui le coordinate specificano le righe e le colonne delle celle dei caratteri del buffer dello schermo.

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**RECT**](/previous-versions//dd162897(v=vs.85))

[**RECTL**](/previous-versions//dd162907(v=vs.85))