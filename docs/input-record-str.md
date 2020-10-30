---
title: Struttura INPUT_RECORD
description: Vedere le informazioni di riferimento sulla struttura INPUT_RECORD, che descrive un evento di input nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038539"
---
# <a name="input_record-structure"></a><span data-ttu-id="8dec8-104">\_Struttura record di input</span><span class="sxs-lookup"><span data-stu-id="8dec8-104">INPUT\_RECORD structure</span></span>

<span data-ttu-id="8dec8-105">Descrive un evento di input nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="8dec8-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="8dec8-106">Questi record possono essere letti dal buffer di input usando la funzione [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) o scritti nel buffer di input usando la funzione [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="8dec8-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="8dec8-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8dec8-107">Syntax</span></span>

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a><span data-ttu-id="8dec8-108">Members</span><span class="sxs-lookup"><span data-stu-id="8dec8-108">Members</span></span>

<span data-ttu-id="8dec8-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="8dec8-109">**EventType**</span></span>  
<span data-ttu-id="8dec8-110">Handle per il tipo di evento di input e il record dell'evento archiviato nel membro dell' **evento** .</span><span class="sxs-lookup"><span data-stu-id="8dec8-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="8dec8-111">Il membro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="8dec8-111">This member can be one of the following values.</span></span>

| <span data-ttu-id="8dec8-112">Valore</span><span class="sxs-lookup"><span data-stu-id="8dec8-112">Value</span></span> | <span data-ttu-id="8dec8-113">Significato</span><span class="sxs-lookup"><span data-stu-id="8dec8-113">Meaning</span></span> |
|-|-|
| <span data-ttu-id="8dec8-114">**FOCUS_EVENT** 0x0010</span><span class="sxs-lookup"><span data-stu-id="8dec8-114">**FOCUS_EVENT** 0x0010</span></span> | <span data-ttu-id="8dec8-115">Il membro dell' **evento** contiene una struttura **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="8dec8-115">The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure.</span></span> <span data-ttu-id="8dec8-116">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="8dec8-116">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="8dec8-117">**KEY_EVENT** 0x0001</span><span class="sxs-lookup"><span data-stu-id="8dec8-117">**KEY_EVENT** 0x0001</span></span> | <span data-ttu-id="8dec8-118">Il membro dell' **evento** contiene una struttura **[KEY_EVENT_RECORD](key-event-record-str.md)** con informazioni su un evento di tastiera.</span><span class="sxs-lookup"><span data-stu-id="8dec8-118">The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event.</span></span> |
| <span data-ttu-id="8dec8-119">**MENU_EVENT** 0x0008</span><span class="sxs-lookup"><span data-stu-id="8dec8-119">**MENU_EVENT** 0x0008</span></span> | <span data-ttu-id="8dec8-120">Il membro dell' **evento** contiene una struttura **[MENU_EVENT_RECORD](menu-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="8dec8-120">The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure.</span></span> <span data-ttu-id="8dec8-121">Questi eventi vengono usati internamente e devono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="8dec8-121">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="8dec8-122">**Mouse_event** 0x0002</span><span class="sxs-lookup"><span data-stu-id="8dec8-122">**MOUSE_EVENT** 0x0002</span></span> | <span data-ttu-id="8dec8-123">Il membro dell' **evento** contiene una struttura di **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** con informazioni su un evento di spostamento o di un pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="8dec8-123">The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event.</span></span> |
| <span data-ttu-id="8dec8-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span><span class="sxs-lookup"><span data-stu-id="8dec8-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span></span> | <span data-ttu-id="8dec8-125">Il membro dell' **evento** contiene una struttura **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** con informazioni sulle nuove dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8dec8-125">The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer.</span></span> |

<span data-ttu-id="8dec8-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="8dec8-126">**Event**</span></span>  
<span data-ttu-id="8dec8-127">Informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="8dec8-127">The event information.</span></span> <span data-ttu-id="8dec8-128">Il formato di questo membro dipende dal tipo di evento specificato dal membro **eventType** .</span><span class="sxs-lookup"><span data-stu-id="8dec8-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

## <a name="examples"></a><span data-ttu-id="8dec8-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="8dec8-129">Examples</span></span>

<span data-ttu-id="8dec8-130">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="8dec8-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="8dec8-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8dec8-131">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8dec8-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8dec8-132">Minimum supported client</span></span> | <span data-ttu-id="8dec8-133">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="8dec8-133">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8dec8-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8dec8-134">Minimum supported server</span></span> | <span data-ttu-id="8dec8-135">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="8dec8-135">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8dec8-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8dec8-136">Header</span></span> | <span data-ttu-id="8dec8-137">WinConTypes. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8dec8-137">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="8dec8-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8dec8-138">See also</span></span>

[<span data-ttu-id="8dec8-139">**\_record evento \_ attivo**</span><span class="sxs-lookup"><span data-stu-id="8dec8-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="8dec8-140">**\_record evento \_ chiave**</span><span class="sxs-lookup"><span data-stu-id="8dec8-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="8dec8-141">**\_record evento \_ menu**</span><span class="sxs-lookup"><span data-stu-id="8dec8-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="8dec8-142">**\_record evento \_ mouse**</span><span class="sxs-lookup"><span data-stu-id="8dec8-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="8dec8-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8dec8-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="8dec8-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8dec8-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="8dec8-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8dec8-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
