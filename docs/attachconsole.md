---
title: AttachConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AttachConsole, che consente di alleghi il processo chiamante alla console del processo specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bfc71c10a02e9ed8a0bc18fd26cffa855012c692
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037479"
---
# <a name="attachconsole-function"></a><span data-ttu-id="d3efb-104">AttachConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="d3efb-104">AttachConsole function</span></span>

<span data-ttu-id="d3efb-105">Connette il processo chiamante alla console del processo specificato come applicazione client.</span><span class="sxs-lookup"><span data-stu-id="d3efb-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3efb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d3efb-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="d3efb-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d3efb-107">Parameters</span></span>

<span data-ttu-id="d3efb-108">*dwProcessId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d3efb-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="d3efb-109">Identificatore del processo di cui si desidera utilizzare la console.</span><span class="sxs-lookup"><span data-stu-id="d3efb-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="d3efb-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="d3efb-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="d3efb-111">Valore</span><span class="sxs-lookup"><span data-stu-id="d3efb-111">Value</span></span> | <span data-ttu-id="d3efb-112">Significato</span><span class="sxs-lookup"><span data-stu-id="d3efb-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="d3efb-113">*PID*</span><span class="sxs-lookup"><span data-stu-id="d3efb-113">*pid*</span></span> | <span data-ttu-id="d3efb-114">Utilizzare la console del processo specificato.</span><span class="sxs-lookup"><span data-stu-id="d3efb-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="d3efb-115">**Connetti \_ \_processo padre**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="d3efb-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="d3efb-116">Utilizzare la console dell'elemento padre del processo corrente.</span><span class="sxs-lookup"><span data-stu-id="d3efb-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="d3efb-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d3efb-117">Return value</span></span>

<span data-ttu-id="d3efb-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="d3efb-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d3efb-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="d3efb-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d3efb-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d3efb-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="d3efb-121">Commenti</span><span class="sxs-lookup"><span data-stu-id="d3efb-121">Remarks</span></span>

<span data-ttu-id="d3efb-122">Un processo può essere collegato al massimo da una console.</span><span class="sxs-lookup"><span data-stu-id="d3efb-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="d3efb-123">Se il processo chiamante è già collegato a una console, il codice di errore restituito è **errore \_ accesso \_ negato** ( `5` ).</span><span class="sxs-lookup"><span data-stu-id="d3efb-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="d3efb-124">Se il processo specificato non dispone di una console, il codice di errore restituito **è \_ errore \_ handle non valido** ( `6` ).</span><span class="sxs-lookup"><span data-stu-id="d3efb-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="d3efb-125">Se il processo specificato non esiste, il codice di errore restituito è **errore \_ \_ parametro non valido** ( `87` ).</span><span class="sxs-lookup"><span data-stu-id="d3efb-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="d3efb-126">Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console.</span><span class="sxs-lookup"><span data-stu-id="d3efb-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="d3efb-127">Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="d3efb-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="d3efb-128">Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole** .</span><span class="sxs-lookup"><span data-stu-id="d3efb-128">A console is closed when the last process attached to it terminates or calls **FreeConsole** .</span></span> <span data-ttu-id="d3efb-129">Dopo che un processo chiama **FreeConsole** , può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o **AttachConsole** per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="d3efb-129">After a process calls **FreeConsole** , it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="d3efb-130">Questa funzione è utile principalmente per le applicazioni collegate con [**/SUBSYSTEM: Windows**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), che implica al sistema operativo che non è necessaria una console prima di immettere il metodo Main del programma.</span><span class="sxs-lookup"><span data-stu-id="d3efb-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="d3efb-131">In tal caso, gli handle standard recuperati con [**GetStdHandle**](getstdhandle.md) probabilmente non saranno validi all'avvio fino a quando non viene chiamato **AttachConsole** .</span><span class="sxs-lookup"><span data-stu-id="d3efb-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="d3efb-132">L'eccezione è rappresentata dall'avvio dell'applicazione con la gestione dell'ereditarietà da parte del processo padre.</span><span class="sxs-lookup"><span data-stu-id="d3efb-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="d3efb-133">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come `0x0501` o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="d3efb-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="d3efb-134">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="d3efb-134">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

## <a name="requirements"></a><span data-ttu-id="d3efb-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d3efb-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d3efb-136">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d3efb-136">Minimum supported client</span></span> | <span data-ttu-id="d3efb-137">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="d3efb-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="d3efb-138">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d3efb-138">Minimum supported server</span></span> | <span data-ttu-id="d3efb-139">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="d3efb-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="d3efb-140">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d3efb-140">Header</span></span> | <span data-ttu-id="d3efb-141">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d3efb-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d3efb-142">Libreria</span><span class="sxs-lookup"><span data-stu-id="d3efb-142">Library</span></span> | <span data-ttu-id="d3efb-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d3efb-143">Kernel32.lib</span></span> |
| <span data-ttu-id="d3efb-144">DLL</span><span class="sxs-lookup"><span data-stu-id="d3efb-144">DLL</span></span> | <span data-ttu-id="d3efb-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d3efb-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d3efb-146">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d3efb-146">See also</span></span>

[<span data-ttu-id="d3efb-147">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="d3efb-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d3efb-148">Console</span><span class="sxs-lookup"><span data-stu-id="d3efb-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="d3efb-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="d3efb-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="d3efb-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="d3efb-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="d3efb-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="d3efb-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)
