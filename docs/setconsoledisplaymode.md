---
title: SetConsoleDisplayMode (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleDisplayMode, che imposta la modalità di visualizzazione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060105"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="ab138-104">SetConsoleDisplayMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="ab138-104">SetConsoleDisplayMode function</span></span>


<span data-ttu-id="ab138-105">Imposta la modalità di visualizzazione del buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="ab138-105">Sets the display mode of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ab138-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ab138-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a><span data-ttu-id="ab138-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ab138-107">Parameters</span></span>
----------

<span data-ttu-id="ab138-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ab138-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ab138-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="ab138-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="ab138-110">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ab138-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="ab138-111">Modalità di visualizzazione della console.</span><span class="sxs-lookup"><span data-stu-id="ab138-111">The display mode of the console.</span></span> <span data-ttu-id="ab138-112">Il parametro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="ab138-112">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="ab138-113">valore</span><span class="sxs-lookup"><span data-stu-id="ab138-113">Value</span></span></th>
<th><span data-ttu-id="ab138-114">Significato</span><span class="sxs-lookup"><span data-stu-id="ab138-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="ab138-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span><span class="sxs-lookup"><span data-stu-id="ab138-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span></span></td>
<td><p><span data-ttu-id="ab138-116">Il testo viene visualizzato in modalità schermo intero.</span><span class="sxs-lookup"><span data-stu-id="ab138-116">Text is displayed in full-screen mode.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="ab138-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="ab138-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span></span></td>
<td><p><span data-ttu-id="ab138-118">Il testo viene visualizzato in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="ab138-118">Text is displayed in a console window.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="ab138-119">*lpNewScreenBufferDimensions* \[ out, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="ab138-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="ab138-120">Puntatore a una struttura [**Coord**](coord-str.md) che riceve le nuove dimensioni del buffer dello schermo, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="ab138-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="ab138-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ab138-121">Return value</span></span>
------------

<span data-ttu-id="ab138-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="ab138-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ab138-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="ab138-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ab138-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ab138-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="ab138-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ab138-125">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ab138-126">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ab138-126">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ab138-127">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ab138-127">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ab138-128">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ab138-128">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ab138-129">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ab138-129">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ab138-130">Intestazione</span><span class="sxs-lookup"><span data-stu-id="ab138-130">Header</span></span></p></td>
<td><span data-ttu-id="ab138-131">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ab138-131">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ab138-132">Libreria</span><span class="sxs-lookup"><span data-stu-id="ab138-132">Library</span></span></p></td>
<td><span data-ttu-id="ab138-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ab138-133">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ab138-134">DLL</span><span class="sxs-lookup"><span data-stu-id="ab138-134">DLL</span></span></p></td>
<td><span data-ttu-id="ab138-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ab138-135">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ab138-136"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab138-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ab138-137">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="ab138-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ab138-138">Modalità console</span><span class="sxs-lookup"><span data-stu-id="ab138-138">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="ab138-139">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="ab138-139">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)

 

 




