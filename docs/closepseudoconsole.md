---
title: ClosePseudoConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione ClosePseudoConsole, che chiude un pseudoconsole dall'handle specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037289"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="2ebfc-104">ClosePseudoConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="2ebfc-104">ClosePseudoConsole function</span></span>

<span data-ttu-id="2ebfc-105">Chiude un pseudoconsole dall'handle specificato.</span><span class="sxs-lookup"><span data-stu-id="2ebfc-105">Closes a pseudoconsole from the given handle.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ebfc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2ebfc-106">Syntax</span></span>

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a><span data-ttu-id="2ebfc-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="2ebfc-107">Parameters</span></span>

<span data-ttu-id="2ebfc-108">*hPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2ebfc-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="2ebfc-109">Handle per un pseudoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="2ebfc-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="2ebfc-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2ebfc-110">Return value</span></span>

<span data-ttu-id="2ebfc-111">*nessuna*</span><span class="sxs-lookup"><span data-stu-id="2ebfc-111">*none*</span></span>

## <a name="remarks"></a><span data-ttu-id="2ebfc-112">Commenti</span><span class="sxs-lookup"><span data-stu-id="2ebfc-112">Remarks</span></span>

<span data-ttu-id="2ebfc-113">Alla chiusura di un pseudoconsole, verranno terminate anche le applicazioni client associate alla sessione.</span><span class="sxs-lookup"><span data-stu-id="2ebfc-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="2ebfc-114">Un frame finale disegnato può arrivare all' `hOutput` handle fornito in origine a [CreatePsuedoConsole](createpseudoconsole.md) quando viene chiamata l'API.</span><span class="sxs-lookup"><span data-stu-id="2ebfc-114">A final painted frame may arrive on the `hOutput` handle originally provided to [CreatePsuedoConsole](createpseudoconsole.md) when this API is called.</span></span> <span data-ttu-id="2ebfc-115">Si prevede che il chiamante svuoterà queste informazioni dal buffer del canale di comunicazione e le presenti o lo eliminerà.</span><span class="sxs-lookup"><span data-stu-id="2ebfc-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="2ebfc-116">Se il buffer non viene svuotato, la chiamata di chiusura resta in attesa per un periodo illimitato fino a quando non viene svuotata o i canali di comunicazione vengono interrotti in altro modo.</span><span class="sxs-lookup"><span data-stu-id="2ebfc-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ebfc-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2ebfc-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2ebfc-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2ebfc-118">Minimum supported client</span></span> | <span data-ttu-id="2ebfc-119">Aggiornamento di Windows 10 ottobre 2018 (versione 1809) \[ solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="2ebfc-119">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ebfc-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2ebfc-120">Minimum supported server</span></span> | <span data-ttu-id="2ebfc-121">\[Solo app desktop Windows Server 2019\]</span><span class="sxs-lookup"><span data-stu-id="2ebfc-121">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ebfc-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2ebfc-122">Header</span></span> | <span data-ttu-id="2ebfc-123">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2ebfc-123">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2ebfc-124">Libreria</span><span class="sxs-lookup"><span data-stu-id="2ebfc-124">Library</span></span> | <span data-ttu-id="2ebfc-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2ebfc-125">Kernel32.lib</span></span> |
| <span data-ttu-id="2ebfc-126">DLL</span><span class="sxs-lookup"><span data-stu-id="2ebfc-126">DLL</span></span> | <span data-ttu-id="2ebfc-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2ebfc-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="2ebfc-128">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2ebfc-128">See also</span></span>

[<span data-ttu-id="2ebfc-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="2ebfc-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="2ebfc-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="2ebfc-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="2ebfc-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="2ebfc-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
