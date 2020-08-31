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
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060180"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole (funzione)


Chiude un pseudoconsole dall'handle specificato.

<a name="syntax"></a>Sintassi
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a>Parametri
----------

*hPC* \[ in\]  
Handle per un psuedoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).

<a name="return-value"></a>Valore restituito
------------

*nessuna*

<a name="remarks"></a>Osservazioni
-------

Alla chiusura di un pseudoconsole, verranno terminate anche le applicazioni client associate alla sessione.

`hOutput`Quando viene chiamata questa API, un frame finale disegnato può arrivare dal pseudoconsole. Si prevede che il chiamante svuoterà queste informazioni dal buffer del canale di comunicazione e le presenti o lo eliminerà. Se il buffer non viene svuotato, la chiamata di chiusura resta in attesa per un periodo illimitato fino a quando non viene svuotata o i canali di comunicazione vengono interrotti in altro modo.

<a name="requirements"></a>Requisiti
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimo supportato</p></td>
<td><p>Windows 10 1809 [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows Server 2019 [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ConsoleApi. h (tramite wincon. h, Includi Windows. h)</td>
</tr>
<tr class="even">
<td><p>Libreria</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
