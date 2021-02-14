---
title: GetNumberOfConsoleInputEvents (funzione)
description: Recupera il numero di record di input non letti nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 622dc96598df9a851934c73645afb7691f77f1be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358861"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents (funzione)

Recupera il numero di record di input non letti nel buffer di input della console.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a>Parametri

*hConsoleInput* \[ in\]  
Handle per il buffer di input della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpcNumberOfEvents* \[ out\]  
Puntatore a una variabile che riceve il numero di record di input non letti nel buffer di input della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

La funzione **GetNumberOfConsoleInputEvents** indica il numero totale di record di input non letti nel buffer di input, tra cui la tastiera, il mouse e i record di input per il ridimensionamento delle finestre. I processi che usano la funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) possono leggere solo l'input da tastiera. I processi che usano la funzione [**ReadConsoleInput**](readconsoleinput.md) possono leggere tutti i tipi di record di input.

Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](/windows/win32/sync/wait-functions) per determinare quando l'input della console non è stato letto. Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.

Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) . Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

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

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Funzioni di input della console di basso livello](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)