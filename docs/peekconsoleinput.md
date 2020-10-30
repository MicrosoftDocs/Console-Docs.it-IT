---
title: PeekConsoleInput (funzione)
description: Legge i dati dal buffer di input della console specificato senza rimuoverlo dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9052f15b36e16dd2ddf7fe46d3d201aa21403f91
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039499"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="4c4a9-104">PeekConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="4c4a9-104">PeekConsoleInput function</span></span>

<span data-ttu-id="4c4a9-105">Legge i dati dal buffer di input della console specificato senza rimuoverlo dal buffer.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c4a9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4c4a9-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="4c4a9-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4c4a9-107">Parameters</span></span>

<span data-ttu-id="4c4a9-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="4c4a9-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-109">A handle to the console input buffer.</span></span> <span data-ttu-id="4c4a9-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="4c4a9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4c4a9-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4c4a9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4c4a9-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="4c4a9-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="4c4a9-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="4c4a9-115">Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="4c4a9-116">*lpNumberOfEventsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="4c4a9-117">Puntatore a una variabile che riceve il numero di record di input letti.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c4a9-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4c4a9-118">Return value</span></span>

<span data-ttu-id="4c4a9-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4c4a9-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4c4a9-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c4a9-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4c4a9-122">Commenti</span><span class="sxs-lookup"><span data-stu-id="4c4a9-122">Remarks</span></span>

<span data-ttu-id="4c4a9-123">Se il numero di record richiesti supera il numero di record disponibili nel buffer, viene letto il numero disponibile.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="4c4a9-124">Se non sono disponibili dati, la funzione restituisce immediatamente il risultato.</span><span class="sxs-lookup"><span data-stu-id="4c4a9-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="4c4a9-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4c4a9-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4c4a9-126">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4c4a9-126">Minimum supported client</span></span> | <span data-ttu-id="4c4a9-127">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c4a9-128">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4c4a9-128">Minimum supported server</span></span> | <span data-ttu-id="4c4a9-129">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4c4a9-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c4a9-130">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4c4a9-130">Header</span></span> | <span data-ttu-id="4c4a9-131">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c4a9-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4c4a9-132">Libreria</span><span class="sxs-lookup"><span data-stu-id="4c4a9-132">Library</span></span> | <span data-ttu-id="4c4a9-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c4a9-133">Kernel32.lib</span></span> |
| <span data-ttu-id="4c4a9-134">DLL</span><span class="sxs-lookup"><span data-stu-id="4c4a9-134">DLL</span></span> | <span data-ttu-id="4c4a9-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c4a9-135">Kernel32.dll</span></span> |
| <span data-ttu-id="4c4a9-136">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="4c4a9-136">Unicode and ANSI names</span></span> | <span data-ttu-id="4c4a9-137">**PeekConsoleInputW** (Unicode) e **PeekConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4c4a9-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4c4a9-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4c4a9-138">See also</span></span>

[<span data-ttu-id="4c4a9-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="4c4a9-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c4a9-140">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4c4a9-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="4c4a9-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="4c4a9-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="4c4a9-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="4c4a9-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="4c4a9-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4c4a9-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="4c4a9-144">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="4c4a9-144">**INPUT\_RECORD**</span></span>](input-record-str.md)
