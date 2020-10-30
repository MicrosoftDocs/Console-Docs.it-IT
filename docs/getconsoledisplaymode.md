---
title: GetConsoleDisplayMode (funzione)
description: Vedere informazioni di riferimento sulla funzione GetConsoleDisplayMode, che consente di recuperare la modalità di visualizzazione della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 74dc06cbb7ecadb0f86c4c4a992e3526be8ab74d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038059"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera la modalità di visualizzazione della console corrente.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a>Parametri

*lpModeFlags* \[ out\]  
Modalità di visualizzazione della console. Il parametro può essere costituito da uno o più dei valori seguenti.

| Valore | Significato |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | Console a schermo intero. La console è in questa modalità non appena la finestra è ingrandita. A questo punto, la transizione alla modalità schermo intero può comunque avere esito negativo. |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | Console a schermo intero che comunica direttamente con l'hardware del video. Questa modalità viene impostata dopo che la console è in modalità **CONSOLE_FULLSCREEN** per indicare che la transizione alla modalità schermo intero è stata completata. |

> [!NOTE]
> La transizione a una modalità hardware video a schermo intero 100% è stata rimossa in Windows Vista con la ripiattaforma dello stack di grafica su [WDDM](https://docs.microsoft.com//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model). Nelle versioni successive di Windows, lo stato massimo risultante è **CONSOLE_FULLSCREEN** che rappresenta una finestra senza frame visualizzata a schermo intero, ma non è in esclusiva per il controllo dell'hardware.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)
