---
title: FillConsoleOutputAttribute (funzione)
description: Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059881"
---
# <a name="fillconsoleoutputattribute-function"></a>FillConsoleOutputAttribute (funzione)


Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*wAttribute* \[ in\]  
Attributi da utilizzare durante la scrittura nel buffer dello schermo della console. Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#_win32_font_attributes).

*nLength* \[ in\]  
Numero di celle di tipo carattere da impostare sugli attributi di colore specificati.

*dwWriteCoord* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella i cui attributi devono essere impostati.

*lpNumberOfAttrsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di celle di tipo carattere i cui attributi sono stati effettivamente impostati.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Se il numero di celle di tipo carattere i cui attributi devono essere impostati si estende oltre la fine della riga specificata nel buffer dello schermo della console, vengono impostate le celle della riga successiva. Se il numero di celle in cui scrivere si estende oltre la fine del buffer dello schermo della console, le celle vengono scritte fino alla fine del buffer dello schermo della console.

I valori di carattere nelle posizioni scritte in non vengono modificati.

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

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

 

 




