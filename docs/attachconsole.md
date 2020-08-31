---
title: AttachConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AttachConsole, che consente di alleghi il processo chiamante alla console del processo specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060233"
---
# <a name="attachconsole-function"></a><span data-ttu-id="39c32-104">AttachConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="39c32-104">AttachConsole function</span></span>


<span data-ttu-id="39c32-105">Connette il processo chiamante alla console del processo specificato.</span><span class="sxs-lookup"><span data-stu-id="39c32-105">Attaches the calling process to the console of the specified process.</span></span>

<a name="syntax"></a><span data-ttu-id="39c32-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39c32-106">Syntax</span></span>
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a><span data-ttu-id="39c32-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="39c32-107">Parameters</span></span>
----------

<span data-ttu-id="39c32-108">*dwProcessId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="39c32-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="39c32-109">Identificatore del processo di cui si desidera utilizzare la console.</span><span class="sxs-lookup"><span data-stu-id="39c32-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="39c32-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="39c32-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="39c32-111">valore</span><span class="sxs-lookup"><span data-stu-id="39c32-111">Value</span></span></th>
<th><span data-ttu-id="39c32-112">Significato</span><span class="sxs-lookup"><span data-stu-id="39c32-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="39c32-113"><em>PID</em></span><span class="sxs-lookup"><span data-stu-id="39c32-113"><em>pid</em></span></span></td>
<td><p><span data-ttu-id="39c32-114">Utilizzare la console del processo specificato.</span><span class="sxs-lookup"><span data-stu-id="39c32-114">Use the console of the specified process.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="39c32-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span><span class="sxs-lookup"><span data-stu-id="39c32-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span></span></td>
<td><p><span data-ttu-id="39c32-116">Utilizzare la console dell'elemento padre del processo corrente.</span><span class="sxs-lookup"><span data-stu-id="39c32-116">Use the console of the parent of the current process.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="39c32-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="39c32-117">Return value</span></span>
------------

<span data-ttu-id="39c32-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="39c32-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="39c32-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="39c32-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="39c32-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="39c32-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="39c32-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="39c32-121">Remarks</span></span>
-------

<span data-ttu-id="39c32-122">Un processo può essere collegato al massimo da una console.</span><span class="sxs-lookup"><span data-stu-id="39c32-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="39c32-123">Se il processo chiamante è già collegato a una console, il codice di errore restituito è **errore \_ accesso \_ negato** (5).</span><span class="sxs-lookup"><span data-stu-id="39c32-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5).</span></span> <span data-ttu-id="39c32-124">Se il processo specificato non dispone di una console, il codice di errore restituito **è \_ errore \_ handle non valido** (6).</span><span class="sxs-lookup"><span data-stu-id="39c32-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6).</span></span> <span data-ttu-id="39c32-125">Se il processo specificato non esiste, il codice di errore restituito è **errore \_ \_ parametro non valido** (87).</span><span class="sxs-lookup"><span data-stu-id="39c32-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="39c32-126">Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console.</span><span class="sxs-lookup"><span data-stu-id="39c32-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="39c32-127">Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="39c32-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="39c32-128">Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="39c32-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="39c32-129">Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o **AttachConsole** per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="39c32-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="39c32-130">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="39c32-130">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="39c32-131">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="39c32-131">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="39c32-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="39c32-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="39c32-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="39c32-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="39c32-134">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="39c32-134">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="39c32-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="39c32-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="39c32-136">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="39c32-136">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="39c32-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="39c32-137">Header</span></span></p></td>
<td><span data-ttu-id="39c32-138">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="39c32-138">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="39c32-139">Libreria</span><span class="sxs-lookup"><span data-stu-id="39c32-139">Library</span></span></p></td>
<td><span data-ttu-id="39c32-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="39c32-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="39c32-141">DLL</span><span class="sxs-lookup"><span data-stu-id="39c32-141">DLL</span></span></p></td>
<td><span data-ttu-id="39c32-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="39c32-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="39c32-143"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39c32-143"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="39c32-144">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="39c32-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="39c32-145">Console</span><span class="sxs-lookup"><span data-stu-id="39c32-145">Consoles</span></span>](consoles.md)

[<span data-ttu-id="39c32-146">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="39c32-146">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="39c32-147">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="39c32-147">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="39c32-148">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="39c32-148">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

 

 




