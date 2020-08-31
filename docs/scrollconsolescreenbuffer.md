---
title: ScrollConsoleScreenBuffer (funzione)
description: Vedere informazioni di riferimento sulla funzione ScrollConsoleScreenBuffer, che consente di spostare un blocco di dati in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060337"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer (funzione)


Sposta un blocco di dati in un buffer dello schermo. Gli effetti dello spostamento possono essere limitati specificando un rettangolo di ritaglio, in modo che il contenuto del buffer dello schermo della console all'esterno del rettangolo di ritaglio non sia modificato.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpScrollRectangle* \[ in\]  
Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console da spostare.

*lpClipRectangle* \[ in, facoltativo\]  
Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console interessato dallo scorrimento. Questo puntatore può essere **null**.

*dwDestinationOrigin* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica l'angolo superiore sinistro della nuova posizione del contenuto di *lpScrollRectangle* , in caratteri.

*lpFill* \[ in\]  
Puntatore a una struttura [**di \_ informazioni char**](char-info-str.md) che specifica gli attributi di caratteri e colori da utilizzare per riempire le celle all'interno dell'intersezione tra *lpScrollRectangle* e *lpClipRectangle* che sono stati lasciati vuoti come risultato dello spostamento.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

**ScrollConsoleScreenBuffer** copia il contenuto di un'area rettangolare di un buffer dello schermo, specificato dal parametro *lpScrollRectangle* , in un'altra area del buffer dello schermo della console. Il rettangolo di destinazione ha le stesse dimensioni del rettangolo *lpScrollRectangle* con l'angolo superiore sinistro in corrispondenza delle coordinate specificate dal parametro *dwDestinationOrigin* . Le parti di *lpScrollRectangle* che non si sovrappongono al rettangolo di destinazione vengono compilate con gli attributi di carattere e colore specificati dal parametro *lpFill* .

Il rettangolo di ritaglio si applica alle modifiche apportate sia nel rettangolo *lpScrollRectangle* che nel rettangolo di destinazione. Se, ad esempio, il rettangolo di ridimensionamento non include un'area che verrebbe compilata con il contenuto di *lpFill*, il contenuto originale dell'area viene lasciato invariato.

Se le aree di scorrimento o di destinazione si estendono oltre le dimensioni del buffer dello schermo della console, vengono ritagliate. Ad esempio, se *lpScrollRectangle* è l'area contenuta da (0,0) e (19, 19) e *dwDestinationOrigin* è (10, 15), il rettangolo di destinazione è l'area contenuta da (10, 15) e (29, 34). Tuttavia, se il buffer dello schermo della console ha una larghezza di 50 caratteri e 30 caratteri di altezza, il rettangolo di destinazione viene ritagliato in (10, 15) e (29, 29). Anche le modifiche apportate al buffer dello schermo della console vengono ritagliate in base a *lpClipRectangle*, se il parametro specifica una struttura [** \_ Rect di piccole dimensioni**](small-rect-str.md) . Se il rettangolo di ritaglio viene specificato come (0, 0) e (49, 19), vengono effettuate solo le modifiche che si verificano in tale area del buffer dello schermo della console.

Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console. Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema. Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

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
<td><p><strong>ScrollConsoleScreenBufferW</strong> (Unicode) e <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</p></td>
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


[**\_informazioni char**](char-info-str.md)

[Funzioni console](console-functions.md)

[**COORD**](coord-str.md)

[Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**\_Rect piccolo**](small-rect-str.md)

 

 




