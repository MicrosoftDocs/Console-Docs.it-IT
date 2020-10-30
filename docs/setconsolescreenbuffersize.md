---
title: SetConsoleScreenBufferSize (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleScreenBufferSize, che modifica la dimensione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039329"
---
# <a name="setconsolescreenbuffersize-function"></a>SetConsoleScreenBufferSize (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Modifica la dimensione del buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*dwSize* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica la nuova dimensione del buffer dello schermo della console, in righe e colonne di tipo carattere. La larghezza e l'altezza specificate non possono essere minori della larghezza e dell'altezza della finestra del buffer dello schermo della console. Anche le dimensioni specificate non possono essere inferiori alle dimensioni minime consentite dal sistema. Questo valore minimo dipende dalle dimensioni correnti del carattere per la console (selezionate dall'utente) e dai valori **\_ CYMIN** **SM \_ CXMIN** e SM restituiti dalla funzione [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Osservazioni

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[Buffer di input della console](console-input-buffer.md)

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)
