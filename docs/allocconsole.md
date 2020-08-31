---
title: AllocConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AllocConsole, che alloca una nuova console per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060244"
---
# <a name="allocconsole-function"></a>AllocConsole (funzione)


Alloca una nuova console per il processo chiamante.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a>Parametri
----------

Questa funzione non ha parametri.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Un processo può essere associato a una sola console, quindi la funzione **AllocConsole** ha esito negativo se il processo chiamante dispone già di una console. Un processo può usare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console corrente, quindi può chiamare **AllocConsole** per creare una nuova console o [**AttachConsole**](attachconsole.md) da connettere a un'altra console.

Se il processo chiamante crea un processo figlio, l'elemento figlio eredita la nuova console.

**AllocConsole** Inizializza l'input standard, l'output standard e gli handle di errore standard per la nuova console. L'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle per il buffer dello schermo della console. Per recuperare questi handle, utilizzare la funzione [**GetStdHandle**](getstdhandle.md) .

Questa funzione viene utilizzata principalmente da un'applicazione GUI (Graphical User Interface) per creare una finestra della console. Le applicazioni GUI vengono inizializzate senza una console. Le applicazioni console vengono inizializzate con una console, a meno che non vengano create come processi scollegati (chiamando la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con il flag di ** \_ processo scollegato** ).

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
<td><p>Windows 2000 Professional [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows 2000 Server [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</td>
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


[Funzioni console](console-functions.md)

[Console](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)

 

 




