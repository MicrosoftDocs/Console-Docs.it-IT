---
title: GetConsoleDisplayMode (funzione)
description: Vedere informazioni di riferimento sulla funzione GetConsoleDisplayMode, che consente di recuperare la modalità di visualizzazione della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059812"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode (funzione)


Recupera la modalità di visualizzazione della console corrente.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a>Parametri
----------

*lpModeFlags* \[ out\]  
Modalità di visualizzazione della console. Il parametro può essere costituito da uno o più dei valori seguenti.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</td>
<td><p>Console a schermo intero. La console è in questa modalità non appena la finestra è ingrandita. A questo punto, la transizione alla modalità schermo intero può comunque avere esito negativo.</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</td>
<td><p>Console a schermo intero che comunica direttamente con l'hardware del video. Questa modalità viene impostata dopo che la console è in modalità <strong>CONSOLE_FULLSCREEN</strong> per indicare che la transizione alla modalità schermo intero è stata completata.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Per compilare un'applicazione che usa questa funzione, definire ** \_ Win32 \_ WinNT** come 0x0500 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows Server 2003 [solo app desktop]</p></td>
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

[Modalità console](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

 

 




