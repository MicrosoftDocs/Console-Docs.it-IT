---
title: Struttura CONSOLE_HISTORY_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_HISTORY_INFO, che contiene informazioni sulla cronologia della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039219"
---
# <a name="console_history_info-structure"></a>Struttura delle informazioni della \_ cronologia della console \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene informazioni sulla cronologia della console.

## <a name="syntax"></a>Sintassi

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a>Members

**cbSize**  
Dimensioni, in byte, della struttura. Impostare questo membro su `sizeof(CONSOLE_HISTORY_INFO)` .

**HistoryBufferSize**  
Il numero di comandi conservati in ogni buffer della cronologia.

**NumberOfHistoryBuffers**  
Numero di buffer di cronologia conservati per questo processo della console.

**dwFlags**  
Questo parametro può essere zero o il valore seguente.

| Valore | Significato |
|-|-|
| **HISTORY_NO_DUP_FLAG** 0x1 | Le voci duplicate non verranno archiviate nel buffer della cronologia.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |

## <a name="see-also"></a>Vedi anche

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
