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
ms.openlocfilehash: 622dc96598df9a851934c73645afb7691f77f1be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358861"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="d28fb-104">GetNumberOfConsoleInputEvents (funzione)</span><span class="sxs-lookup"><span data-stu-id="d28fb-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="d28fb-105">Recupera il numero di record di input non letti nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="d28fb-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d28fb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d28fb-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="d28fb-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d28fb-107">Parameters</span></span>

<span data-ttu-id="d28fb-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d28fb-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="d28fb-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="d28fb-109">A handle to the console input buffer.</span></span> <span data-ttu-id="d28fb-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="d28fb-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d28fb-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d28fb-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d28fb-112">*lpcNumberOfEvents* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="d28fb-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="d28fb-113">Puntatore a una variabile che riceve il numero di record di input non letti nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="d28fb-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="d28fb-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d28fb-114">Return value</span></span>

<span data-ttu-id="d28fb-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="d28fb-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d28fb-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="d28fb-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d28fb-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="d28fb-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d28fb-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d28fb-118">Remarks</span></span>

<span data-ttu-id="d28fb-119">La funzione **GetNumberOfConsoleInputEvents** indica il numero totale di record di input non letti nel buffer di input, tra cui la tastiera, il mouse e i record di input per il ridimensionamento delle finestre.</span><span class="sxs-lookup"><span data-stu-id="d28fb-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="d28fb-120">I processi che usano la funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) possono leggere solo l'input da tastiera.</span><span class="sxs-lookup"><span data-stu-id="d28fb-120">Processes using the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="d28fb-121">I processi che usano la funzione [**ReadConsoleInput**](readconsoleinput.md) possono leggere tutti i tipi di record di input.</span><span class="sxs-lookup"><span data-stu-id="d28fb-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="d28fb-122">Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](/windows/win32/sync/wait-functions) per determinare quando l'input della console non è stato letto.</span><span class="sxs-lookup"><span data-stu-id="d28fb-122">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="d28fb-123">Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="d28fb-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="d28fb-124">Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="d28fb-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="d28fb-125">Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="d28fb-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d28fb-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d28fb-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d28fb-127">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d28fb-127">Minimum supported client</span></span> | <span data-ttu-id="d28fb-128">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="d28fb-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d28fb-129">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d28fb-129">Minimum supported server</span></span> | <span data-ttu-id="d28fb-130">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="d28fb-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d28fb-131">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d28fb-131">Header</span></span> | <span data-ttu-id="d28fb-132">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="d28fb-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d28fb-133">Libreria</span><span class="sxs-lookup"><span data-stu-id="d28fb-133">Library</span></span> | <span data-ttu-id="d28fb-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d28fb-134">Kernel32.lib</span></span> |
| <span data-ttu-id="d28fb-135">DLL</span><span class="sxs-lookup"><span data-stu-id="d28fb-135">DLL</span></span> | <span data-ttu-id="d28fb-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d28fb-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d28fb-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d28fb-137">See also</span></span>

[<span data-ttu-id="d28fb-138">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="d28fb-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d28fb-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="d28fb-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="d28fb-140">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="d28fb-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="d28fb-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="d28fb-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="d28fb-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="d28fb-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="d28fb-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="d28fb-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="d28fb-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="d28fb-144">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)