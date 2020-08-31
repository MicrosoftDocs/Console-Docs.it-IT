---
title: GetLargestConsoleWindowSize (funzione)
description: Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059689"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize (funzione)


Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.

<a name="syntax"></a>Sintassi
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che specifica il numero di colonne di celle di tipo carattere (membro**X** ) e le righe (membro**Y** ) nella finestra della console più grande possibile. In caso contrario, i membri della struttura sono pari a zero.

Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

La funzione non prende in considerazione le dimensioni del buffer dello schermo della console, il che significa che le dimensioni della finestra restituite possono essere maggiori delle dimensioni del buffer dello schermo della console. La funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) può essere usata per determinare le dimensioni massime della finestra della console, date le dimensioni correnti del buffer dello schermo, il tipo di carattere corrente e le dimensioni di visualizzazione.

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
<td>ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</td>
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

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)

 

 




