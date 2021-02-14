---
title: GetConsoleOutputCP (funzione)
description: Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358951"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP (funzione)

Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante. Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.

## <a name="syntax"></a>Sintassi

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a>Parametri

Questa funzione non ha parametri.

## <a name="return-value"></a>Valore restituito

Il valore restituito è un codice che identifica la tabella codici. Per un elenco di identificatori, vedere [identificatori della tabella codici](/windows/win32/intl/code-page-identifiers).

Se il valore restituito è zero, la funzione ha avuto esito negativo. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi. Per recuperare altre informazioni su una tabella codici, incluso il relativo nome, vedere la funzione [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .

Per impostare la tabella codici di output di una console, usare la funzione [**SetConsoleOutputCP**](setconsoleoutputcp.md) . Per impostare ed eseguire una query sulla tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Tabelle codici della console](console-code-pages.md)

[Funzioni della console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)