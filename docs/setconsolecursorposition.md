---
title: SetConsoleCursorPosition (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleCursorPosition, che imposta la posizione del cursore nel buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060273"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="f4629-104">SetConsoleCursorPosition (funzione)</span><span class="sxs-lookup"><span data-stu-id="f4629-104">SetConsoleCursorPosition function</span></span>


<span data-ttu-id="f4629-105">Imposta la posizione del cursore nel buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="f4629-105">Sets the cursor position in the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="f4629-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f4629-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a><span data-ttu-id="f4629-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="f4629-107">Parameters</span></span>
----------

<span data-ttu-id="f4629-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f4629-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f4629-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f4629-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f4629-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="f4629-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f4629-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f4629-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f4629-112">*dwCursorPosition* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f4629-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="f4629-113">Struttura [**Coord**](coord-str.md) che specifica la nuova posizione del cursore, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="f4629-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="f4629-114">Le coordinate sono la colonna e la riga di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="f4629-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="f4629-115">Le coordinate devono trovarsi all'interno dei limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f4629-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="f4629-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f4629-116">Return value</span></span>
------------

<span data-ttu-id="f4629-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="f4629-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f4629-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="f4629-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f4629-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f4629-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f4629-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f4629-120">Remarks</span></span>
-------

<span data-ttu-id="f4629-121">La posizione del cursore determina la posizione in cui vengono visualizzati i caratteri scritti dalla funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) o con la funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="f4629-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="f4629-122">Per determinare la posizione corrente del cursore, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="f4629-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="f4629-123">Se la nuova posizione del cursore non si trova all'interno dei limiti della finestra del buffer dello schermo della console, l'origine della finestra cambia per rendere visibile il cursore.</span><span class="sxs-lookup"><span data-stu-id="f4629-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

<a name="examples"></a><span data-ttu-id="f4629-124">Esempi</span><span class="sxs-lookup"><span data-stu-id="f4629-124">Examples</span></span>
--------

<span data-ttu-id="f4629-125">Per un esempio, vedere [utilizzo delle funzioni di input e output di alto livello](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f4629-125">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="f4629-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f4629-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f4629-127">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f4629-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f4629-128">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f4629-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f4629-129">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f4629-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f4629-130">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f4629-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f4629-131">Intestazione</span><span class="sxs-lookup"><span data-stu-id="f4629-131">Header</span></span></p></td>
<td><span data-ttu-id="f4629-132">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f4629-132">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f4629-133">Libreria</span><span class="sxs-lookup"><span data-stu-id="f4629-133">Library</span></span></p></td>
<td><span data-ttu-id="f4629-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f4629-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f4629-135">DLL</span><span class="sxs-lookup"><span data-stu-id="f4629-135">DLL</span></span></p></td>
<td><span data-ttu-id="f4629-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f4629-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f4629-137"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f4629-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f4629-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="f4629-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f4629-139">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="f4629-139">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="f4629-140">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="f4629-140">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="f4629-141">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="f4629-141">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="f4629-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="f4629-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="f4629-143">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="f4629-143">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="f4629-144">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="f4629-144">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="f4629-145">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="f4629-145">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="f4629-146">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="f4629-146">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




