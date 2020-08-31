---
title: Struttura FOCUS_EVENT_RECORD
description: Descrive un evento di attivazione in una struttura di record di INPUT della console \_ . Questi eventi vengono usati internamente e devono essere ignorati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059873"
---
# <a name="focus_event_record-structure"></a>Struttura del record dell' \_ evento di attivazione \_


Descrive un evento di attivazione in una struttura di [** \_ record di input**](input-record-str.md) della console. Questi eventi vengono usati internamente e devono essere ignorati.

<a name="syntax"></a>Sintassi
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a>Membri
-------

**bSetFocus**  
Riservato.

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


[**RECORD di INPUT \_**](input-record-str.md)

 

 




