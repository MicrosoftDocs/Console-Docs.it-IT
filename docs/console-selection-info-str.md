---
title: Struttura CONSOLE_SELECTION_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_SELECTION_INFO, che contiene informazioni per la selezione di una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060001"
---
# <a name="console_selection_info-structure"></a>Struttura delle informazioni di \_ selezione della console \_


Contiene informazioni per la selezione di una console.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a>Membri
-------

**dwFlags**  
Indicatore di selezione. Il membro può essere costituito da uno o più dei valori seguenti.

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
<td><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</td>
<td><p>Il mouse è inattivo</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</td>
<td><p>Selezione con il mouse</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</td>
<td><p>Nessuna selezione</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</td>
<td><p>Selezione iniziata</p></td>
</tr>
<tr class="odd">
<td><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</td>
<td><p>Il rettangolo di selezione non è vuoto</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwSelectionAnchor**  
Struttura [**Coord**](coord-str.md) che specifica l'ancoraggio di selezione, in caratteri.

**srSelection**  
Struttura [** \_ Rect piccola**](small-rect-str.md) che specifica il rettangolo di selezione.

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
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[**COORD**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**\_Rect piccolo**](small-rect-str.md)

 

 




