---
title: FlushConsoleInputBuffer (funzione)
description: Svuota il buffer di input della console. Tutti i record di input attualmente presenti nel buffer di input vengono eliminati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039049"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="e3d2c-105">FlushConsoleInputBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="e3d2c-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e3d2c-106">Svuota il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-106">Flushes the console input buffer.</span></span> <span data-ttu-id="e3d2c-107">Tutti i record di input attualmente presenti nel buffer di input vengono eliminati.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3d2c-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e3d2c-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="e3d2c-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="e3d2c-109">Parameters</span></span>

<span data-ttu-id="e3d2c-110">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e3d2c-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="e3d2c-111">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-111">A handle to the console input buffer.</span></span> <span data-ttu-id="e3d2c-112">L'handle deve avere il diritto di accesso in **\_ scrittura generico** .</span><span class="sxs-lookup"><span data-stu-id="e3d2c-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="e3d2c-113">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e3d2c-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="e3d2c-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e3d2c-114">Return value</span></span>

<span data-ttu-id="e3d2c-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e3d2c-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e3d2c-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e3d2c-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e3d2c-118">Commenti</span><span class="sxs-lookup"><span data-stu-id="e3d2c-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="e3d2c-119">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="e3d2c-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="e3d2c-120">Il tentativo di svuotare la coda di input in una sola volta può eliminare lo stato della coda in modo imprevisto.</span><span class="sxs-lookup"><span data-stu-id="e3d2c-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3d2c-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e3d2c-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e3d2c-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e3d2c-122">Minimum supported client</span></span> | <span data-ttu-id="e3d2c-123">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="e3d2c-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3d2c-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e3d2c-124">Minimum supported server</span></span> | <span data-ttu-id="e3d2c-125">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="e3d2c-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3d2c-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e3d2c-126">Header</span></span> | <span data-ttu-id="e3d2c-127">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e3d2c-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e3d2c-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="e3d2c-128">Library</span></span> | <span data-ttu-id="e3d2c-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e3d2c-129">Kernel32.lib</span></span> |
| <span data-ttu-id="e3d2c-130">DLL</span><span class="sxs-lookup"><span data-stu-id="e3d2c-130">DLL</span></span> | <span data-ttu-id="e3d2c-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e3d2c-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3d2c-132">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e3d2c-132">See also</span></span>

[<span data-ttu-id="e3d2c-133">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="e3d2c-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e3d2c-134">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="e3d2c-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="e3d2c-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="e3d2c-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="e3d2c-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e3d2c-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="e3d2c-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e3d2c-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e3d2c-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e3d2c-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
