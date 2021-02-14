---
title: AllocConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AllocConsole che alloca una nuova console per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357861"
---
# <a name="allocconsole-function"></a>AllocConsole (funzione)

Alloca una nuova console per il processo chiamante.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a>Parametri

Questa funzione non ha parametri.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Un processo può essere associato a una sola console, quindi la funzione **AllocConsole** ha esito negativo se il processo chiamante dispone già di una console. Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console corrente e successivamente chiamare la funzione **AllocConsole** per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.

Se il processo chiamante crea un processo figlio, l'elemento figlio eredita la nuova console.

La funzione **AllocConsole** inizializza l'input standard, l'output standard e gli handle di errore standard per la nuova console. L'handle di input standard è un handle per il buffer di input della console, gli handle di output standard e di errore standard sono handle per il buffer dello schermo della console. Per recuperare questi handle usare la funzione [**GetStdHandle**](getstdhandle.md).

Questa funzione viene utilizzata principalmente da un'applicazione interfaccia utente grafica (GUI) per creare una finestra della console. Le applicazioni GUI vengono inizializzate senza una console. Le applicazioni console vengono inizializzate con una console a meno che non vengano create come processi scollegati (chiamando la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con il flag **DETACHED\_PROCESS**).

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

[Console](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)