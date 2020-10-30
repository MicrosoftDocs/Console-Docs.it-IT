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
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037099"
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

**In basso**  
Coordinata y dell'angolo inferiore destro del rettangolo.

## <a name="remarks"></a>Commenti

Questa struttura viene utilizzata dalle funzioni console per specificare le aree rettangolari dei buffer dello schermo della console, in cui le coordinate specificano le righe e le colonne delle celle dei caratteri del buffer dello schermo.

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**RECT**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTL**](https://msdn.microsoft.com/library/windows/desktop/dd162907)
