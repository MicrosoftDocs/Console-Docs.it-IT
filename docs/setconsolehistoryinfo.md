---
title: SetConsoleHistoryInfo (funzione)
description: Imposta le impostazioni della cronologia per la console di Windows del processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bf194e154a06efc32510fe811ab89877e283e142
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059660"
---
# <a name="setconsolehistoryinfo-function"></a>SetConsoleHistoryInfo (funzione)


Imposta le impostazioni della cronologia per la console del processo chiamante.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a>Parametri
----------

*lpConsoleHistoryInfo* \[ in\]  
Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che contiene le impostazioni di cronologia per la console del processo.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo codice di errore su ** \_ accesso \_ negato**.

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

[**\_informazioni cronologia \_ console**](console-history-info.md)

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

 

 




