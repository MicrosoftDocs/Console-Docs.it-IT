---
title: Struttura CONSOLE_CURSOR_INFO
description: Contiene le informazioni sulle dimensioni e sulla visibilità relative al cursore della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037014"
---
# <a name="console_cursor_info-structure"></a>\_ \_ Struttura informazioni cursore console

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene informazioni sul cursore della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a>Members

**dwSize**  
Percentuale della cella di tipo carattere compilata dal cursore. Questo valore è compreso tra 1 e 100. L'aspetto del cursore varia a seconda che la cella venga riempita completamente per essere visualizzata come riga orizzontale nella parte inferiore della cella.

> [!NOTE]
>Anche se il valore **dwSize** è in genere compreso tra 1 e 100, in alcune circostanze potrebbe essere restituito un valore esterno a tale intervallo. Se, ad esempio, **CursorSize** è impostato su 0 nel registro di sistema, il valore **dwSize** restituito sarà 0.

 **bVisible**  
Visibilità del cursore. Se il cursore è visibile, questo membro è **true** .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | WinCon. h (include Windows. h) |

## <a name="see-also"></a>Vedi anche

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)
