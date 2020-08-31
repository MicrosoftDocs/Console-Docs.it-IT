---
title: Struttura CONSOLE_READCONSOLE_CONTROL
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_READCONSOLE_CONTROL, che contiene informazioni per un'operazione di lettura della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060076"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="7db88-104">\_Struttura di \_ controllo READCONSOLE console</span><span class="sxs-lookup"><span data-stu-id="7db88-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>


<span data-ttu-id="7db88-105">Contiene informazioni per un'operazione di lettura della console.</span><span class="sxs-lookup"><span data-stu-id="7db88-105">Contains information for a console read operation.</span></span>

<a name="syntax"></a><span data-ttu-id="7db88-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7db88-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a><span data-ttu-id="7db88-107">Membri</span><span class="sxs-lookup"><span data-stu-id="7db88-107">Members</span></span>
-------

<span data-ttu-id="7db88-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="7db88-108">**nLength**</span></span>  
<span data-ttu-id="7db88-109">Dimensione della struttura.</span><span class="sxs-lookup"><span data-stu-id="7db88-109">The size of the structure.</span></span> <span data-ttu-id="7db88-110">Impostare questo membro su `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="7db88-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="7db88-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="7db88-111">**nInitialChars**</span></span>  
<span data-ttu-id="7db88-112">Numero di caratteri da ignorare (e di conseguenza conservati) prima di scrivere un nuovo input di lettura nel buffer passato alla funzione [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="7db88-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="7db88-113">Questo valore deve essere minore del parametro *nNumberOfCharsToRead* della funzione **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="7db88-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="7db88-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="7db88-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="7db88-115">Carattere di controllo definito dall'utente usato per segnalare che la lettura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="7db88-115">A user-defined control character used to signal that the read is complete.</span></span>

<span data-ttu-id="7db88-116">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="7db88-116">**dwControlKeyState**</span></span>  
<span data-ttu-id="7db88-117">Stato delle chiavi del controllo.</span><span class="sxs-lookup"><span data-stu-id="7db88-117">The state of the control keys.</span></span> <span data-ttu-id="7db88-118">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="7db88-118">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="7db88-119">valore</span><span class="sxs-lookup"><span data-stu-id="7db88-119">Value</span></span></th>
<th><span data-ttu-id="7db88-120">Significato</span><span class="sxs-lookup"><span data-stu-id="7db88-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="7db88-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="7db88-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="7db88-122">La luce del blocco è attiva.</span><span class="sxs-lookup"><span data-stu-id="7db88-122">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7db88-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="7db88-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="7db88-124">La chiave è stata migliorata.</span><span class="sxs-lookup"><span data-stu-id="7db88-124">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7db88-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="7db88-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="7db88-126">Viene premuto il tasto ALT sinistro.</span><span class="sxs-lookup"><span data-stu-id="7db88-126">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7db88-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="7db88-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="7db88-128">Viene premuto il tasto CTRL sinistro.</span><span class="sxs-lookup"><span data-stu-id="7db88-128">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7db88-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="7db88-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="7db88-130">Il BLOC NUM Light è on.</span><span class="sxs-lookup"><span data-stu-id="7db88-130">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7db88-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="7db88-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="7db88-132">Viene premuto il tasto ALT destro.</span><span class="sxs-lookup"><span data-stu-id="7db88-132">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7db88-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="7db88-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="7db88-134">Viene premuto il tasto CTRL destro.</span><span class="sxs-lookup"><span data-stu-id="7db88-134">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7db88-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="7db88-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="7db88-136">La luce del blocco di scorrimento è attiva.</span><span class="sxs-lookup"><span data-stu-id="7db88-136">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="7db88-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="7db88-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="7db88-138">Il tasto MAIUSC è premuto.</span><span class="sxs-lookup"><span data-stu-id="7db88-138">The SHIFT key is pressed.</span></span></p></td>
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
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="7db88-139">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7db88-139">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7db88-140">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7db88-140">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7db88-141">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="7db88-141">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7db88-142">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7db88-142">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7db88-143">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="7db88-143">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7db88-144">Intestazione</span><span class="sxs-lookup"><span data-stu-id="7db88-144">Header</span></span></p></td>
<td><span data-ttu-id="7db88-145">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7db88-145">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7db88-146"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7db88-146"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7db88-147">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="7db88-147">**ReadConsole**</span></span>](readconsole.md)

 

 




