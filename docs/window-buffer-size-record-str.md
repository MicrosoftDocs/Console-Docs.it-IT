---
title: Struttura WINDOW_BUFFER_SIZE_RECORD
description: Vedere le informazioni di riferimento sulla struttura WINDOW_BUFFER_SIZE_RECORD, che descrive una modifica delle dimensioni del buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039269"
---
# <a name="window_buffer_size_record-structure"></a>\_ \_ Struttura record dimensioni buffer finestra \_

Descrive una modifica delle dimensioni del buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a>Members

**dwSize**  
Struttura [**Coord**](coord-str.md) che contiene le dimensioni del buffer dello schermo della console, in colonne e righe di celle di tipo carattere.

## <a name="remarks"></a>Commenti

Gli eventi di dimensioni del buffer vengono inseriti nel buffer di input quando la console di è in modalità compatibile con la finestra ( **Abilita \_ \_ input finestra** ).

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**COORD**](coord-str.md)

[**RECORD di INPUT \_**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)
