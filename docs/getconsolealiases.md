---
title: GetConsoleAliases (funzione)
description: Recupera tutti gli alias di console definiti per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059817"
---
# <a name="getconsolealiases-function"></a>GetConsoleAliases (funzione)


Recupera tutti gli alias della console definiti per il file eseguibile specificato.

<a name="syntax"></a>Sintassi
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a>Parametri
----------

*lpAliasBuffer* \[ out\]  
Puntatore a un buffer che riceve gli alias.

Il formato dei dati è il seguente: *source1* = *Target1* \\ 0*source2* = *Target2* \\ 0... *Origine dati* = *Destinazione* \\ 0, dove *N* è il numero di alias di console definito.

*AliasBufferLength* \[ in\]  
Dimensioni del buffer a cui punta *lpAliasBuffer*in byte.

*lpExeName* \[ in\]  
File eseguibile di cui devono essere recuperati gli alias.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Per determinare le dimensioni necessarie per il buffer *lpExeName* , usare la funzione [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .

Per compilare un'applicazione che usa questa funzione, definire ** \_ Win32 \_ WinNT** come 0x0501 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Nomi Unicode e ANSI</p></td>
<td><p><strong>GetConsoleAliasesW</strong> (Unicode) e <strong>GetConsoleAliasesA</strong> (ANSI)</p></td>
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


[**AddConsoleAlias**](addconsolealias.md)

[Alias di console](console-aliases.md)

[Funzioni console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasesLength**](getconsolealiaseslength.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




