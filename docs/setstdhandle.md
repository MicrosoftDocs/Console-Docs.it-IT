---
title: SetStdHandle (funzione)
description: Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039299"
---
# <a name="setstdhandle-function"></a>SetStdHandle (funzione)

Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).

## <a name="syntax"></a>Sintassi

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a>Parametri

*nStdHandle* \[ in\]  
Dispositivo standard per il quale deve essere impostato l'handle. Questo parametro può essere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Dispositivo di input standard. Inizialmente, si tratta del buffer di input della console `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Dispositivo di output standard. Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Dispositivo di errore standard. Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` . |

*hHandle* \[ in\]  
Handle per il dispositivo standard.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Gli handle standard di un processo potrebbero essere stati reindirizzati da una chiamata a **SetStdHandle** , nel qual caso [**GetStdHandle**](getstdhandle.md) restituirà l'handle reindirizzato. Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console. Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo della console.

## <a name="examples"></a>Esempio

Per un esempio, vedere [creazione di un processo figlio con input e output reindirizzati](https://msdn.microsoft.com/library/windows/desktop/ms682499).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ProcessEnv. h (tramite Winbase. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[Handle della console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)
