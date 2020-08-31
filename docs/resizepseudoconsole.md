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
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060348"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="a94b1-104">ResizePseudoConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="a94b1-104">ResizePseudoConsole function</span></span>


<span data-ttu-id="a94b1-105">Ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata.</span><span class="sxs-lookup"><span data-stu-id="a94b1-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

<a name="syntax"></a><span data-ttu-id="a94b1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a94b1-106">Syntax</span></span>
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a><span data-ttu-id="a94b1-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="a94b1-107">Parameters</span></span>
----------

<span data-ttu-id="a94b1-108">*hPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a94b1-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="a94b1-109">Handle per un psuedoconsole attivo come aperto da [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="a94b1-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="a94b1-110">*dimensioni* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a94b1-110">*size* \[in\]</span></span>  
<span data-ttu-id="a94b1-111">Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati per il buffer interno di questo pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="a94b1-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span> 

<a name="return-value"></a><span data-ttu-id="a94b1-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="a94b1-112">Return value</span></span>
------------

<span data-ttu-id="a94b1-113">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="a94b1-113">Type: **HRESULT**</span></span>

<span data-ttu-id="a94b1-114">Se questo metodo ha esito positivo, restituisce **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="a94b1-114">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="a94b1-115">In caso contrario, restituisce un codice di errore **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="a94b1-115">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="a94b1-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a94b1-116">Remarks</span></span>
-------

<span data-ttu-id="a94b1-117">Questa funzione può ridimensionare i buffer interni della sessione pseudoconsole in modo che corrispondano alla dimensione della finestra o del buffer utilizzata per la visualizzazione nel terminale finale.</span><span class="sxs-lookup"><span data-stu-id="a94b1-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="a94b1-118">In questo modo si assicura che le applicazioni con le funzioni di interfaccia della riga di comando collegate che usano le [funzioni della console](console-functions.md) per la comunicazione abbiano le dimensioni corrette restituite nelle chiamate.</span><span class="sxs-lookup"><span data-stu-id="a94b1-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

<a name="requirements"></a><span data-ttu-id="a94b1-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a94b1-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a94b1-120">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a94b1-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a94b1-121">Windows 10 1809 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="a94b1-121">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a94b1-122">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="a94b1-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a94b1-123">Windows Server 2019 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="a94b1-123">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a94b1-124">Intestazione</span><span class="sxs-lookup"><span data-stu-id="a94b1-124">Header</span></span></p></td>
<td><span data-ttu-id="a94b1-125">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a94b1-125">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a94b1-126">Libreria</span><span class="sxs-lookup"><span data-stu-id="a94b1-126">Library</span></span></p></td>
<td><span data-ttu-id="a94b1-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a94b1-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a94b1-128">DLL</span><span class="sxs-lookup"><span data-stu-id="a94b1-128">DLL</span></span></p></td>
<td><span data-ttu-id="a94b1-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a94b1-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a94b1-130"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a94b1-130"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="a94b1-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="a94b1-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="a94b1-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="a94b1-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="a94b1-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="a94b1-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
