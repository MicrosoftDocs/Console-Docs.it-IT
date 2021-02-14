---
title: GetConsoleMode (funzione)
description: Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 3f98797b0662dadcf696f76ffda5f42e759bf930
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357283"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="89f2f-104">GetConsoleMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="89f2f-104">GetConsoleMode function</span></span>

<span data-ttu-id="89f2f-105">Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="89f2f-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="89f2f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="89f2f-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="89f2f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="89f2f-107">Parameters</span></span>

<span data-ttu-id="89f2f-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="89f2f-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="89f2f-109">Handle per il buffer di input della console o il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="89f2f-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="89f2f-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="89f2f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="89f2f-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="89f2f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="89f2f-112">*lpMode* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="89f2f-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="89f2f-113">Puntatore a una variabile che riceve la modalità corrente del buffer specificato.</span><span class="sxs-lookup"><span data-stu-id="89f2f-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="89f2f-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="89f2f-114">Return value</span></span>

<span data-ttu-id="89f2f-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="89f2f-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="89f2f-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="89f2f-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="89f2f-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="89f2f-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="89f2f-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="89f2f-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="89f2f-119">Per modificare le modalità I/O di una console, chiamare la funzione [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="89f2f-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="89f2f-120">Esempi</span><span class="sxs-lookup"><span data-stu-id="89f2f-120">Examples</span></span>

<span data-ttu-id="89f2f-121">Un esempio è disponibile in [Lettura di eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="89f2f-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="89f2f-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="89f2f-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="89f2f-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="89f2f-123">Minimum supported client</span></span> | <span data-ttu-id="89f2f-124">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="89f2f-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="89f2f-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="89f2f-125">Minimum supported server</span></span> | <span data-ttu-id="89f2f-126">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="89f2f-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="89f2f-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="89f2f-127">Header</span></span> | <span data-ttu-id="89f2f-128">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="89f2f-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="89f2f-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="89f2f-129">Library</span></span> | <span data-ttu-id="89f2f-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="89f2f-130">Kernel32.lib</span></span> |
| <span data-ttu-id="89f2f-131">DLL</span><span class="sxs-lookup"><span data-stu-id="89f2f-131">DLL</span></span> | <span data-ttu-id="89f2f-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="89f2f-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="89f2f-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89f2f-133">See also</span></span>

[<span data-ttu-id="89f2f-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="89f2f-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="89f2f-135">Modalità della console</span><span class="sxs-lookup"><span data-stu-id="89f2f-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="89f2f-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="89f2f-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="89f2f-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89f2f-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="89f2f-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="89f2f-138">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="89f2f-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="89f2f-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="89f2f-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="89f2f-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="89f2f-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="89f2f-141">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)