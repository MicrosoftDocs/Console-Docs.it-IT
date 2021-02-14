---
title: FreeConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione FreeConsole, che scollega il processo chiamante dalla relativa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a7a90b3770128067a63b4872e6bb9a37acdcaf6c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359011"
---
# <a name="freeconsole-function"></a><span data-ttu-id="8223d-104">FreeConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="8223d-104">FreeConsole function</span></span>

<span data-ttu-id="8223d-105">Scollega il processo chiamante dalla relativa console.</span><span class="sxs-lookup"><span data-stu-id="8223d-105">Detaches the calling process from its console.</span></span>

## <a name="syntax"></a><span data-ttu-id="8223d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8223d-106">Syntax</span></span>

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="8223d-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8223d-107">Parameters</span></span>

<span data-ttu-id="8223d-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="8223d-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="8223d-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8223d-109">Return value</span></span>

<span data-ttu-id="8223d-110">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="8223d-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8223d-111">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="8223d-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8223d-112">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="8223d-112">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="8223d-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8223d-113">Remarks</span></span>

<span data-ttu-id="8223d-114">Un processo può essere collegato al massimo da una console.</span><span class="sxs-lookup"><span data-stu-id="8223d-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="8223d-115">Se il processo chiamante non è già collegato a una console, il codice di errore restituito **è \_ errore \_ parametro non valido** (87).</span><span class="sxs-lookup"><span data-stu-id="8223d-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="8223d-116">Un processo può utilizzare la funzione **FreeConsole** per scollegarsi dalla console.</span><span class="sxs-lookup"><span data-stu-id="8223d-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="8223d-117">Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="8223d-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="8223d-118">Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="8223d-118">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="8223d-119">Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="8223d-119">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

## <a name="requirements"></a><span data-ttu-id="8223d-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8223d-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8223d-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8223d-121">Minimum supported client</span></span> | <span data-ttu-id="8223d-122">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="8223d-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8223d-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8223d-123">Minimum supported server</span></span> | <span data-ttu-id="8223d-124">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="8223d-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8223d-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8223d-125">Header</span></span> | <span data-ttu-id="8223d-126">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="8223d-126">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8223d-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="8223d-127">Library</span></span> | <span data-ttu-id="8223d-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="8223d-128">Kernel32.lib</span></span> |
| <span data-ttu-id="8223d-129">DLL</span><span class="sxs-lookup"><span data-stu-id="8223d-129">DLL</span></span> | <span data-ttu-id="8223d-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8223d-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="8223d-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8223d-131">See also</span></span>

[<span data-ttu-id="8223d-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="8223d-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="8223d-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="8223d-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="8223d-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="8223d-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8223d-135">Console</span><span class="sxs-lookup"><span data-stu-id="8223d-135">Consoles</span></span>](consoles.md)