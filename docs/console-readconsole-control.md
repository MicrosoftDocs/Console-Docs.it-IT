---
title: Struttura CONSOLE_READCONSOLE_CONTROL
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_READCONSOLE_CONTROL, che contiene informazioni per un'operazione di lettura della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039189"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="1ff3c-104">\_Struttura di \_ controllo READCONSOLE console</span><span class="sxs-lookup"><span data-stu-id="1ff3c-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>

<span data-ttu-id="1ff3c-105">Contiene informazioni per un'operazione di lettura della console.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-105">Contains information for a console read operation.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ff3c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1ff3c-106">Syntax</span></span>

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a><span data-ttu-id="1ff3c-107">Members</span><span class="sxs-lookup"><span data-stu-id="1ff3c-107">Members</span></span>

<span data-ttu-id="1ff3c-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="1ff3c-108">**nLength**</span></span>  
<span data-ttu-id="1ff3c-109">Dimensione della struttura.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-109">The size of the structure.</span></span> <span data-ttu-id="1ff3c-110">Impostare questo membro su `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="1ff3c-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="1ff3c-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="1ff3c-111">**nInitialChars**</span></span>  
<span data-ttu-id="1ff3c-112">Numero di caratteri da ignorare (e di conseguenza conservati) prima di scrivere un nuovo input di lettura nel buffer passato alla funzione [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="1ff3c-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="1ff3c-113">Questo valore deve essere minore del parametro *nNumberOfCharsToRead* della funzione **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="1ff3c-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="1ff3c-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="1ff3c-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="1ff3c-115">Maschera che specifica i caratteri di controllo tra `0x00` e `0x1F` da usare per segnalare che la lettura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-115">A mask specifying which control characters between `0x00` and `0x1F` should be used to signal that the read is complete.</span></span> <span data-ttu-id="1ff3c-116">Ogni bit corrisponde a un carattere con il bit meno significativo che corrisponde a `0x00` o `NUL` e il bit più significativo corrispondente a `0x1F` o `US` .</span><span class="sxs-lookup"><span data-stu-id="1ff3c-116">Each bit corresponds to a character with the least significant bit corresponding to `0x00` or `NUL` and the most significant bit corresponding to `0x1F` or `US`.</span></span> <span data-ttu-id="1ff3c-117">È possibile specificare più bit (caratteri di controllo).</span><span class="sxs-lookup"><span data-stu-id="1ff3c-117">Multiple bits (control characters) can be specified.</span></span>

<span data-ttu-id="1ff3c-118">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="1ff3c-118">**dwControlKeyState**</span></span>  
<span data-ttu-id="1ff3c-119">Stato delle chiavi del controllo.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-119">The state of the control keys.</span></span> <span data-ttu-id="1ff3c-120">Il membro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-120">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="1ff3c-121">Valore</span><span class="sxs-lookup"><span data-stu-id="1ff3c-121">Value</span></span> | <span data-ttu-id="1ff3c-122">Significato</span><span class="sxs-lookup"><span data-stu-id="1ff3c-122">Meaning</span></span> |
|-|-|
| <span data-ttu-id="1ff3c-123">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="1ff3c-123">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="1ff3c-124">La luce del blocco è attiva.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-124">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="1ff3c-125">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="1ff3c-125">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="1ff3c-126">La chiave è stata migliorata.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-126">The key is enhanced.</span></span> <span data-ttu-id="1ff3c-127">Vedere la [sezione Osservazioni](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="1ff3c-127">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="1ff3c-128">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="1ff3c-128">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="1ff3c-129">Viene premuto il tasto ALT sinistro.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-129">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="1ff3c-130">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="1ff3c-130">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="1ff3c-131">Viene premuto il tasto CTRL sinistro.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-131">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="1ff3c-132">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="1ff3c-132">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="1ff3c-133">Il BLOC NUM Light è on.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-133">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="1ff3c-134">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="1ff3c-134">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="1ff3c-135">Viene premuto il tasto ALT destro.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-135">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="1ff3c-136">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="1ff3c-136">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="1ff3c-137">Viene premuto il tasto CTRL destro.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-137">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="1ff3c-138">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="1ff3c-138">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="1ff3c-139">La luce del blocco di scorrimento è attiva.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-139">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="1ff3c-140">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="1ff3c-140">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="1ff3c-141">Il tasto MAIUSC è premuto.</span><span class="sxs-lookup"><span data-stu-id="1ff3c-141">The SHIFT key is pressed.</span></span> |

## <a name="requirements"></a><span data-ttu-id="1ff3c-142">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ff3c-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1ff3c-143">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1ff3c-143">Minimum supported client</span></span> | <span data-ttu-id="1ff3c-144">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="1ff3c-144">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ff3c-145">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1ff3c-145">Minimum supported server</span></span> | <span data-ttu-id="1ff3c-146">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="1ff3c-146">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ff3c-147">Intestazione</span><span class="sxs-lookup"><span data-stu-id="1ff3c-147">Header</span></span> | <span data-ttu-id="1ff3c-148">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1ff3c-148">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ff3c-149">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1ff3c-149">See also</span></span>

[<span data-ttu-id="1ff3c-150">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="1ff3c-150">**ReadConsole**</span></span>](readconsole.md)
