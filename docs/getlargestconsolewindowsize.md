---
title: GetLargestConsoleWindowSize (funzione)
description: Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3fe4ddf83f25f1951defed52eaf8fea18e1ff2dc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358871"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.

## <a name="syntax"></a>Sintassi

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che specifica il numero di colonne di celle di tipo carattere (membro **X** ) e le righe (membro **Y** ) nella finestra della console più grande possibile. In caso contrario, i membri della struttura sono pari a zero.

Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

La funzione non prende in considerazione le dimensioni del buffer dello schermo della console, il che significa che le dimensioni della finestra restituite possono essere maggiori delle dimensioni del buffer dello schermo della console. La funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) può essere usata per determinare le dimensioni massime della finestra della console, date le dimensioni correnti del buffer dello schermo, il tipo di carattere corrente e le dimensioni di visualizzazione.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)