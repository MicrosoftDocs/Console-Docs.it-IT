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
# <a name="console-winevents"></a><span data-ttu-id="6e3bc-105">WinEvents console</span><span class="sxs-lookup"><span data-stu-id="6e3bc-105">Console WinEvents</span></span>


<span data-ttu-id="6e3bc-106">Le costanti di evento seguenti vengono usate nel parametro *Event* della funzione di callback [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="6e3bc-106">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="6e3bc-107">Per ulteriori informazioni, vedere [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="6e3bc-107">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="6e3bc-108">Costante/valore</span><span class="sxs-lookup"><span data-stu-id="6e3bc-108">Constant/value</span></span></th>
<th><span data-ttu-id="6e3bc-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6e3bc-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="6e3bc-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span><span class="sxs-lookup"><span data-stu-id="6e3bc-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span></span></td>
<td><p><span data-ttu-id="6e3bc-111">Il punto di inserimento della console è stato spostato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-111">The console caret has moved.</span></span> <span data-ttu-id="6e3bc-112">Il parametro <em>idObject</em> è uno o più dei valori seguenti: <strong>CONSOLE_CARET_SELECTION</strong> o <strong>CONSOLE_CARET_VISIBLE</strong>.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-112">The <em>idObject</em> parameter is one or more of the following values: <strong>CONSOLE_CARET_SELECTION</strong> or <strong>CONSOLE_CARET_VISIBLE</strong>.</span></span></p>
<p><span data-ttu-id="6e3bc-113">Il parametro <em>idChild</em> è una struttura <strong><a href="https://docs.microsoft.com/windows/console/coord-str">Coord</a></strong> che specifica la posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-113">The <em>idChild</em> parameter is a <strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong> structure that specifies the cursor's current position.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6e3bc-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span><span class="sxs-lookup"><span data-stu-id="6e3bc-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span></span></td>
<td><p><span data-ttu-id="6e3bc-115">Un processo console è stato terminato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-115">A console process has exited.</span></span> <span data-ttu-id="6e3bc-116">Il parametro <em>idObject</em> contiene l'identificatore di processo del processo terminato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-116">The <em>idObject</em> parameter contains the process identifier of the terminated process.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6e3bc-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span><span class="sxs-lookup"><span data-stu-id="6e3bc-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span></span></td>
<td><p><span data-ttu-id="6e3bc-118">Il layout della console è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-118">The console layout has changed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6e3bc-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span><span class="sxs-lookup"><span data-stu-id="6e3bc-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span></span></td>
<td><p><span data-ttu-id="6e3bc-120">È stato avviato un nuovo processo console.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-120">A new console process has started.</span></span> <span data-ttu-id="6e3bc-121">Il parametro <em>idObject</em> contiene l'identificatore di processo del processo appena creato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-121">The <em>idObject</em> parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="6e3bc-122">Se l'applicazione è un'applicazione a 16 bit, il parametro <em>idChild</em> è <strong>CONSOLE_APPLICATION_16BIT</strong> e <em>idObject</em> è l'identificatore del processo della sessione NTVDM associata alla console.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-122">If the application is a 16-bit application, the <em>idChild</em> parameter is <strong>CONSOLE_APPLICATION_16BIT</strong> and <em>idObject</em> is the process identifier of the NTVDM session associated with the console.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6e3bc-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span><span class="sxs-lookup"><span data-stu-id="6e3bc-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span></span></td>
<td><p><span data-ttu-id="6e3bc-124">Più di un carattere è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-124">More than one character has changed.</span></span> <span data-ttu-id="6e3bc-125">Il parametro <em>idObject</em> è una struttura <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>Coord</strong></a> che specifica l'inizio dell'area modificata.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-125">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the start of the changed region.</span></span> <span data-ttu-id="6e3bc-126">Il parametro <em>idChild</em> è una struttura <strong>Coord</strong> che specifica la fine dell'area modificata.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-126">The <em>idChild</em> parameter is a <strong>COORD</strong> structure that specifies the end of the changed region.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6e3bc-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span><span class="sxs-lookup"><span data-stu-id="6e3bc-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span></span></td>
<td><p><span data-ttu-id="6e3bc-128">Lo scorrimento della console è stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-128">The console has scrolled.</span></span> <span data-ttu-id="6e3bc-129">Il parametro <em>idObject</em> è la distanza orizzontale con cui è stato eseguito lo scorrimento della console.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-129">The <em>idObject</em> parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="6e3bc-130">Il parametro <em>idChild</em> è la distanza verticale con cui è stato eseguito lo scorrimento della console.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-130">The <em>idChild</em> parameter is the vertical distance the console has scrolled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6e3bc-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span><span class="sxs-lookup"><span data-stu-id="6e3bc-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span></span></td>
<td><p><span data-ttu-id="6e3bc-132">Un singolo carattere è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-132">A single character has changed.</span></span> <span data-ttu-id="6e3bc-133">Il parametro <em>idObject</em> è una struttura <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>Coord</strong></a> che specifica il carattere che è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-133">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the character that has changed.</span></span> <span data-ttu-id="6e3bc-134">Il parametro <em>idChild</em> specifica il carattere nella parola bassa e gli <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">attributi carattere</a> nella parola alta.</span><span class="sxs-lookup"><span data-stu-id="6e3bc-134">The <em>idChild</em> parameter specifies the character in the low word and the <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">character attributes</a> in the high word.</span></span></p></td>
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

<a name="requirements"></a><span data-ttu-id="6e3bc-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6e3bc-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6e3bc-136">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e3bc-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6e3bc-137">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6e3bc-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6e3bc-138">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e3bc-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6e3bc-139">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6e3bc-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6e3bc-140">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6e3bc-140">Header</span></span></p></td>
<td><span data-ttu-id="6e3bc-141">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="6e3bc-141">Winuser.h</span></span></td>
</tr>
</tbody>
</table>
