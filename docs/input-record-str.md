---
title: Struttura INPUT_RECORD
description: Vedere le informazioni di riferimento sulla struttura INPUT_RECORD, che descrive un evento di input nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060433"
---
# <a name="input_record-structure"></a><span data-ttu-id="47134-104">\_Struttura record di input</span><span class="sxs-lookup"><span data-stu-id="47134-104">INPUT\_RECORD structure</span></span>


<span data-ttu-id="47134-105">Descrive un evento di input nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="47134-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="47134-106">Questi record possono essere letti dal buffer di input usando la funzione [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) o scritti nel buffer di input usando la funzione [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="47134-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="47134-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="47134-107">Syntax</span></span>
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a><span data-ttu-id="47134-108">Membri</span><span class="sxs-lookup"><span data-stu-id="47134-108">Members</span></span>
-------

<span data-ttu-id="47134-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="47134-109">**EventType**</span></span>  
<span data-ttu-id="47134-110">Handle per il tipo di evento di input e il record dell'evento archiviato nel membro dell' **evento** .</span><span class="sxs-lookup"><span data-stu-id="47134-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="47134-111">Il membro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="47134-111">This member can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="47134-112">valore</span><span class="sxs-lookup"><span data-stu-id="47134-112">Value</span></span></th>
<th><span data-ttu-id="47134-113">Significato</span><span class="sxs-lookup"><span data-stu-id="47134-113">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="47134-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="47134-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="47134-115">Il membro dell' <strong>evento</strong> contiene una struttura <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="47134-115">The <strong>Event</strong> member contains a <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="47134-116">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="47134-116">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="47134-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="47134-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="47134-118">Il membro dell' <strong>evento</strong> contiene una struttura <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> con informazioni su un evento di tastiera.</span><span class="sxs-lookup"><span data-stu-id="47134-118">The <strong>Event</strong> member contains a <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> structure with information about a keyboard event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="47134-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="47134-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="47134-120">Il membro dell' <strong>evento</strong> contiene una struttura <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="47134-120">The <strong>Event</strong> member contains a <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="47134-121">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="47134-121">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="47134-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>Mouse_event</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="47134-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="47134-123">Il membro dell' <strong>evento</strong> contiene una struttura di <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> con informazioni su un evento di spostamento o di un pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="47134-123">The <strong>Event</strong> member contains a <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> structure with information about a mouse movement or button press event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="47134-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="47134-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="47134-125">Il membro dell' <strong>evento</strong> contiene una struttura <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> con informazioni sulle nuove dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="47134-125">The <strong>Event</strong> member contains a <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> structure with information about the new size of the console screen buffer.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="47134-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="47134-126">**Event**</span></span>  
<span data-ttu-id="47134-127">Informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="47134-127">The event information.</span></span> <span data-ttu-id="47134-128">Il formato di questo membro dipende dal tipo di evento specificato dal membro **eventType** .</span><span class="sxs-lookup"><span data-stu-id="47134-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

<a name="examples"></a><span data-ttu-id="47134-129">Esempi</span><span class="sxs-lookup"><span data-stu-id="47134-129">Examples</span></span>
--------

<span data-ttu-id="47134-130">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="47134-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="47134-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="47134-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="47134-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="47134-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="47134-133">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="47134-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="47134-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="47134-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="47134-135">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="47134-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="47134-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="47134-136">Header</span></span></p></td>
<td><span data-ttu-id="47134-137">WinConTypes. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="47134-137">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="47134-138"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="47134-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="47134-139">**\_record evento \_ attivo**</span><span class="sxs-lookup"><span data-stu-id="47134-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="47134-140">**\_record evento \_ chiave**</span><span class="sxs-lookup"><span data-stu-id="47134-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="47134-141">**\_record evento \_ menu**</span><span class="sxs-lookup"><span data-stu-id="47134-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="47134-142">**\_record evento \_ mouse**</span><span class="sxs-lookup"><span data-stu-id="47134-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="47134-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="47134-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="47134-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="47134-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="47134-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="47134-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




