---
title: GetConsoleDisplayMode (funzione)
description: Vedere informazioni di riferimento sulla funzione GetConsoleDisplayMode, che consente di recuperare la modalità di visualizzazione della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059812"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="ad29a-104">GetConsoleDisplayMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="ad29a-104">GetConsoleDisplayMode function</span></span>


<span data-ttu-id="ad29a-105">Recupera la modalità di visualizzazione della console corrente.</span><span class="sxs-lookup"><span data-stu-id="ad29a-105">Retrieves the display mode of the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="ad29a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ad29a-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a><span data-ttu-id="ad29a-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ad29a-107">Parameters</span></span>
----------

<span data-ttu-id="ad29a-108">*lpModeFlags* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="ad29a-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="ad29a-109">Modalità di visualizzazione della console.</span><span class="sxs-lookup"><span data-stu-id="ad29a-109">The display mode of the console.</span></span> <span data-ttu-id="ad29a-110">Il parametro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="ad29a-110">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="ad29a-111">valore</span><span class="sxs-lookup"><span data-stu-id="ad29a-111">Value</span></span></th>
<th><span data-ttu-id="ad29a-112">Significato</span><span class="sxs-lookup"><span data-stu-id="ad29a-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="ad29a-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span><span class="sxs-lookup"><span data-stu-id="ad29a-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span></span></td>
<td><p><span data-ttu-id="ad29a-114">Console a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="ad29a-114">Full-screen console.</span></span> <span data-ttu-id="ad29a-115">La console è in questa modalità non appena la finestra è ingrandita.</span><span class="sxs-lookup"><span data-stu-id="ad29a-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="ad29a-116">A questo punto, la transizione alla modalità schermo intero può comunque avere esito negativo.</span><span class="sxs-lookup"><span data-stu-id="ad29a-116">At this point, the transition to full-screen mode can still fail.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="ad29a-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="ad29a-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span></span></td>
<td><p><span data-ttu-id="ad29a-118">Console a schermo intero che comunica direttamente con l'hardware del video.</span><span class="sxs-lookup"><span data-stu-id="ad29a-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="ad29a-119">Questa modalità viene impostata dopo che la console è in modalità <strong>CONSOLE_FULLSCREEN</strong> per indicare che la transizione alla modalità schermo intero è stata completata.</span><span class="sxs-lookup"><span data-stu-id="ad29a-119">This mode is set after the console is in <strong>CONSOLE_FULLSCREEN</strong> mode to indicate that the transition to full-screen mode has completed.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="ad29a-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ad29a-120">Return value</span></span>
------------

<span data-ttu-id="ad29a-121">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="ad29a-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ad29a-122">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="ad29a-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ad29a-123">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ad29a-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ad29a-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ad29a-124">Remarks</span></span>
-------

<span data-ttu-id="ad29a-125">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ad29a-125">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="ad29a-126">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ad29a-126">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="ad29a-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ad29a-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ad29a-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ad29a-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ad29a-129">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ad29a-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ad29a-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ad29a-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ad29a-131">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ad29a-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ad29a-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="ad29a-132">Header</span></span></p></td>
<td><span data-ttu-id="ad29a-133">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ad29a-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ad29a-134">Libreria</span><span class="sxs-lookup"><span data-stu-id="ad29a-134">Library</span></span></p></td>
<td><span data-ttu-id="ad29a-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ad29a-135">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ad29a-136">DLL</span><span class="sxs-lookup"><span data-stu-id="ad29a-136">DLL</span></span></p></td>
<td><span data-ttu-id="ad29a-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ad29a-137">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ad29a-138"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad29a-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ad29a-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="ad29a-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ad29a-140">Modalità console</span><span class="sxs-lookup"><span data-stu-id="ad29a-140">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="ad29a-141">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="ad29a-141">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

 

 




