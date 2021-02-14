---
title: AllocConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AllocConsole che alloca una nuova console per il processo chiamante.
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
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357861"
---
# <a name="allocconsole-function"></a><span data-ttu-id="74e0e-104">AllocConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="74e0e-104">AllocConsole function</span></span>

<span data-ttu-id="74e0e-105">Alloca una nuova console per il processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="74e0e-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="74e0e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="74e0e-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="74e0e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="74e0e-107">Parameters</span></span>

<span data-ttu-id="74e0e-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="74e0e-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="74e0e-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="74e0e-109">Return value</span></span>

<span data-ttu-id="74e0e-110">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="74e0e-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="74e0e-111">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="74e0e-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="74e0e-112">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="74e0e-112">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="74e0e-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="74e0e-113">Remarks</span></span>

<span data-ttu-id="74e0e-114">Un processo può essere associato a una sola console, quindi la funzione **AllocConsole** ha esito negativo se il processo chiamante dispone già di una console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="74e0e-115">Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console corrente e successivamente chiamare la funzione **AllocConsole** per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="74e0e-116">Se il processo chiamante crea un processo figlio, l'elemento figlio eredita la nuova console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="74e0e-117">La funzione **AllocConsole** inizializza l'input standard, l'output standard e gli handle di errore standard per la nuova console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="74e0e-118">L'handle di input standard è un handle per il buffer di input della console, gli handle di output standard e di errore standard sono handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="74e0e-119">Per recuperare questi handle usare la funzione [**GetStdHandle**](getstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="74e0e-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="74e0e-120">Questa funzione viene utilizzata principalmente da un'applicazione interfaccia utente grafica (GUI) per creare una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="74e0e-121">Le applicazioni GUI vengono inizializzate senza una console.</span><span class="sxs-lookup"><span data-stu-id="74e0e-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="74e0e-122">Le applicazioni console vengono inizializzate con una console a meno che non vengano create come processi scollegati (chiamando la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con il flag **DETACHED\_PROCESS**).</span><span class="sxs-lookup"><span data-stu-id="74e0e-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="74e0e-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="74e0e-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="74e0e-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="74e0e-124">Minimum supported client</span></span> | <span data-ttu-id="74e0e-125">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="74e0e-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="74e0e-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="74e0e-126">Minimum supported server</span></span> | <span data-ttu-id="74e0e-127">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="74e0e-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="74e0e-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="74e0e-128">Header</span></span> | <span data-ttu-id="74e0e-129">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="74e0e-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="74e0e-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="74e0e-130">Library</span></span> | <span data-ttu-id="74e0e-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="74e0e-131">Kernel32.lib</span></span> |
| <span data-ttu-id="74e0e-132">DLL</span><span class="sxs-lookup"><span data-stu-id="74e0e-132">DLL</span></span> | <span data-ttu-id="74e0e-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="74e0e-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="74e0e-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="74e0e-134">See also</span></span>

[<span data-ttu-id="74e0e-135">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="74e0e-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="74e0e-136">Console</span><span class="sxs-lookup"><span data-stu-id="74e0e-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="74e0e-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="74e0e-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="74e0e-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="74e0e-138">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="74e0e-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="74e0e-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="74e0e-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="74e0e-140">**GetStdHandle**</span></span>](getstdhandle.md)