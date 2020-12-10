---
title: Funzione SetConsoleMode
description: Imposta la modalità di input di un buffer di input della console o la modalità di output di un buffer dello schermo della console.
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
ms.localizationpriority: high
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420300"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="13ce8-104">Funzione SetConsoleMode</span><span class="sxs-lookup"><span data-stu-id="13ce8-104">SetConsoleMode function</span></span>

<span data-ttu-id="13ce8-105">Imposta la modalità di input di un buffer di input della console o la modalità di output di un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="13ce8-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="13ce8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="13ce8-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="13ce8-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="13ce8-107">Parameters</span></span>

<span data-ttu-id="13ce8-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="13ce8-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="13ce8-109">Handle per un buffer di input della console o per un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="13ce8-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="13ce8-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="13ce8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="13ce8-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="13ce8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="13ce8-112">*dwMode* \[in\]</span><span class="sxs-lookup"><span data-stu-id="13ce8-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="13ce8-113">Modalità di input o output da impostare.</span><span class="sxs-lookup"><span data-stu-id="13ce8-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="13ce8-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="13ce8-114">Return value</span></span>

<span data-ttu-id="13ce8-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="13ce8-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="13ce8-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="13ce8-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="13ce8-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="13ce8-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="13ce8-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="13ce8-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="13ce8-119">Per determinare la modalità corrente di un buffer di input della console o di un buffer dello schermo, usare la funzione [**GetConsoleMode**](getconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="13ce8-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="13ce8-120">Esempi</span><span class="sxs-lookup"><span data-stu-id="13ce8-120">Examples</span></span>

<span data-ttu-id="13ce8-121">Per un esempio, vedere [Lettura di eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="13ce8-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="13ce8-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="13ce8-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="13ce8-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="13ce8-123">Minimum supported client</span></span> | <span data-ttu-id="13ce8-124">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="13ce8-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="13ce8-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="13ce8-125">Minimum supported server</span></span> | <span data-ttu-id="13ce8-126">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="13ce8-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="13ce8-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="13ce8-127">Header</span></span> | <span data-ttu-id="13ce8-128">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="13ce8-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="13ce8-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="13ce8-129">Library</span></span> | <span data-ttu-id="13ce8-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="13ce8-130">Kernel32.lib</span></span> |
| <span data-ttu-id="13ce8-131">DLL</span><span class="sxs-lookup"><span data-stu-id="13ce8-131">DLL</span></span> | <span data-ttu-id="13ce8-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="13ce8-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="13ce8-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="13ce8-133">See also</span></span>

[<span data-ttu-id="13ce8-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="13ce8-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="13ce8-135">Modalità della console</span><span class="sxs-lookup"><span data-stu-id="13ce8-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="13ce8-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="13ce8-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="13ce8-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="13ce8-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="13ce8-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="13ce8-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="13ce8-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="13ce8-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="13ce8-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="13ce8-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="13ce8-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="13ce8-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="13ce8-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="13ce8-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
