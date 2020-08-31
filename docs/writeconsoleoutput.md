---
title: WriteConsoleOutput (funzione)
description: Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059564"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput (funzione)


Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console. I dati da scrivere vengono ricavati da un blocco rettangolare di dimensioni corrispondenti in una posizione specificata nel buffer di origine.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Dati da scrivere nel buffer dello schermo della console. Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [** \_ informazioni char**](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .

*dwBufferSize* \[ in\]  
Dimensioni del buffer a cui punta il parametro *lpBuffer* , in celle di tipo carattere. Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.

*dwBufferCoord* \[ in\]  
Coordinate della cella superiore sinistra nel buffer a cui punta il parametro *lpBuffer* . Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.

*lpWriteRegion* \[ in uscita\]  
Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) . In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console in cui scrivere. Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

**WriteConsoleOutput** considera il buffer di origine e il buffer dello schermo di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere). Il rettangolo a cui punta il parametro *lpWriteRegion* specifica le dimensioni e la posizione del blocco in cui scrivere nel buffer dello schermo della console. Un rettangolo con le stesse dimensioni si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* . I dati delle celle presenti nell'intersezione tra il rettangolo e il rettangolo del buffer di origine (le cui dimensioni sono specificate dal parametro *dwBufferSize* ) vengono scritti nel rettangolo di destinazione.

Le celle nel rettangolo di destinazione il cui percorso di origine corrispondente si trova al di fuori dei limiti del rettangolo del buffer di origine non vengono influenzate dall'operazione di scrittura. In altre parole, queste sono le celle per le quali non sono disponibili dati da scrivere.

Prima della restituzione di **WriteConsoleOutput** , imposta i membri di *lpWriteRegion* sul rettangolo del buffer dello schermo effettivo interessato dall'operazione di scrittura. Questo rettangolo riflette le celle del rettangolo di destinazione per cui esiste una cella corrispondente nel buffer di origine, perché **WriteConsoleOutput** Ritaglia le dimensioni del rettangolo di destinazione ai limiti del buffer dello schermo della console.

Se il rettangolo specificato da *lpWriteRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di origine, non viene scritto alcun dato. In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpWriteRegion* , in modo tale che il membro **destro** sia minore della **sinistra**o che il membro **inferiore** sia minore della **parte superiore**. Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

**WriteConsoleOutput** non ha alcun effetto sulla posizione del cursore.

Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console. Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema. Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).

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
<td><p><strong>WriteConsoleOutputW</strong> (Unicode) e <strong>WriteConsoleOutputA</strong> (ANSI)</p></td>
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

[**\_informazioni char**](char-info-str.md)

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**\_Rect piccolo**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




