---
title: Struttura COORD
description: Definisce le coordinate di una cella di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059940"
---
# <a name="coord-structure"></a>Struttura COORD


Definisce le coordinate di una cella di tipo carattere in un buffer dello schermo della console. L'origine del sistema di coordinate (0, 0) si trova nella parte superiore della cella sinistra del buffer.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a>Membri
-------

**X**  
Il valore della colonna o della coordinata orizzontale. Le unità dipendono dalla chiamata di funzione.

**S**  
Il valore della riga o della coordinata verticale. Le unità dipendono dalla chiamata di funzione.

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
<td>WinConTypes. h (tramite wincon. h, Includi Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[**informazioni sul tipo di carattere della CONSOLE \_ \_**](console-font-info-str.md)

[**\_informazioni sul \_ buffer dello schermo della console \_**](console-screen-buffer-info-str.md)

[**\_informazioni selezione \_ console**](console-selection-info-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**\_record evento \_ mouse**](mouse-event-record-str.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**\_ \_ record dimensioni buffer \_ finestra**](window-buffer-size-record-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 




