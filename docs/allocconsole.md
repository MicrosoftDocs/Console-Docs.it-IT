---
title: AllocConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AllocConsole, che alloca una nuova console per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: c63c9a176c0d8ca2ef4342f7bee1b427eae00014
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420170"
---
# <a name="allocconsole-function"></a><span data-ttu-id="52510-104">AllocConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="52510-104">AllocConsole function</span></span>

<span data-ttu-id="52510-105">Alloca una nuova console per il processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="52510-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="52510-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="52510-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="52510-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="52510-107">Parameters</span></span>

<span data-ttu-id="52510-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="52510-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="52510-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="52510-109">Return value</span></span>

<span data-ttu-id="52510-110">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="52510-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="52510-111">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="52510-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="52510-112">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="52510-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="52510-113">Commenti</span><span class="sxs-lookup"><span data-stu-id="52510-113">Remarks</span></span>

<span data-ttu-id="52510-114">Un processo può essere associato a una sola console, quindi la funzione **AllocConsole** ha esito negativo se il processo chiamante dispone già di una console.</span><span class="sxs-lookup"><span data-stu-id="52510-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="52510-115">Un processo può usare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console corrente, quindi può chiamare **AllocConsole** per creare una nuova console o [**AttachConsole**](attachconsole.md) da connettere a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="52510-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="52510-116">Se il processo chiamante crea un processo figlio, l'elemento figlio eredita la nuova console.</span><span class="sxs-lookup"><span data-stu-id="52510-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="52510-117">**AllocConsole** Inizializza l'input standard, l'output standard e gli handle di errore standard per la nuova console.</span><span class="sxs-lookup"><span data-stu-id="52510-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="52510-118">L'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="52510-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="52510-119">Per recuperare questi handle, utilizzare la funzione [**GetStdHandle**](getstdhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="52510-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="52510-120">Questa funzione viene utilizzata principalmente da un'applicazione GUI (Graphical User Interface) per creare una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="52510-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="52510-121">Le applicazioni GUI vengono inizializzate senza una console.</span><span class="sxs-lookup"><span data-stu-id="52510-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="52510-122">Le applicazioni console vengono inizializzate con una console, a meno che non vengano create come processi scollegati (chiamando la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con il flag di **\_ processo scollegato** ).</span><span class="sxs-lookup"><span data-stu-id="52510-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="52510-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="52510-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="52510-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="52510-124">Minimum supported client</span></span> | <span data-ttu-id="52510-125">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="52510-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="52510-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="52510-126">Minimum supported server</span></span> | <span data-ttu-id="52510-127">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="52510-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="52510-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="52510-128">Header</span></span> | <span data-ttu-id="52510-129">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="52510-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="52510-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="52510-130">Library</span></span> | <span data-ttu-id="52510-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="52510-131">Kernel32.lib</span></span> |
| <span data-ttu-id="52510-132">DLL</span><span class="sxs-lookup"><span data-stu-id="52510-132">DLL</span></span> | <span data-ttu-id="52510-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="52510-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="52510-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="52510-134">See also</span></span>

[<span data-ttu-id="52510-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="52510-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="52510-136">Console</span><span class="sxs-lookup"><span data-stu-id="52510-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="52510-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="52510-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="52510-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="52510-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="52510-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="52510-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="52510-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="52510-140">**GetStdHandle**</span></span>](getstdhandle.md)
