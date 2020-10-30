---
title: GetNumberOfConsoleMouseButtons (funzione)
description: Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037829"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a>Parametri

*lpNumberOfMouseButtons* \[ out\]  
Puntatore a una variabile che riceve il numero di pulsanti del mouse.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Quando una console riceve l'input del mouse, una struttura di [**\_ record di input**](input-record-str.md) contenente una struttura di [**\_ \_ record di eventi del mouse**](mouse-event-record-str.md) viene inserita nel buffer di input della console. Il membro **dwButtonState** del **\_ \_ record dell'evento del mouse** presenta un bit che indica lo stato di ogni pulsante del mouse. Il bit è 1 se il pulsante è inattivo e 0 se il pulsante è attivo. Per determinare il numero di bit significativi, utilizzare **GetNumberOfConsoleMouseButtons** .

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** . Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi. Questo stato è pertinente solo per l'utente locale, la sessione e il contesto dei privilegi. Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[Buffer di input della console](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**RECORD di INPUT \_**](input-record-str.md)

[**\_record evento \_ mouse**](mouse-event-record-str.md)
