---
title: ReadConsoleInput (funzione)
description: Legge i dati da un buffer di input della console e li rimuove dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039489"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="30f87-104">ReadConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="30f87-104">ReadConsoleInput function</span></span>

<span data-ttu-id="30f87-105">Legge i dati da un buffer di input della console e li rimuove dal buffer.</span><span class="sxs-lookup"><span data-stu-id="30f87-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="30f87-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="30f87-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="30f87-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="30f87-107">Parameters</span></span>

<span data-ttu-id="30f87-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="30f87-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="30f87-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="30f87-109">A handle to the console input buffer.</span></span> <span data-ttu-id="30f87-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="30f87-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="30f87-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="30f87-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="30f87-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="30f87-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="30f87-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.</span><span class="sxs-lookup"><span data-stu-id="30f87-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="30f87-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="30f87-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="30f87-115">Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="30f87-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="30f87-116">*lpNumberOfEventsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="30f87-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="30f87-117">Puntatore a una variabile che riceve il numero di record di input letti.</span><span class="sxs-lookup"><span data-stu-id="30f87-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="30f87-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="30f87-118">Return value</span></span>

<span data-ttu-id="30f87-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="30f87-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="30f87-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="30f87-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="30f87-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="30f87-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="30f87-122">Commenti</span><span class="sxs-lookup"><span data-stu-id="30f87-122">Remarks</span></span>

<span data-ttu-id="30f87-123">Se il numero di record richiesti nel parametro *nLength* supera il numero di record disponibili nel buffer, viene letto il numero disponibile.</span><span class="sxs-lookup"><span data-stu-id="30f87-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="30f87-124">La funzione non restituisce alcun risultato finché non viene letto almeno un record di input.</span><span class="sxs-lookup"><span data-stu-id="30f87-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="30f87-125">Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](https://msdn.microsoft.com/library/windows/desktop/ms687069) per determinare quando l'input della console non è stato letto.</span><span class="sxs-lookup"><span data-stu-id="30f87-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="30f87-126">Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="30f87-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="30f87-127">Per determinare il numero di record di input non letti nel buffer di input di una console, usare la funzione [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="30f87-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="30f87-128">Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="30f87-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="30f87-129">Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="30f87-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="30f87-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="30f87-130">Examples</span></span>

<span data-ttu-id="30f87-131">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="30f87-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="30f87-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="30f87-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="30f87-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="30f87-133">Minimum supported client</span></span> | <span data-ttu-id="30f87-134">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="30f87-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="30f87-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="30f87-135">Minimum supported server</span></span> | <span data-ttu-id="30f87-136">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="30f87-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="30f87-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="30f87-137">Header</span></span> | <span data-ttu-id="30f87-138">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="30f87-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="30f87-139">Libreria</span><span class="sxs-lookup"><span data-stu-id="30f87-139">Library</span></span> | <span data-ttu-id="30f87-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="30f87-140">Kernel32.lib</span></span> |
| <span data-ttu-id="30f87-141">DLL</span><span class="sxs-lookup"><span data-stu-id="30f87-141">DLL</span></span> | <span data-ttu-id="30f87-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="30f87-142">Kernel32.dll</span></span> |
| <span data-ttu-id="30f87-143">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="30f87-143">Unicode and ANSI names</span></span> | <span data-ttu-id="30f87-144">**ReadConsoleInputW** (Unicode) e **ReadConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="30f87-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="30f87-145">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="30f87-145">See also</span></span>

[<span data-ttu-id="30f87-146">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="30f87-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="30f87-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="30f87-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="30f87-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="30f87-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="30f87-149">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="30f87-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="30f87-150">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="30f87-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="30f87-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="30f87-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="30f87-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="30f87-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="30f87-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="30f87-153">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="30f87-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="30f87-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="30f87-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="30f87-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="30f87-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="30f87-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
