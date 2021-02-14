---
title: GetConsoleOriginalTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleOriginalTitle, che recupera il titolo originale per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359001"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera il titolo originale per la finestra della console corrente.

## <a name="syntax"></a>Sintassi

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Parametri

*lpConsoleTitle* \[ out\]  
Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo originale.

*nSize* \[ in\]  
Dimensioni del buffer *lpConsoleTitle* , in caratteri.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito corrisponde alla lunghezza della stringa copiata nel buffer, in caratteri.

Se il buffer non è abbastanza grande per archiviare il titolo, il valore restituito è zero e [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) restituisce un **errore di \_ esito positivo**.

Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) restituisce il codice di errore.

## <a name="remarks"></a>Commenti

Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) . Per recuperare la stringa del titolo corrente, usare la funzione [**GetConsoleTitle**](getconsoletitle.md) .

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0600 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** . Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi. Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **GetConsoleOriginalTitleW** (Unicode) e **GetConsoleOriginalTitleA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)