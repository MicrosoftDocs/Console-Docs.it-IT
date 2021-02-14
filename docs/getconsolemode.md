---
title: GetConsoleMode (funzione)
description: Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 3f98797b0662dadcf696f76ffda5f42e759bf930
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357283"
---
# <a name="getconsolemode-function"></a>GetConsoleMode (funzione)

Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a>Parametri

*hConsoleHandle* \[in\]  
Handle per il buffer di input della console o il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpMode* \[ out\]  
Puntatore a una variabile che riceve la modalità corrente del buffer specificato.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

Per modificare le modalità I/O di una console, chiamare la funzione [**SetConsoleMode**](setconsolemode.md) .

## <a name="examples"></a>Esempi

Un esempio è disponibile in [Lettura di eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Modalità della console](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)