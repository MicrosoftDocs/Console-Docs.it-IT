---
title: ReadConsoleInput (funzione)
description: Legge i dati da un buffer di input della console e li rimuove dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039489"
---
# <a name="readconsoleinput-function"></a>ReadConsoleInput (funzione)

Legge i dati da un buffer di input della console e li rimuove dal buffer.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a>Parametri

*hConsoleInput* \[ in\]  
Handle per il buffer di input della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ out\]  
Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.

*nLength* \[ in\]  
Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.

*lpNumberOfEventsRead* \[ out\]  
Puntatore a una variabile che riceve il numero di record di input letti.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Se il numero di record richiesti nel parametro *nLength* supera il numero di record disponibili nel buffer, viene letto il numero disponibile. La funzione non restituisce alcun risultato finché non viene letto almeno un record di input.

Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](https://msdn.microsoft.com/library/windows/desktop/ms687069) per determinare quando l'input della console non è stato letto. Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.

Per determinare il numero di record di input non letti nel buffer di input di una console, usare la funzione [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) . Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) . Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **ReadConsoleInputW** (Unicode) e **ReadConsoleInputA** (ANSI) |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**RECORD di INPUT \_**](input-record-str.md)

[Funzioni di input della console di basso livello](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)
