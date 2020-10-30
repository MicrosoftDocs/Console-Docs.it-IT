---
title: ResizePseudoConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione ResizePseudoConsole, che ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037539"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="5cb22-104">ResizePseudoConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="5cb22-104">ResizePseudoConsole function</span></span>

<span data-ttu-id="5cb22-105">Ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.</span><span class="sxs-lookup"><span data-stu-id="5cb22-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

## <a name="syntax"></a><span data-ttu-id="5cb22-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5cb22-106">Syntax</span></span>

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a><span data-ttu-id="5cb22-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5cb22-107">Parameters</span></span>

<span data-ttu-id="5cb22-108">*hPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5cb22-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="5cb22-109">Handle per un pseudoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="5cb22-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="5cb22-110">*dimensioni* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5cb22-110">*size* \[in\]</span></span>  
<span data-ttu-id="5cb22-111">Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati per il buffer interno di questo pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="5cb22-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span>

## <a name="return-value"></a><span data-ttu-id="5cb22-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5cb22-112">Return value</span></span>

<span data-ttu-id="5cb22-113">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="5cb22-113">Type: **HRESULT**</span></span>

<span data-ttu-id="5cb22-114">Se questo metodo ha esito positivo, restituisce **S_OK** .</span><span class="sxs-lookup"><span data-stu-id="5cb22-114">If this method succeeds, it returns **S_OK** .</span></span> <span data-ttu-id="5cb22-115">In caso contrario, restituisce un codice di errore **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="5cb22-115">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cb22-116">Commenti</span><span class="sxs-lookup"><span data-stu-id="5cb22-116">Remarks</span></span>

<span data-ttu-id="5cb22-117">Questa funzione può ridimensionare i buffer interni della sessione pseudoconsole in modo che corrispondano alla dimensione della finestra o del buffer utilizzata per la visualizzazione nel terminale finale.</span><span class="sxs-lookup"><span data-stu-id="5cb22-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="5cb22-118">In questo modo si assicura che le applicazioni associate Command-Line Interface (cui) che usano le [funzioni della console](console-functions.md) per la comunicazione abbiano le dimensioni corrette restituite nelle chiamate.</span><span class="sxs-lookup"><span data-stu-id="5cb22-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cb22-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5cb22-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5cb22-120">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5cb22-120">Minimum supported client</span></span> | <span data-ttu-id="5cb22-121">Aggiornamento di Windows 10 ottobre 2018 (versione 1809) \[ solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="5cb22-121">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="5cb22-122">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5cb22-122">Minimum supported server</span></span> | <span data-ttu-id="5cb22-123">\[Solo app desktop Windows Server 2019\]</span><span class="sxs-lookup"><span data-stu-id="5cb22-123">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="5cb22-124">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5cb22-124">Header</span></span> | <span data-ttu-id="5cb22-125">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5cb22-125">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5cb22-126">Libreria</span><span class="sxs-lookup"><span data-stu-id="5cb22-126">Library</span></span> | <span data-ttu-id="5cb22-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5cb22-127">Kernel32.lib</span></span> |
| <span data-ttu-id="5cb22-128">DLL</span><span class="sxs-lookup"><span data-stu-id="5cb22-128">DLL</span></span> | <span data-ttu-id="5cb22-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5cb22-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5cb22-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5cb22-130">See also</span></span>

[<span data-ttu-id="5cb22-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="5cb22-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="5cb22-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="5cb22-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="5cb22-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="5cb22-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
