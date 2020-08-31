---
title: GetConsoleTitle (funzione)
description: Recupera il titolo e le dimensioni del titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059700"
---
# <a name="getconsoletitle-function"></a>GetConsoleTitle (funzione)


Recupera il titolo per la finestra della console corrente.

<a name="syntax"></a>Sintassi
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parametri
----------

*lpConsoleTitle* \[ out\]  
Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo. Se il buffer è troppo piccolo per archiviare il titolo, la funzione archivia il numero di caratteri del titolo che rientrerà nel buffer, terminando con un carattere di terminazione null.

*nSize* \[ in\]  
Dimensioni del buffer a cui punta il parametro *lpConsoleTitle* , in caratteri.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è la lunghezza del titolo della finestra della console, in caratteri.

Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce il codice di errore.

<a name="remarks"></a>Osservazioni
-------

Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) . Per recuperare la stringa del titolo originale, usare la funzione [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .

Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console. Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema. Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [**SetConsoleTitle**](setconsoletitle.md).

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
<td><p>Nomi Unicode e ANSI</p></td>
<td><p><strong>GetConsoleTitleW</strong> (Unicode) e <strong>GetConsoleTitleA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
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

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




