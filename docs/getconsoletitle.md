---
title: GetConsoleTitle (funzione)
description: Recupera il titolo e le dimensioni del titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 6a4c4634316442ac2b03602b6c931b05385d77df
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358331"
---
# <a name="getconsoletitle-function"></a>GetConsoleTitle (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera il titolo per la finestra della console corrente.

## <a name="syntax"></a>Sintassi

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Parametri

*lpConsoleTitle* \[ out\]  
Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo. Se il buffer è troppo piccolo per archiviare il titolo, la funzione archivia il numero di caratteri del titolo che rientrerà nel buffer, terminando con un carattere di terminazione null.

*nSize* \[ in\]  
Dimensioni del buffer a cui punta il parametro *lpConsoleTitle* , in caratteri.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è la lunghezza del titolo della finestra della console, in caratteri.

Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) restituisce il codice di errore.

## <a name="remarks"></a>Commenti

Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) . Per recuperare la stringa del titolo originale, usare la funzione [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** . Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi. Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.

## <a name="examples"></a>Esempio

Per un esempio, vedere [**SetConsoleTitle**](setconsoletitle.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **GetConsoleTitleW** (Unicode) e **GetConsoleTitleA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)