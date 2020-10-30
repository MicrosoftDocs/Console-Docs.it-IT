---
title: SetConsoleCP (funzione)
description: Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039409"
---
# <a name="setconsolecp-function"></a>SetConsoleCP (funzione)

Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante. Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>Parametri

*wCodePageID* \[ in\]  
Identificatore della tabella codici da impostare. Per altre informazioni, vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.

Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) . Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Tuttavia, è preferibile usare [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.

Per determinare se una determinata tabella codici è valida, utilizzare la funzione [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) . Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](https://msdn.microsoft.com/library/windows/desktop/dd317756)delle tabelle codici.

Per determinare la tabella codici di input corrente di una console, usare la funzione [**GetConsoleCP**](getconsolecp.md) . Per impostare e recuperare la tabella codici di output di una console, usare le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Tabelle codici della console](console-code-pages.md)

[Funzioni console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
