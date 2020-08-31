---
title: FreeConsole (funzione)
description: Vedere informazioni di riferimento sulla funzione FreeConsole, che scollega il processo chiamante dalla relativa console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059868"
---
# <a name="freeconsole-function"></a><span data-ttu-id="4e014-104">FreeConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="4e014-104">FreeConsole function</span></span>


<span data-ttu-id="4e014-105">Scollega il processo chiamante dalla relativa console.</span><span class="sxs-lookup"><span data-stu-id="4e014-105">Detaches the calling process from its console.</span></span>

<a name="syntax"></a><span data-ttu-id="4e014-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4e014-106">Syntax</span></span>
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a><span data-ttu-id="4e014-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4e014-107">Parameters</span></span>
----------

<span data-ttu-id="4e014-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="4e014-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="4e014-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4e014-109">Return value</span></span>
------------

<span data-ttu-id="4e014-110">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="4e014-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4e014-111">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="4e014-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4e014-112">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4e014-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4e014-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4e014-113">Remarks</span></span>
-------

<span data-ttu-id="4e014-114">Un processo può essere collegato al massimo da una console.</span><span class="sxs-lookup"><span data-stu-id="4e014-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="4e014-115">Se il processo chiamante non è già collegato a una console, il codice di errore restituito **è \_ errore \_ parametro non valido** (87).</span><span class="sxs-lookup"><span data-stu-id="4e014-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="4e014-116">Un processo può utilizzare la funzione **FreeConsole** per scollegarsi dalla console.</span><span class="sxs-lookup"><span data-stu-id="4e014-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="4e014-117">Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="4e014-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="4e014-118">Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="4e014-118">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="4e014-119">Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="4e014-119">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<a name="requirements"></a><span data-ttu-id="4e014-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4e014-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4e014-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4e014-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4e014-122">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="4e014-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4e014-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4e014-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4e014-124">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="4e014-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4e014-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4e014-125">Header</span></span></p></td>
<td><span data-ttu-id="4e014-126">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4e014-126">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4e014-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="4e014-127">Library</span></span></p></td>
<td><span data-ttu-id="4e014-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4e014-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4e014-129">DLL</span><span class="sxs-lookup"><span data-stu-id="4e014-129">DLL</span></span></p></td>
<td><span data-ttu-id="4e014-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4e014-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4e014-131"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4e014-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4e014-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="4e014-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="4e014-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="4e014-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="4e014-134">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="4e014-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4e014-135">Console</span><span class="sxs-lookup"><span data-stu-id="4e014-135">Consoles</span></span>](consoles.md)

 

 




