---
title: Struttura MENU_EVENT_RECORD
description: Descrive un evento di menu in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039519"
---
# <a name="menu_event_record-structure"></a>Struttura del record dell' \_ evento menu \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Descrive un evento di menu in una struttura di [**\_ record di input**](input-record-str.md) della console. Questi eventi vengono usati internamente e devono essere ignorati.

## <a name="syntax"></a>Sintassi

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a>Members

**dwCommandId**  
Riservato.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinConTypes. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**RECORD di INPUT \_**](input-record-str.md)
