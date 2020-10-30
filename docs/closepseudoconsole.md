---
title: ClosePseudoConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione ClosePseudoConsole, che chiude un pseudoconsole dall'handle specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037289"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole (funzione)

Chiude un pseudoconsole dall'handle specificato.

## <a name="syntax"></a>Sintassi

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a>Parametri

*hPC* \[ in\]  
Handle per un pseudoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).

## <a name="return-value"></a>Valore restituito

*nessuna*

## <a name="remarks"></a>Commenti

Alla chiusura di un pseudoconsole, verranno terminate anche le applicazioni client associate alla sessione.

Un frame finale disegnato può arrivare all' `hOutput` handle fornito in origine a [CreatePsuedoConsole](createpseudoconsole.md) quando viene chiamata l'API. Si prevede che il chiamante svuoterà queste informazioni dal buffer del canale di comunicazione e le presenti o lo eliminerà. Se il buffer non viene svuotato, la chiamata di chiusura resta in attesa per un periodo illimitato fino a quando non viene svuotata o i canali di comunicazione vengono interrotti in altro modo.

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

[**ResizePseudoConsole**](resizepseudoconsole.md)
