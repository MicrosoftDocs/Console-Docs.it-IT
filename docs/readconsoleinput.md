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
ms.openlocfilehash: 06e784ebaebde2ed68ed17f75f4e54932aa463f5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358721"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="f8081-104">ReadConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="f8081-104">ReadConsoleInput function</span></span>

<span data-ttu-id="f8081-105">Legge i dati da un buffer di input della console e li rimuove dal buffer.</span><span class="sxs-lookup"><span data-stu-id="f8081-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8081-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f8081-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="f8081-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="f8081-107">Parameters</span></span>

<span data-ttu-id="f8081-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f8081-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="f8081-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="f8081-109">A handle to the console input buffer.</span></span> <span data-ttu-id="f8081-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="f8081-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f8081-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f8081-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f8081-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="f8081-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="f8081-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che riceve i dati del buffer di input.</span><span class="sxs-lookup"><span data-stu-id="f8081-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="f8081-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f8081-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="f8081-115">Dimensione della matrice a cui fa riferimento il parametro *lpBuffer* , in elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="f8081-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="f8081-116">*lpNumberOfEventsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="f8081-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="f8081-117">Puntatore a una variabile che riceve il numero di record di input letti.</span><span class="sxs-lookup"><span data-stu-id="f8081-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8081-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f8081-118">Return value</span></span>

<span data-ttu-id="f8081-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="f8081-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f8081-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="f8081-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f8081-121">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="f8081-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f8081-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f8081-122">Remarks</span></span>

<span data-ttu-id="f8081-123">Se il numero di record richiesti nel parametro *nLength* supera il numero di record disponibili nel buffer, viene letto il numero disponibile.</span><span class="sxs-lookup"><span data-stu-id="f8081-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="f8081-124">La funzione non restituisce alcun risultato finché non viene letto almeno un record di input.</span><span class="sxs-lookup"><span data-stu-id="f8081-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="f8081-125">Un processo può specificare un handle del buffer di input della console in una delle [funzioni di attesa](/windows/win32/sync/wait-functions) per determinare quando l'input della console non è stato letto.</span><span class="sxs-lookup"><span data-stu-id="f8081-125">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="f8081-126">Quando il buffer di input non è vuoto, viene segnalato lo stato di un handle del buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="f8081-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="f8081-127">Per determinare il numero di record di input non letti nel buffer di input di una console, usare la funzione [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) .</span><span class="sxs-lookup"><span data-stu-id="f8081-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="f8081-128">Per leggere i record di input da un buffer di input della console senza influire sul numero di record non letti, usare la funzione [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="f8081-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="f8081-129">Per rimuovere tutti i record non letti nel buffer di input di una console, usare la funzione [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="f8081-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="f8081-130">Esempi</span><span class="sxs-lookup"><span data-stu-id="f8081-130">Examples</span></span>

<span data-ttu-id="f8081-131">Un esempio è disponibile in [Lettura di eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="f8081-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f8081-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f8081-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f8081-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f8081-133">Minimum supported client</span></span> | <span data-ttu-id="f8081-134">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="f8081-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f8081-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f8081-135">Minimum supported server</span></span> | <span data-ttu-id="f8081-136">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="f8081-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f8081-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="f8081-137">Header</span></span> | <span data-ttu-id="f8081-138">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="f8081-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f8081-139">Libreria</span><span class="sxs-lookup"><span data-stu-id="f8081-139">Library</span></span> | <span data-ttu-id="f8081-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f8081-140">Kernel32.lib</span></span> |
| <span data-ttu-id="f8081-141">DLL</span><span class="sxs-lookup"><span data-stu-id="f8081-141">DLL</span></span> | <span data-ttu-id="f8081-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f8081-142">Kernel32.dll</span></span> |
| <span data-ttu-id="f8081-143">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="f8081-143">Unicode and ANSI names</span></span> | <span data-ttu-id="f8081-144">**ReadConsoleInputW** (Unicode) e **ReadConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f8081-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f8081-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8081-145">See also</span></span>

[<span data-ttu-id="f8081-146">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="f8081-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f8081-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="f8081-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="f8081-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="f8081-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="f8081-149">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="f8081-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="f8081-150">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="f8081-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="f8081-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f8081-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="f8081-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="f8081-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="f8081-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="f8081-153">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="f8081-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f8081-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f8081-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f8081-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f8081-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f8081-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)