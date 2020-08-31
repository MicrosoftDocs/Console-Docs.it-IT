---
title: GetConsoleOriginalTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleOriginalTitle, che recupera il titolo originale per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059737"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle (funzione)


Recupera il titolo originale per la finestra della console corrente.

<a name="syntax"></a>Sintassi
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parametri
----------

*lpConsoleTitle* \[ out\]  
Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo originale.

*nSize* \[ in\]  
Dimensioni del buffer *lpConsoleTitle* , in caratteri.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito corrisponde alla lunghezza della stringa copiata nel buffer, in caratteri.

Se il buffer non è abbastanza grande per archiviare il titolo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce un **errore di \_ esito positivo**.

Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce il codice di errore.

<a name="remarks"></a>Osservazioni
-------

Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) . Per recuperare la stringa del titolo corrente, usare la funzione [**GetConsoleTitle**](getconsoletitle.md) .

Per compilare un'applicazione che usa questa funzione, definire ** \_ Win32 \_ WinNT** come 0x0600 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows Vista [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows Server 2008 [solo app desktop]</p></td>
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
<td><p><strong>GetConsoleOriginalTitleW</strong> (Unicode) e <strong>GetConsoleOriginalTitleA</strong> (ANSI)</p></td>
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

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




