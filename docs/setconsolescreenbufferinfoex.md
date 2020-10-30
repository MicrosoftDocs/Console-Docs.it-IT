---
title: SetConsoleScreenBufferInfoEx (funzione)
description: Imposta le informazioni estese sul buffer dello schermo della console specificato sul buffer specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4a83c91a60a26d8e962efdf10b127e97beb70a7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039349"
---
# <a name="setconsolescreenbufferinfoex-function"></a>SetConsoleScreenBufferInfoEx (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta le informazioni estese sul buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfoEx* \[ in\]  
Struttura [**\_ \_ \_ INFOEX buffer dello schermo**](console-screen-buffer-infoex.md) della console che contiene le informazioni sul buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

> [!TIP]
> Questa API ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** parziale. Il **[buffer di posizionamento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)** e **[gli attributi di testo](console-virtual-terminal-sequences.md#text-formatting)** hanno equivalenti di sequenza specifici. La tabella dei colori non è configurabile, ma **[i colori estesi](console-virtual-terminal-sequences.md#extended-colors)** sono disponibili oltre quelli normalmente disponibili tramite le **[funzioni della console](console-functions.md)** . Gli attributi popup non hanno alcun equivalente perché i menu popup sono la responsabilità dell'applicazione client dalla riga di comando nel mondo dei **terminali virtuali** . Infine, le dimensioni della finestra e dello stato schermo intero sono considerati privilegi di proprietà dell'utente nel mondo del **terminale virtuale** e non hanno una sequenza equivalente.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[**\_INFOEX buffer dello schermo della console \_ \_**](console-screen-buffer-infoex.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)
