---
title: WinEvents console
description: Le costanti di evento seguenti vengono usate nel parametro event della funzione di callback WinEventProc. Per ulteriori informazioni, vedere WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059948"
---
# <a name="console-winevents"></a>WinEvents console


Le costanti di evento seguenti vengono usate nel parametro *Event* della funzione di callback [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) . Per ulteriori informazioni, vedere [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Costante/valore</th>
<th>Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</td>
<td><p>Il punto di inserimento della console è stato spostato. Il parametro <em>idObject</em> è uno o più dei valori seguenti: <strong>CONSOLE_CARET_SELECTION</strong> o <strong>CONSOLE_CARET_VISIBLE</strong>.</p>
<p>Il parametro <em>idChild</em> è una struttura <strong><a href="https://docs.microsoft.com/windows/console/coord-str">Coord</a></strong> che specifica la posizione corrente del cursore.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</td>
<td><p>Un processo console è stato terminato. Il parametro <em>idObject</em> contiene l'identificatore di processo del processo terminato.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</td>
<td><p>Il layout della console è stato modificato.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</td>
<td><p>È stato avviato un nuovo processo console. Il parametro <em>idObject</em> contiene l'identificatore di processo del processo appena creato. Se l'applicazione è un'applicazione a 16 bit, il parametro <em>idChild</em> è <strong>CONSOLE_APPLICATION_16BIT</strong> e <em>idObject</em> è l'identificatore del processo della sessione NTVDM associata alla console.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</td>
<td><p>Più di un carattere è stato modificato. Il parametro <em>idObject</em> è una struttura <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>Coord</strong></a> che specifica l'inizio dell'area modificata. Il parametro <em>idChild</em> è una struttura <strong>Coord</strong> che specifica la fine dell'area modificata.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</td>
<td><p>Lo scorrimento della console è stato eseguito. Il parametro <em>idObject</em> è la distanza orizzontale con cui è stato eseguito lo scorrimento della console. Il parametro <em>idChild</em> è la distanza verticale con cui è stato eseguito lo scorrimento della console.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</td>
<td><p>Un singolo carattere è stato modificato. Il parametro <em>idObject</em> è una struttura <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>Coord</strong></a> che specifica il carattere che è stato modificato. Il parametro <em>idChild</em> specifica il carattere nella parola bassa e gli <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">attributi carattere</a> nella parola alta.</p></td>
</tr>
<tr class="even">
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
<td>Winuser. h</td>
</tr>
</tbody>
</table>
