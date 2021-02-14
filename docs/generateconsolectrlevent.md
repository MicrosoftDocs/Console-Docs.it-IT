---
title: GenerateConsoleCtrlEvent (funzione)
description: Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357531"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="fff43-104">GenerateConsoleCtrlEvent (funzione)</span><span class="sxs-lookup"><span data-stu-id="fff43-104">GenerateConsoleCtrlEvent function</span></span>

<span data-ttu-id="fff43-105">Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="fff43-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="fff43-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fff43-106">Syntax</span></span>

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a><span data-ttu-id="fff43-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="fff43-107">Parameters</span></span>

<span data-ttu-id="fff43-108">*dwCtrlEvent* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fff43-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="fff43-109">Tipo di segnale da generare.</span><span class="sxs-lookup"><span data-stu-id="fff43-109">The type of signal to be generated.</span></span> <span data-ttu-id="fff43-110">Questo parametro può avere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="fff43-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="fff43-111">Valore</span><span class="sxs-lookup"><span data-stu-id="fff43-111">Value</span></span> | <span data-ttu-id="fff43-112">Significato</span><span class="sxs-lookup"><span data-stu-id="fff43-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="fff43-113">**CTRL_C_EVENT** 0</span><span class="sxs-lookup"><span data-stu-id="fff43-113">**CTRL_C_EVENT** 0</span></span> | <span data-ttu-id="fff43-114">Genera un segnale CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="fff43-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="fff43-115">Non è possibile generare questo segnale per i gruppi di processi.</span><span class="sxs-lookup"><span data-stu-id="fff43-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="fff43-116">Se *dwProcessGroupId* è diverso da zero, questa funzione avrà esito positivo, ma il segnale CTRL + C non verrà ricevuto dai processi all'interno del gruppo di processi specificato.</span><span class="sxs-lookup"><span data-stu-id="fff43-116">If *dwProcessGroupId* is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span> |
| <span data-ttu-id="fff43-117">**CTRL_BREAK_EVENT** 1</span><span class="sxs-lookup"><span data-stu-id="fff43-117">**CTRL_BREAK_EVENT** 1</span></span> | <span data-ttu-id="fff43-118">Genera un segnale CTRL + BREAK.</span><span class="sxs-lookup"><span data-stu-id="fff43-118">Generates a CTRL+BREAK signal.</span></span> |

<span data-ttu-id="fff43-119">*dwProcessGroupId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fff43-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="fff43-120">Identificatore del gruppo di processi per ricevere il segnale.</span><span class="sxs-lookup"><span data-stu-id="fff43-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="fff43-121">Un gruppo di processi viene creato quando il flag **Crea \_ nuovo \_ \_ gruppo di processi** viene specificato in una chiamata alla funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) .</span><span class="sxs-lookup"><span data-stu-id="fff43-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function.</span></span> <span data-ttu-id="fff43-122">L'identificatore del processo del nuovo processo è anche l'identificatore del gruppo di processi di un nuovo gruppo di processi.</span><span class="sxs-lookup"><span data-stu-id="fff43-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="fff43-123">Il gruppo di processi include tutti i processi discendenti dal processo radice.</span><span class="sxs-lookup"><span data-stu-id="fff43-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="fff43-124">Solo i processi del gruppo che condividono la stessa console del processo chiamante ricevono il segnale.</span><span class="sxs-lookup"><span data-stu-id="fff43-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="fff43-125">In altre parole, se un processo del gruppo crea una nuova console, il processo non riceve il segnale, né i relativi discendenti.</span><span class="sxs-lookup"><span data-stu-id="fff43-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="fff43-126">Se questo parametro è zero, il segnale viene generato in tutti i processi che condividono la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="fff43-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

## <a name="return-value"></a><span data-ttu-id="fff43-127">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="fff43-127">Return value</span></span>

<span data-ttu-id="fff43-128">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="fff43-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fff43-129">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="fff43-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fff43-130">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="fff43-130">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="fff43-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fff43-131">Remarks</span></span>

<span data-ttu-id="fff43-132">**GenerateConsoleCtrlEvent** fa sì che vengano chiamate le funzioni del gestore di controllo dei processi nel gruppo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="fff43-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="fff43-133">Tutti i processi della console hanno una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) .</span><span class="sxs-lookup"><span data-stu-id="fff43-133">All console processes have a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="fff43-134">Un processo console può utilizzare la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) per installare o rimuovere altre funzioni del gestore.</span><span class="sxs-lookup"><span data-stu-id="fff43-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="fff43-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) può anche abilitare un attributo ereditabile che fa in modo che il processo chiamante ignori i segnali CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="fff43-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="fff43-136">Se **GenerateConsoleCtrlEvent** Invia un segnale CTRL + C a un processo per il quale questo attributo è abilitato, le funzioni del gestore per tale processo non vengono chiamate.</span><span class="sxs-lookup"><span data-stu-id="fff43-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="fff43-137">I segnali CTRL + BREAK determinano sempre la chiamata delle funzioni del gestore.</span><span class="sxs-lookup"><span data-stu-id="fff43-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

## <a name="requirements"></a><span data-ttu-id="fff43-138">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fff43-138">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fff43-139">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fff43-139">Minimum supported client</span></span> | <span data-ttu-id="fff43-140">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="fff43-140">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fff43-141">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fff43-141">Minimum supported server</span></span> | <span data-ttu-id="fff43-142">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="fff43-142">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fff43-143">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fff43-143">Header</span></span> | <span data-ttu-id="fff43-144">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fff43-144">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fff43-145">Libreria</span><span class="sxs-lookup"><span data-stu-id="fff43-145">Library</span></span> | <span data-ttu-id="fff43-146">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="fff43-146">Kernel32.lib</span></span> |
| <span data-ttu-id="fff43-147">DLL</span><span class="sxs-lookup"><span data-stu-id="fff43-147">DLL</span></span> | <span data-ttu-id="fff43-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fff43-148">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="fff43-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fff43-149">See also</span></span>

[<span data-ttu-id="fff43-150">Gestori di controllo della console</span><span class="sxs-lookup"><span data-stu-id="fff43-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="fff43-151">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="fff43-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fff43-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="fff43-152">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="fff43-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="fff43-153">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="fff43-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="fff43-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)