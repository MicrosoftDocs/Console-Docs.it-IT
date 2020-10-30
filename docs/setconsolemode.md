---
title: SetConsoleMode (funzione)
description: Imposta la modalità di input del buffer di input di una console o la modalità di output di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b382e6567d2099e2d6eacf33c8e19233f20c6400
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039359"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="2cca7-104">SetConsoleMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="2cca7-104">SetConsoleMode function</span></span>

<span data-ttu-id="2cca7-105">Imposta la modalità di input del buffer di input di una console o la modalità di output di un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2cca7-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="2cca7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2cca7-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="2cca7-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="2cca7-107">Parameters</span></span>

<span data-ttu-id="2cca7-108">*hConsoleHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2cca7-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="2cca7-109">Handle per il buffer di input della console o un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2cca7-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="2cca7-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="2cca7-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="2cca7-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2cca7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2cca7-112">*dwMode* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2cca7-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="2cca7-113">Modalità di input o output da impostare.</span><span class="sxs-lookup"><span data-stu-id="2cca7-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="2cca7-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2cca7-114">Return value</span></span>

<span data-ttu-id="2cca7-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2cca7-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2cca7-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2cca7-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2cca7-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2cca7-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="2cca7-118">Commenti</span><span class="sxs-lookup"><span data-stu-id="2cca7-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="2cca7-119">Per determinare la modalità corrente di un buffer di input della console o di un buffer dello schermo, usare la funzione [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="2cca7-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="2cca7-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="2cca7-120">Examples</span></span>

<span data-ttu-id="2cca7-121">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="2cca7-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="2cca7-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2cca7-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2cca7-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2cca7-123">Minimum supported client</span></span> | <span data-ttu-id="2cca7-124">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="2cca7-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2cca7-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2cca7-125">Minimum supported server</span></span> | <span data-ttu-id="2cca7-126">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="2cca7-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2cca7-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2cca7-127">Header</span></span> | <span data-ttu-id="2cca7-128">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2cca7-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2cca7-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="2cca7-129">Library</span></span> | <span data-ttu-id="2cca7-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2cca7-130">Kernel32.lib</span></span> |
| <span data-ttu-id="2cca7-131">DLL</span><span class="sxs-lookup"><span data-stu-id="2cca7-131">DLL</span></span> | <span data-ttu-id="2cca7-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2cca7-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="2cca7-133">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2cca7-133">See also</span></span>

[<span data-ttu-id="2cca7-134">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="2cca7-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2cca7-135">Modalità console</span><span class="sxs-lookup"><span data-stu-id="2cca7-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="2cca7-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2cca7-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="2cca7-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="2cca7-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="2cca7-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="2cca7-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="2cca7-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2cca7-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="2cca7-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="2cca7-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="2cca7-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="2cca7-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="2cca7-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="2cca7-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
