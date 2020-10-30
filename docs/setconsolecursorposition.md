---
title: SetConsoleCursorPosition (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleCursorPosition, che imposta la posizione del cursore nel buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039369"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="c744f-104">SetConsoleCursorPosition (funzione)</span><span class="sxs-lookup"><span data-stu-id="c744f-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c744f-105">Imposta la posizione del cursore nel buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="c744f-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="c744f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c744f-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="c744f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c744f-107">Parameters</span></span>

<span data-ttu-id="c744f-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c744f-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c744f-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c744f-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c744f-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="c744f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c744f-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c744f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c744f-112">*dwCursorPosition* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c744f-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="c744f-113">Struttura [**Coord**](coord-str.md) che specifica la nuova posizione del cursore, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="c744f-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="c744f-114">Le coordinate sono la colonna e la riga di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="c744f-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="c744f-115">Le coordinate devono trovarsi all'interno dei limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c744f-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="c744f-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c744f-116">Return value</span></span>

<span data-ttu-id="c744f-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="c744f-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c744f-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="c744f-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c744f-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c744f-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="c744f-120">Commenti</span><span class="sxs-lookup"><span data-stu-id="c744f-120">Remarks</span></span>

<span data-ttu-id="c744f-121">La posizione del cursore determina la posizione in cui vengono visualizzati i caratteri scritti dalla funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) o con la funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="c744f-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="c744f-122">Per determinare la posizione corrente del cursore, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="c744f-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="c744f-123">Se la nuova posizione del cursore non si trova all'interno dei limiti della finestra del buffer dello schermo della console, l'origine della finestra cambia per rendere visibile il cursore.</span><span class="sxs-lookup"><span data-stu-id="c744f-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="c744f-124">Questa API dispone di un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sezioni **[posizionamento semplice del cursore](console-virtual-terminal-sequences.md#simple-cursor-positioning)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="c744f-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="c744f-125">L'uso delle sequenze di nuova riga, ritorno a capo, BACKSPACE e controllo tab può supportare anche il posizionamento del cursore.</span><span class="sxs-lookup"><span data-stu-id="c744f-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="c744f-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="c744f-126">Examples</span></span>

<span data-ttu-id="c744f-127">Per un esempio, vedere [uso delle funzioni di input e output di High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c744f-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c744f-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c744f-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c744f-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c744f-129">Minimum supported client</span></span> | <span data-ttu-id="c744f-130">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="c744f-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c744f-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c744f-131">Minimum supported server</span></span> | <span data-ttu-id="c744f-132">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="c744f-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c744f-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c744f-133">Header</span></span> | <span data-ttu-id="c744f-134">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c744f-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c744f-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="c744f-135">Library</span></span> | <span data-ttu-id="c744f-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c744f-136">Kernel32.lib</span></span> |
| <span data-ttu-id="c744f-137">DLL</span><span class="sxs-lookup"><span data-stu-id="c744f-137">DLL</span></span> | <span data-ttu-id="c744f-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c744f-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c744f-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c744f-139">See also</span></span>

[<span data-ttu-id="c744f-140">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="c744f-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c744f-141">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="c744f-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="c744f-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="c744f-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="c744f-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="c744f-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="c744f-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="c744f-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="c744f-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="c744f-145">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="c744f-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="c744f-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="c744f-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="c744f-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="c744f-148">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="c744f-148">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
