---
title: SetConsoleDisplayMode (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleDisplayMode, che imposta la modalità di visualizzazione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039389"
---
# <a name="setconsoledisplaymode-function"></a>SetConsoleDisplayMode (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta la modalità di visualizzazione del buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console.

*dwFlags* \[ in\]  
Modalità di visualizzazione della console. Il parametro può essere costituito da uno o più dei valori seguenti.

| Valore | Significato |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | Il testo viene visualizzato in modalità schermo intero. |
| **CONSOLE_WINDOWED_MODE** 2 | Il testo viene visualizzato in una finestra della console. |

*lpNewScreenBufferDimensions* \[ out, facoltativo\]  
Puntatore a una struttura [**Coord**](coord-str.md) che riceve le nuove dimensioni del buffer dello schermo, in caratteri.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Osservazioni

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[Modalità console](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)
