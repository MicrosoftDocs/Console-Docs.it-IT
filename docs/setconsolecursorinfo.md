---
title: SetConsoleCursorInfo (funzione)
description: Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039399"
---
# <a name="setconsolecursorinfo-function"></a>SetConsoleCursorInfo (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpConsoleCursorInfo* \[ in\]  
Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che fornisce le nuove specifiche per il cursore del buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Quando il cursore di un buffer dello schermo è visibile, l'aspetto può variare, a partire dal riempimento completo di una cella di tipo carattere per essere visualizzata come linea orizzontale nella parte inferiore della cella. Il membro **dwSize** della struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) specifica la percentuale di una cella di tipo carattere compilata dal cursore. Se questo membro è minore di 1 o maggiore di 100, **SetConsoleCursorInfo** ha esito negativo.

> [!TIP]
> Questa API dispone di un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nella sezione **[visibilità del cursore](console-virtual-terminal-sequences.md#cursor-visibility)** con le `^[[?25h` sequenze e `^[[?25l` . 

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

[**\_informazioni cursore \_ console**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)
