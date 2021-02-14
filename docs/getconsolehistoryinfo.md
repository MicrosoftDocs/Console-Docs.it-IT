---
title: GetConsoleHistoryInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleHistoryInfo, che recupera le impostazioni della cronologia per la console del processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a26dbeb2a873bd780f91c240bf2658cde11b45ec
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359021"
---
# <a name="getconsolehistoryinfo-function"></a>GetConsoleHistoryInfo (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera le impostazioni della cronologia per la console del processo chiamante.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>Parametri

*lpConsoleHistoryInfo* \[ out\]  
Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che riceve le impostazioni della cronologia per la console del processo chiamante.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo errore su **\_ accesso \_ negato**.

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**\_informazioni cronologia \_ console**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)