---
title: GenerateConsoleCtrlEvent (funzione)
description: Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059860"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="5f0a4-104">GenerateConsoleCtrlEvent (funzione)</span><span class="sxs-lookup"><span data-stu-id="5f0a4-104">GenerateConsoleCtrlEvent function</span></span>


<span data-ttu-id="5f0a4-105">Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="5f0a4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5f0a4-106">Syntax</span></span>
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a><span data-ttu-id="5f0a4-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5f0a4-107">Parameters</span></span>
----------

<span data-ttu-id="5f0a4-108">*dwCtrlEvent* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5f0a4-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="5f0a4-109">Tipo di segnale da generare.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-109">The type of signal to be generated.</span></span> <span data-ttu-id="5f0a4-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="5f0a4-111">valore</span><span class="sxs-lookup"><span data-stu-id="5f0a4-111">Value</span></span></th>
<th><span data-ttu-id="5f0a4-112">Significato</span><span class="sxs-lookup"><span data-stu-id="5f0a4-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="5f0a4-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span><span class="sxs-lookup"><span data-stu-id="5f0a4-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span></span></td>
<td><p><span data-ttu-id="5f0a4-114">Genera un segnale CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="5f0a4-115">Non è possibile generare questo segnale per i gruppi di processi.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="5f0a4-116">Se <em>dwProcessGroupId</em> è diverso da zero, questa funzione avrà esito positivo, ma il segnale CTRL + C non verrà ricevuto dai processi all'interno del gruppo di processi specificato.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-116">If <em>dwProcessGroupId</em> is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5f0a4-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span><span class="sxs-lookup"><span data-stu-id="5f0a4-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span></span></td>
<td><p><span data-ttu-id="5f0a4-118">Genera un segnale CTRL + BREAK.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-118">Generates a CTRL+BREAK signal.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="5f0a4-119">*dwProcessGroupId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5f0a4-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="5f0a4-120">Identificatore del gruppo di processi per ricevere il segnale.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="5f0a4-121">Un gruppo di processi viene creato quando il flag **Crea \_ nuovo \_ \_ gruppo di processi** viene specificato in una chiamata alla funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) .</span><span class="sxs-lookup"><span data-stu-id="5f0a4-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function.</span></span> <span data-ttu-id="5f0a4-122">L'identificatore del processo del nuovo processo è anche l'identificatore del gruppo di processi di un nuovo gruppo di processi.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="5f0a4-123">Il gruppo di processi include tutti i processi discendenti dal processo radice.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="5f0a4-124">Solo i processi del gruppo che condividono la stessa console del processo chiamante ricevono il segnale.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="5f0a4-125">In altre parole, se un processo del gruppo crea una nuova console, il processo non riceve il segnale, né i relativi discendenti.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="5f0a4-126">Se questo parametro è zero, il segnale viene generato in tutti i processi che condividono la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

<a name="return-value"></a><span data-ttu-id="5f0a4-127">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5f0a4-127">Return value</span></span>
------------

<span data-ttu-id="5f0a4-128">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5f0a4-129">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5f0a4-130">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5f0a4-130">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="5f0a4-131">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5f0a4-131">Remarks</span></span>
-------

<span data-ttu-id="5f0a4-132">**GenerateConsoleCtrlEvent** fa sì che vengano chiamate le funzioni del gestore di controllo dei processi nel gruppo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="5f0a4-133">Tutti i processi della console hanno una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="5f0a4-133">All console processes have a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="5f0a4-134">Un processo console può utilizzare la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) per installare o rimuovere altre funzioni del gestore.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="5f0a4-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) può anche abilitare un attributo ereditabile che fa in modo che il processo chiamante ignori i segnali CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="5f0a4-136">Se **GenerateConsoleCtrlEvent** Invia un segnale CTRL + C a un processo per il quale questo attributo è abilitato, le funzioni del gestore per tale processo non vengono chiamate.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="5f0a4-137">I segnali CTRL + BREAK determinano sempre la chiamata delle funzioni del gestore.</span><span class="sxs-lookup"><span data-stu-id="5f0a4-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

<a name="requirements"></a><span data-ttu-id="5f0a4-138">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5f0a4-138">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5f0a4-139">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5f0a4-139">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5f0a4-140">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5f0a4-140">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5f0a4-141">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5f0a4-141">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5f0a4-142">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5f0a4-142">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5f0a4-143">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5f0a4-143">Header</span></span></p></td>
<td><span data-ttu-id="5f0a4-144">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5f0a4-144">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5f0a4-145">Libreria</span><span class="sxs-lookup"><span data-stu-id="5f0a4-145">Library</span></span></p></td>
<td><span data-ttu-id="5f0a4-146">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5f0a4-146">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5f0a4-147">DLL</span><span class="sxs-lookup"><span data-stu-id="5f0a4-147">DLL</span></span></p></td>
<td><span data-ttu-id="5f0a4-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5f0a4-148">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5f0a4-149"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f0a4-149"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5f0a4-150">Gestori di controlli console</span><span class="sxs-lookup"><span data-stu-id="5f0a4-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="5f0a4-151">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="5f0a4-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5f0a4-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="5f0a4-152">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="5f0a4-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="5f0a4-153">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="5f0a4-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="5f0a4-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)

 

 




