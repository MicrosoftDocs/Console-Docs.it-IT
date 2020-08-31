---
title: GetConsoleOutputCP (funzione)
description: Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059756"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP (funzione)


Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante. Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.

<a name="syntax"></a>Sintassi
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a>Parametri
----------

Questa funzione non ha parametri.

<a name="return-value"></a>Valore restituito
------------

Il valore restituito è un codice che identifica la tabella codici. Per un elenco di identificatori, vedere [identificatori della tabella codici](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Se il valore restituito è zero, la funzione ha avuto esito negativo. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi. Per recuperare altre informazioni su una tabella codici, incluso il relativo nome, vedere la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .

Per impostare la tabella codici di output di una console, usare la funzione [**SetConsoleOutputCP**](setconsoleoutputcp.md) . Per impostare ed eseguire una query sulla tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .

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


[Tabelle codici della console](console-code-pages.md)

[Funzioni console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

 

 




