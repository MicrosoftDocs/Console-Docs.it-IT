---
title: FillConsoleOutputCharacter (funzione)
description: Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059884"
---
# <a name="fillconsoleoutputcharacter-function"></a>FillConsoleOutputCharacter (funzione)


Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*cCharacter* \[ in\]  
Carattere da scrivere nel buffer dello schermo della console.

*nLength* \[ in\]  
Numero di celle di caratteri in cui deve essere scritto il carattere.

*dwWriteCoord* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella in cui deve essere scritto il carattere.

*lpNumberOfCharsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti nel buffer dello schermo della console.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Se il numero di caratteri in cui scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva. Se il numero di caratteri in cui scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.

I valori di attributo nelle posizioni scritte non vengono modificati.

Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console. Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema. Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .

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
<td><p><strong>FillConsoleOutputCharacterW</strong> (Unicode) e <strong>FillConsoleOutputCharacterA</strong> (ANSI)</p></td>
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

[**COORD**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




