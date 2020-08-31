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
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060348"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole (funzione)


Ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.

<a name="syntax"></a>Sintassi
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a>Parametri
----------

*hPC* \[ in\]  
Handle per un psuedoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).

*dimensioni* \[ in\]  
Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati per il buffer interno di questo pseudoconsole. 

<a name="return-value"></a>Valore restituito
------------

Tipo: **HRESULT**

Se questo metodo ha esito positivo, restituisce **S_OK**. In caso contrario, restituisce un codice di errore **HRESULT** .

<a name="remarks"></a>Osservazioni
-------

Questa funzione può ridimensionare i buffer interni della sessione pseudoconsole in modo che corrispondano alla dimensione della finestra o del buffer utilizzata per la visualizzazione nel terminale finale. In questo modo si assicura che le applicazioni con le funzioni di interfaccia della riga di comando collegate che usano le [funzioni della console](console-functions.md) per la comunicazione abbiano le dimensioni corrette restituite nelle chiamate.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
