---
title: SetConsoleActiveScreenBuffer (funzione)
description: Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039439"
---
# <a name="setconsoleactivescreenbuffer-function"></a>SetConsoleActiveScreenBuffer (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Una console può avere più buffer dello schermo. **SetConsoleActiveScreenBuffer** determina quale viene visualizzato. È possibile scrivere in un buffer dello schermo inattivo e quindi usare **SetConsoleActiveScreenBuffer** per visualizzare il contenuto del buffer.

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).

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

[Buffer dello schermo della console](console-screen-buffers.md)

[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)
