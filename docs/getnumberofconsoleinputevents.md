---
title: GetNumberOfConsoleInputEvents (funzione)
description: Recupera il numero di record di input non letti nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038689"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="5df2e-104">GetNumberOfConsoleInputEvents (funzione)</span><span class="sxs-lookup"><span data-stu-id="5df2e-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="5df2e-105">Recupera il numero di record di input non letti nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="5df2e-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="5df2e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5df2e-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="5df2e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5df2e-107">Parameters</span></span>

<span data-ttu-id="5df2e-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5df2e-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="5df2e-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="5df2e-109">A handle to the console input buffer.</span></span> <span data-ttu-id="5df2e-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="5df2e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="5df2e-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5df2e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5df2e-112">*lpcNumberOfEvents* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="5df2e-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="5df2e-113">Puntatore a una variabile che riceve il numero di record di input non letti nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="5df2e-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="5df2e-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5df2e-114">Return value</span></span>

<span data-ttu-id="5df2e-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="5df2e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5df2e-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="5df2e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5df2e-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5df2e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="5df2e-118">Commenti</span><span class="sxs-lookup"><span data-stu-id="5df2e-118">Remarks</span></span>

<span data-ttu-id="5df2e-119">La funzione **GetNumberOfConsoleInputEvents** indica il numero totale di record di input non letti nel buffer di input, tra cui la tastiera, il mouse e i record di input per il ridimensionamento delle finestre.</span><span class="sxs-lookup"><span data-stu-id="5df2e-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="5df2e-120">I processi che usano la funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) possono leggere solo l'input da tastiera.</span><span class="sxs-lookup"><span data-stu-id="5df2e-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="5df2e-121">I processi che usano la funzione [**ReadConsoleInput**](readconsoleinput.md) possono leggere tutti i tipi di record di input.</span><span class="sxs-lookup"><span data-stu-id="5df2e-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="5df2e-122">Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](https://msdn.microsoft.com/library/windows/desktop/ms687069) per determinare quando l'input della console non è stato letto.</span><span class="sxs-lookup"><span data-stu-id="5df2e-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="5df2e-123">Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="5df2e-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="5df2e-124">Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="5df2e-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="5df2e-125">Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="5df2e-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5df2e-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5df2e-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5df2e-127">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5df2e-127">Minimum supported client</span></span> | <span data-ttu-id="5df2e-128">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="5df2e-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5df2e-129">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5df2e-129">Minimum supported server</span></span> | <span data-ttu-id="5df2e-130">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="5df2e-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5df2e-131">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5df2e-131">Header</span></span> | <span data-ttu-id="5df2e-132">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5df2e-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5df2e-133">Libreria</span><span class="sxs-lookup"><span data-stu-id="5df2e-133">Library</span></span> | <span data-ttu-id="5df2e-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5df2e-134">Kernel32.lib</span></span> |
| <span data-ttu-id="5df2e-135">DLL</span><span class="sxs-lookup"><span data-stu-id="5df2e-135">DLL</span></span> | <span data-ttu-id="5df2e-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5df2e-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5df2e-137">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5df2e-137">See also</span></span>

[<span data-ttu-id="5df2e-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="5df2e-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5df2e-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="5df2e-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="5df2e-140">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="5df2e-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="5df2e-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5df2e-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="5df2e-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="5df2e-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="5df2e-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5df2e-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="5df2e-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="5df2e-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)
