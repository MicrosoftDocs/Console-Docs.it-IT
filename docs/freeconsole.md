---
title: FreeConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione FreeConsole, che scollega il processo chiamante dalla relativa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059868"
---
# <a name="freeconsole-function"></a>FreeConsole (funzione)


Scollega il processo chiamante dalla relativa console.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI FreeConsole(void);
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

Un processo può essere collegato al massimo da una console. Se il processo chiamante non è già collegato a una console, il codice di errore restituito **è \_ errore \_ parametro non valido** (87).

Un processo può utilizzare la funzione **FreeConsole** per scollegarsi dalla console. Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento. Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**. Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.

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


[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[Funzioni console](console-functions.md)

[Console](consoles.md)

 

 




