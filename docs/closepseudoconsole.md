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
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060180"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="6e587-104">ClosePseudoConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="6e587-104">ClosePseudoConsole function</span></span>


<span data-ttu-id="6e587-105">Chiude un pseudoconsole dall'handle specificato.</span><span class="sxs-lookup"><span data-stu-id="6e587-105">Closes a pseudoconsole from the given handle.</span></span>

<a name="syntax"></a><span data-ttu-id="6e587-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6e587-106">Syntax</span></span>
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a><span data-ttu-id="6e587-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="6e587-107">Parameters</span></span>
----------

<span data-ttu-id="6e587-108">*hPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6e587-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="6e587-109">Handle per un psuedoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="6e587-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<a name="return-value"></a><span data-ttu-id="6e587-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6e587-110">Return value</span></span>
------------

<span data-ttu-id="6e587-111">*nessuna*</span><span class="sxs-lookup"><span data-stu-id="6e587-111">*none*</span></span>

<a name="remarks"></a><span data-ttu-id="6e587-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6e587-112">Remarks</span></span>
-------

<span data-ttu-id="6e587-113">Alla chiusura di un pseudoconsole, verranno terminate anche le applicazioni client associate alla sessione.</span><span class="sxs-lookup"><span data-stu-id="6e587-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="6e587-114">`hOutput`Quando viene chiamata questa API, un frame finale disegnato può arrivare dal pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="6e587-114">A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called.</span></span> <span data-ttu-id="6e587-115">Si prevede che il chiamante svuoterà queste informazioni dal buffer del canale di comunicazione e le presenti o lo eliminerà.</span><span class="sxs-lookup"><span data-stu-id="6e587-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="6e587-116">Se il buffer non viene svuotato, la chiamata di chiusura resta in attesa per un periodo illimitato fino a quando non viene svuotata o i canali di comunicazione vengono interrotti in altro modo.</span><span class="sxs-lookup"><span data-stu-id="6e587-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

<a name="requirements"></a><span data-ttu-id="6e587-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6e587-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6e587-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e587-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6e587-119">Windows 10 1809 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6e587-119">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6e587-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e587-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6e587-121">Windows Server 2019 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6e587-121">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6e587-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6e587-122">Header</span></span></p></td>
<td><span data-ttu-id="6e587-123">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6e587-123">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6e587-124">Libreria</span><span class="sxs-lookup"><span data-stu-id="6e587-124">Library</span></span></p></td>
<td><span data-ttu-id="6e587-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6e587-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6e587-126">DLL</span><span class="sxs-lookup"><span data-stu-id="6e587-126">DLL</span></span></p></td>
<td><span data-ttu-id="6e587-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6e587-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6e587-128"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6e587-128"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="6e587-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="6e587-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="6e587-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="6e587-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="6e587-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="6e587-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
