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
ms.openlocfilehash: 48671b9c54e61733c2936ac1f112e2d499f31a1a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357671"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="436f2-104">SetConsoleCursorPosition (funzione)</span><span class="sxs-lookup"><span data-stu-id="436f2-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="436f2-105">Imposta la posizione del cursore nel buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="436f2-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="436f2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="436f2-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="436f2-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="436f2-107">Parameters</span></span>

<span data-ttu-id="436f2-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="436f2-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="436f2-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="436f2-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="436f2-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="436f2-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="436f2-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="436f2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="436f2-112">*dwCursorPosition* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="436f2-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="436f2-113">Struttura [**Coord**](coord-str.md) che specifica la nuova posizione del cursore, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="436f2-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="436f2-114">Le coordinate sono la colonna e la riga di una cella del carattere del buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="436f2-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="436f2-115">Le coordinate devono trovarsi all'interno dei limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="436f2-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="436f2-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="436f2-116">Return value</span></span>

<span data-ttu-id="436f2-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="436f2-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="436f2-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="436f2-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="436f2-119">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="436f2-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="436f2-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="436f2-120">Remarks</span></span>

<span data-ttu-id="436f2-121">La posizione del cursore determina la posizione in cui vengono visualizzati i caratteri scritti dalla funzione [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md) o con la funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="436f2-121">The cursor position determines where characters written by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="436f2-122">Per determinare la posizione corrente del cursore, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="436f2-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="436f2-123">Se la nuova posizione del cursore non si trova all'interno dei limiti della finestra del buffer dello schermo della console, l'origine della finestra cambia per rendere visibile il cursore.</span><span class="sxs-lookup"><span data-stu-id="436f2-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="436f2-124">Questa API dispone di un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sezioni **[posizionamento semplice del cursore](console-virtual-terminal-sequences.md#simple-cursor-positioning)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="436f2-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="436f2-125">L'uso delle sequenze di nuova riga, ritorno a capo, BACKSPACE e controllo tab può supportare anche il posizionamento del cursore.</span><span class="sxs-lookup"><span data-stu-id="436f2-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="436f2-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="436f2-126">Examples</span></span>

<span data-ttu-id="436f2-127">Per un esempio, vedere [uso delle funzioni di input e output di High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="436f2-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="436f2-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="436f2-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="436f2-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="436f2-129">Minimum supported client</span></span> | <span data-ttu-id="436f2-130">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="436f2-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="436f2-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="436f2-131">Minimum supported server</span></span> | <span data-ttu-id="436f2-132">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="436f2-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="436f2-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="436f2-133">Header</span></span> | <span data-ttu-id="436f2-134">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="436f2-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="436f2-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="436f2-135">Library</span></span> | <span data-ttu-id="436f2-136">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="436f2-136">Kernel32.lib</span></span> |
| <span data-ttu-id="436f2-137">DLL</span><span class="sxs-lookup"><span data-stu-id="436f2-137">DLL</span></span> | <span data-ttu-id="436f2-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="436f2-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="436f2-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="436f2-139">See also</span></span>

[<span data-ttu-id="436f2-140">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="436f2-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="436f2-141">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="436f2-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="436f2-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="436f2-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="436f2-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="436f2-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="436f2-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="436f2-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="436f2-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="436f2-145">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="436f2-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="436f2-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="436f2-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="436f2-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="436f2-148">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="436f2-148">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)