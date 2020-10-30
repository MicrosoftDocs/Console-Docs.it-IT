---
title: ResizePseudoConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione ResizePseudoConsole, che ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037539"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole (funzione)

Ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.

## <a name="syntax"></a>Sintassi

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a>Parametri

*hPC* \[ in\]  
Handle per un pseudoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).

*dimensioni* \[ in\]  
Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati per il buffer interno di questo pseudoconsole.

## <a name="return-value"></a>Valore restituito

Tipo: **HRESULT**

Se questo metodo ha esito positivo, restituisce **S_OK** . In caso contrario, restituisce un codice di errore **HRESULT** .

## <a name="remarks"></a>Commenti

Questa funzione può ridimensionare i buffer interni della sessione pseudoconsole in modo che corrispondano alla dimensione della finestra o del buffer utilizzata per la visualizzazione nel terminale finale. In questo modo si assicura che le applicazioni associate Command-Line Interface (cui) che usano le [funzioni della console](console-functions.md) per la comunicazione abbiano le dimensioni corrette restituite nelle chiamate.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Aggiornamento di Windows 10 ottobre 2018 (versione 1809) \[ solo app desktop\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2019\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
