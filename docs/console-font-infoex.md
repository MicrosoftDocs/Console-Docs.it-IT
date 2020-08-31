---
title: Struttura CONSOLE_FONT_INFOEX
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_FONT_INFOEX, che contiene informazioni estese per un tipo di carattere della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060100"
---
# <a name="console_font_infoex-structure"></a>\_Struttura INFOEX del tipo di carattere della console \_


Contiene informazioni estese per un tipo di carattere della console.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a>Membri
-------

**cbSize**  
Dimensioni, in byte, della struttura. Questo membro deve essere impostato su `sizeof(CONSOLE_FONT_INFOEX)` prima di chiamare [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o avrà esito negativo.

**nFont**  
Indice del tipo di carattere nella tabella dei tipi di carattere della console del sistema.

**dwFontSize**  
Struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche. Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.

**FontFamily**  
Il passo del carattere e la famiglia. Per informazioni sui valori possibili per questo membro, vedere la descrizione del membro **tmPitchAndFamily** della struttura [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .

**SpessoreCarattere**  
Spessore del carattere. Il peso può variare da 100 a 1000, in multipli di 100. Ad esempio, il peso normale è 400, mentre 700 è in grassetto.

**Contemplato**  
Nome del carattere tipografico, ad esempio Courier o Arial.

<a name="remarks"></a>Osservazioni
-------

Per ottenere la dimensione del tipo di carattere, passare l'indice del tipo di carattere alla funzione [**GetConsoleFontSize**](getconsolefontsize.md) .

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
<td>Wincon. h (include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)

 

 




