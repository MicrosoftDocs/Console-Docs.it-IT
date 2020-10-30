---
title: WriteConsoleInput (funzione)
description: Vedere informazioni di riferimento sulla funzione WriteConsoleInput, che consente di scrivere dati direttamente nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039289"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="fbabe-104">WriteConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="fbabe-104">WriteConsoleInput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="fbabe-105">Scrive i dati direttamente nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="fbabe-105">Writes data directly to the console input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbabe-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fbabe-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="fbabe-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="fbabe-107">Parameters</span></span>

<span data-ttu-id="fbabe-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="fbabe-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="fbabe-109">A handle to the console input buffer.</span></span> <span data-ttu-id="fbabe-110">L'handle deve avere il diritto di accesso in **\_ scrittura generico** .</span><span class="sxs-lookup"><span data-stu-id="fbabe-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="fbabe-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="fbabe-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="fbabe-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="fbabe-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che contengono dati da scrivere nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="fbabe-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="fbabe-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="fbabe-115">Numero di record di input da scrivere.</span><span class="sxs-lookup"><span data-stu-id="fbabe-115">The number of input records to be written.</span></span>

<span data-ttu-id="fbabe-116">*lpNumberOfEventsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="fbabe-117">Puntatore a una variabile che riceve il numero di record di input effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="fbabe-117">A pointer to a variable that receives the number of input records actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="fbabe-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="fbabe-118">Return value</span></span>

<span data-ttu-id="fbabe-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="fbabe-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fbabe-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="fbabe-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fbabe-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fbabe-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="fbabe-122">Commenti</span><span class="sxs-lookup"><span data-stu-id="fbabe-122">Remarks</span></span>

<span data-ttu-id="fbabe-123">**WriteConsoleInput** inserisce i record di input nel buffer di input dietro tutti gli eventi in sospeso nel buffer.</span><span class="sxs-lookup"><span data-stu-id="fbabe-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="fbabe-124">Il buffer di input aumenta in modo dinamico, se necessario, per mantenere il numero di eventi scritti.</span><span class="sxs-lookup"><span data-stu-id="fbabe-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="fbabe-125">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="fbabe-125">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="fbabe-126">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="fbabe-126">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="fbabe-127">Questa operazione viene considerata come un **[verbo errato](console-buffer-security-and-access-rights.md#wrong-way-verbs)** per questo buffer.</span><span class="sxs-lookup"><span data-stu-id="fbabe-127">This operation is considered the **[wrong-way verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** for this buffer.</span></span> <span data-ttu-id="fbabe-128">Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.</span><span class="sxs-lookup"><span data-stu-id="fbabe-128">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbabe-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fbabe-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fbabe-130">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fbabe-130">Minimum supported client</span></span> | <span data-ttu-id="fbabe-131">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fbabe-132">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fbabe-132">Minimum supported server</span></span> | <span data-ttu-id="fbabe-133">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="fbabe-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fbabe-134">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fbabe-134">Header</span></span> | <span data-ttu-id="fbabe-135">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fbabe-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fbabe-136">Libreria</span><span class="sxs-lookup"><span data-stu-id="fbabe-136">Library</span></span> | <span data-ttu-id="fbabe-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fbabe-137">Kernel32.lib</span></span> |
| <span data-ttu-id="fbabe-138">DLL</span><span class="sxs-lookup"><span data-stu-id="fbabe-138">DLL</span></span> | <span data-ttu-id="fbabe-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fbabe-139">Kernel32.dll</span></span> |
| <span data-ttu-id="fbabe-140">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="fbabe-140">Unicode and ANSI names</span></span> | <span data-ttu-id="fbabe-141">**WriteConsoleInputW** (Unicode) e **WriteConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="fbabe-141">**WriteConsoleInputW** (Unicode) and **WriteConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fbabe-142">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fbabe-142">See also</span></span>

[<span data-ttu-id="fbabe-143">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="fbabe-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fbabe-144">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="fbabe-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="fbabe-145">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="fbabe-145">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="fbabe-146">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="fbabe-146">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="fbabe-147">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fbabe-147">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="fbabe-148">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fbabe-148">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="fbabe-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="fbabe-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="fbabe-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="fbabe-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="fbabe-151">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="fbabe-151">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)
