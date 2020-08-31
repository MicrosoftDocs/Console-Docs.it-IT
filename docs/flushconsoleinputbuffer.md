---
title: FlushConsoleInputBuffer (funzione)
description: Svuota il buffer di input della console. Tutti i record di input attualmente presenti nel buffer di input vengono eliminati.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059876"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="30497-105">FlushConsoleInputBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="30497-105">FlushConsoleInputBuffer function</span></span>


<span data-ttu-id="30497-106">Svuota il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="30497-106">Flushes the console input buffer.</span></span> <span data-ttu-id="30497-107">Tutti i record di input attualmente presenti nel buffer di input vengono eliminati.</span><span class="sxs-lookup"><span data-stu-id="30497-107">All input records currently in the input buffer are discarded.</span></span>

<a name="syntax"></a><span data-ttu-id="30497-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="30497-108">Syntax</span></span>
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a><span data-ttu-id="30497-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="30497-109">Parameters</span></span>
----------

<span data-ttu-id="30497-110">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="30497-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="30497-111">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="30497-111">A handle to the console input buffer.</span></span> <span data-ttu-id="30497-112">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="30497-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="30497-113">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="30497-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<a name="return-value"></a><span data-ttu-id="30497-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="30497-114">Return value</span></span>
------------

<span data-ttu-id="30497-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="30497-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="30497-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="30497-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="30497-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="30497-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="30497-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="30497-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="30497-119">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="30497-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="30497-120">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="30497-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="30497-121">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="30497-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="30497-122">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="30497-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="30497-123">Intestazione</span><span class="sxs-lookup"><span data-stu-id="30497-123">Header</span></span></p></td>
<td><span data-ttu-id="30497-124">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="30497-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="30497-125">Libreria</span><span class="sxs-lookup"><span data-stu-id="30497-125">Library</span></span></p></td>
<td><span data-ttu-id="30497-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="30497-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="30497-127">DLL</span><span class="sxs-lookup"><span data-stu-id="30497-127">DLL</span></span></p></td>
<td><span data-ttu-id="30497-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="30497-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="30497-129"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="30497-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="30497-130">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="30497-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="30497-131">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="30497-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="30497-132">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="30497-132">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="30497-133">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="30497-133">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="30497-134">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="30497-134">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="30497-135">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="30497-135">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




