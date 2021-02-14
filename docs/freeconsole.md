---
title: FreeConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione FreeConsole, che scollega il processo chiamante dalla relativa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a7a90b3770128067a63b4872e6bb9a37acdcaf6c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359011"
---
# <a name="freeconsole-function"></a>FreeConsole (funzione)

Scollega il processo chiamante dalla relativa console.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a>Parametri

Questa funzione non ha parametri.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Un processo può essere collegato al massimo da una console. Se il processo chiamante non è già collegato a una console, il codice di errore restituito **è \_ errore \_ parametro non valido** (87).

Un processo può utilizzare la funzione **FreeConsole** per scollegarsi dalla console. Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento. Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**. Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[Funzioni della console](console-functions.md)

[Console](consoles.md)