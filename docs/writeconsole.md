---
title: WriteConsole (funzione)
description: Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9023372cf585e9b3645e7dc0a54e46a665935ad4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037129"
---
# <a name="writeconsole-function"></a><span data-ttu-id="62cfc-104">WriteConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="62cfc-104">WriteConsole function</span></span>

<span data-ttu-id="62cfc-105">Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="62cfc-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="62cfc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="62cfc-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="62cfc-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="62cfc-107">Parameters</span></span>

<span data-ttu-id="62cfc-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="62cfc-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="62cfc-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="62cfc-110">L'handle deve avere il diritto di accesso in **\_ scrittura generico** .</span><span class="sxs-lookup"><span data-stu-id="62cfc-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="62cfc-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="62cfc-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="62cfc-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="62cfc-113">Puntatore a un buffer che contiene caratteri da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="62cfc-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="62cfc-114">È previsto che sia una matrice di `char` per `WriteConsoleA` o `wchar_t` per `WriteConsoleW` .</span><span class="sxs-lookup"><span data-stu-id="62cfc-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="62cfc-115">*nNumberOfCharsToWrite* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="62cfc-116">Numero di caratteri da scrivere.</span><span class="sxs-lookup"><span data-stu-id="62cfc-116">The number of characters to be written.</span></span> <span data-ttu-id="62cfc-117">Se la dimensione totale del numero specificato di caratteri supera l'heap disponibile, la funzione ha esito negativo e l' **errore non è sufficiente per la \_ \_ \_ memoria** .</span><span class="sxs-lookup"><span data-stu-id="62cfc-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY** .</span></span>

<span data-ttu-id="62cfc-118">*lpNumberOfCharsWritten* \[ out, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="62cfc-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="62cfc-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="62cfc-120">*lpReserved* Riservati deve essere **null** .</span><span class="sxs-lookup"><span data-stu-id="62cfc-120">*lpReserved* Reserved; must be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="62cfc-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="62cfc-121">Return value</span></span>

<span data-ttu-id="62cfc-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="62cfc-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="62cfc-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="62cfc-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="62cfc-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="62cfc-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="62cfc-125">Commenti</span><span class="sxs-lookup"><span data-stu-id="62cfc-125">Remarks</span></span>

<span data-ttu-id="62cfc-126">La funzione **WriteConsole** scrive i caratteri nel buffer dello schermo della console in corrispondenza della posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="62cfc-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="62cfc-127">La posizione del cursore viene spostata come caratteri.</span><span class="sxs-lookup"><span data-stu-id="62cfc-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="62cfc-128">La funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) imposta la posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="62cfc-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="62cfc-129">I caratteri vengono scritti usando gli attributi del colore di primo piano e di sfondo associati al buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="62cfc-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="62cfc-130">La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifica questi colori.</span><span class="sxs-lookup"><span data-stu-id="62cfc-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="62cfc-131">Per determinare gli attributi di colore correnti e la posizione corrente del cursore, utilizzare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="62cfc-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="62cfc-132">Tutte le modalità di input che influiscono sul comportamento della funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) hanno lo stesso effetto su **WriteConsole** .</span><span class="sxs-lookup"><span data-stu-id="62cfc-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole** .</span></span> <span data-ttu-id="62cfc-133">Per recuperare e impostare le modalità di output di un buffer dello schermo della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="62cfc-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="62cfc-134">**WriteConsole** ha esito negativo se viene usato con un handle standard che viene reindirizzato a un file.</span><span class="sxs-lookup"><span data-stu-id="62cfc-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="62cfc-135">Se un'applicazione elabora l'output multilingue che può essere reindirizzato, determinare se l'handle di output è un handle della console (un metodo consiste nel chiamare la funzione [**GetConsoleMode**](getconsolemode.md) e controllare se ha esito positivo).</span><span class="sxs-lookup"><span data-stu-id="62cfc-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="62cfc-136">Se l'handle è un handle di console, chiamare **WriteConsole** .</span><span class="sxs-lookup"><span data-stu-id="62cfc-136">If the handle is a console handle, call **WriteConsole** .</span></span> <span data-ttu-id="62cfc-137">Se l'handle non è un handle di console, l'output viene reindirizzato ed è necessario chiamare [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) per eseguire l'i/O.</span><span class="sxs-lookup"><span data-stu-id="62cfc-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="62cfc-138">Assicurarsi di anteporre un prefisso a un file di testo normale Unicode con un byte order mark.</span><span class="sxs-lookup"><span data-stu-id="62cfc-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="62cfc-139">Per ulteriori informazioni, vedere [utilizzo dei byte order mark](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="62cfc-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="62cfc-140">Sebbene un'applicazione possa usare **WriteConsole** in modalità ANSI per scrivere caratteri ANSI, le console di non supportano le sequenze "escape ANSI" o "terminale virtuale", a meno che non siano abilitate.</span><span class="sxs-lookup"><span data-stu-id="62cfc-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="62cfc-141">Per ulteriori informazioni e per l'applicabilità della versione del sistema operativo, vedere [**sequenze di terminali virtuali della console**](console-virtual-terminal-sequences.md) .</span><span class="sxs-lookup"><span data-stu-id="62cfc-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="62cfc-142">Quando le sequenze di escape di terminali virtuali non sono abilitate, le funzioni della console possono fornire funzionalità equivalenti.</span><span class="sxs-lookup"><span data-stu-id="62cfc-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="62cfc-143">Per ulteriori informazioni, vedere [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)e [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="62cfc-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="62cfc-144">Requisiti</span><span class="sxs-lookup"><span data-stu-id="62cfc-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="62cfc-145">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="62cfc-145">Minimum supported client</span></span> | <span data-ttu-id="62cfc-146">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="62cfc-147">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="62cfc-147">Minimum supported server</span></span> | <span data-ttu-id="62cfc-148">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="62cfc-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="62cfc-149">Intestazione</span><span class="sxs-lookup"><span data-stu-id="62cfc-149">Header</span></span> | <span data-ttu-id="62cfc-150">ConsoleApi. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="62cfc-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="62cfc-151">Libreria</span><span class="sxs-lookup"><span data-stu-id="62cfc-151">Library</span></span> | <span data-ttu-id="62cfc-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="62cfc-152">Kernel32.lib</span></span> |
| <span data-ttu-id="62cfc-153">DLL</span><span class="sxs-lookup"><span data-stu-id="62cfc-153">DLL</span></span> | <span data-ttu-id="62cfc-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="62cfc-154">Kernel32.dll</span></span> |
| <span data-ttu-id="62cfc-155">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="62cfc-155">Unicode and ANSI names</span></span> | <span data-ttu-id="62cfc-156">**WriteConsoleW** (Unicode) e **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="62cfc-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="62cfc-157">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="62cfc-157">See also</span></span>

[<span data-ttu-id="62cfc-158">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="62cfc-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="62cfc-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="62cfc-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="62cfc-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="62cfc-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="62cfc-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="62cfc-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="62cfc-162">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="62cfc-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="62cfc-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="62cfc-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="62cfc-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="62cfc-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="62cfc-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="62cfc-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="62cfc-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="62cfc-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="62cfc-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="62cfc-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="62cfc-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="62cfc-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="62cfc-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="62cfc-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="62cfc-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="62cfc-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
