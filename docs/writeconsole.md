---
title: Funzione WriteConsole
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
ms.localizationpriority: high
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357611"
---
# <a name="writeconsole-function"></a><span data-ttu-id="14471-104">Funzione WriteConsole</span><span class="sxs-lookup"><span data-stu-id="14471-104">WriteConsole function</span></span>

<span data-ttu-id="14471-105">Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="14471-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="14471-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="14471-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="14471-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="14471-107">Parameters</span></span>

<span data-ttu-id="14471-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="14471-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="14471-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="14471-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="14471-110">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="14471-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="14471-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="14471-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="14471-112">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="14471-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="14471-113">Puntatore a un buffer che contiene caratteri da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="14471-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="14471-114">È previsto che sia una matrice di `char` per `WriteConsoleA` o `wchar_t` per `WriteConsoleW`.</span><span class="sxs-lookup"><span data-stu-id="14471-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="14471-115">*nNumberOfCharsToWrite* \[in\]</span><span class="sxs-lookup"><span data-stu-id="14471-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="14471-116">Numero di caratteri da scrivere.</span><span class="sxs-lookup"><span data-stu-id="14471-116">The number of characters to be written.</span></span> <span data-ttu-id="14471-117">Se la dimensione totale del numero specificato di caratteri supera l'heap disponibile, la funzione avrà esito negativo con **ERROR\_NOT\_ENOUGH\_MEMORY**.</span><span class="sxs-lookup"><span data-stu-id="14471-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="14471-118">*lpNumberOfCharsWritten* \[out, optional\]</span><span class="sxs-lookup"><span data-stu-id="14471-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="14471-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="14471-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="14471-120">*lpReserved* riservato; deve essere **NULL**.</span><span class="sxs-lookup"><span data-stu-id="14471-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="14471-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="14471-121">Return value</span></span>

<span data-ttu-id="14471-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="14471-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="14471-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="14471-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="14471-124">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="14471-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="14471-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="14471-125">Remarks</span></span>

<span data-ttu-id="14471-126">La funzione **WriteConsole** scrive i caratteri nel buffer dello schermo della console in corrispondenza della posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="14471-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="14471-127">La posizione del cursore viene spostata man mano che i caratteri vengono scritti.</span><span class="sxs-lookup"><span data-stu-id="14471-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="14471-128">La funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) imposta la posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="14471-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="14471-129">I caratteri vengono scritti usando gli attributi del colore di primo piano e di sfondo associati al buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="14471-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="14471-130">La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifica questi colori.</span><span class="sxs-lookup"><span data-stu-id="14471-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="14471-131">Per determinare gli attributi di colore correnti e la posizione corrente del cursore, usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="14471-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="14471-132">Tutte le modalità di input che influiscono sul comportamento della funzione [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) hanno lo stesso effetto su **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="14471-132">All of the input modes that affect the behavior of the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="14471-133">Per recuperare e impostare le modalità di output di un buffer dello schermo della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="14471-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="14471-134">**WriteConsole** ha esito negativo se viene usata con un handle standard che viene reindirizzato a un file.</span><span class="sxs-lookup"><span data-stu-id="14471-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="14471-135">Se un'applicazione elabora l'output multilingue che può essere reindirizzato, determinare se l'handle di output è un handle della console (un metodo consiste nel chiamare la funzione [**GetConsoleMode**](getconsolemode.md) e verificare se l'operazione ha esito positivo).</span><span class="sxs-lookup"><span data-stu-id="14471-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="14471-136">Se l'handle è un handle della console, chiamare **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="14471-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="14471-137">Se l'handle non è un handle della console, l'output viene reindirizzato ed è necessario chiamare [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) per eseguire le funzioni di I/O.</span><span class="sxs-lookup"><span data-stu-id="14471-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) to perform the I/O.</span></span> <span data-ttu-id="14471-138">Assicurarsi di anteporre un prefisso a un file di testo normale Unicode con un indicatore dell'ordine dei byte.</span><span class="sxs-lookup"><span data-stu-id="14471-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="14471-139">Per altre informazioni, vedere [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks) (Uso degli indicatori dell'ordine dei byte).</span><span class="sxs-lookup"><span data-stu-id="14471-139">For more information, see [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks).</span></span>

<span data-ttu-id="14471-140">Sebbene un'applicazione possa usare **WriteConsole** in modalità ANSI per scrivere caratteri ANSI, le console non supportano le sequenze di "escape ANSI" o "terminale virtuale", a meno che non siano abilitate.</span><span class="sxs-lookup"><span data-stu-id="14471-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="14471-141">Per altre informazioni e per l'applicabilità della versione del sistema operativo, vedere [**Sequenze del terminale virtuale della console**](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="14471-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="14471-142">Quando le sequenze di escape del terminale virtuale non sono abilitate, le funzioni della console possono fornire funzionalità equivalenti.</span><span class="sxs-lookup"><span data-stu-id="14471-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="14471-143">Per altre informazioni, vedere [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) e [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="14471-143">For more information, see [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="14471-144">Requisiti</span><span class="sxs-lookup"><span data-stu-id="14471-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="14471-145">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="14471-145">Minimum supported client</span></span> | <span data-ttu-id="14471-146">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="14471-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="14471-147">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="14471-147">Minimum supported server</span></span> | <span data-ttu-id="14471-148">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="14471-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="14471-149">Intestazione</span><span class="sxs-lookup"><span data-stu-id="14471-149">Header</span></span> | <span data-ttu-id="14471-150">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="14471-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="14471-151">Libreria</span><span class="sxs-lookup"><span data-stu-id="14471-151">Library</span></span> | <span data-ttu-id="14471-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="14471-152">Kernel32.lib</span></span> |
| <span data-ttu-id="14471-153">DLL</span><span class="sxs-lookup"><span data-stu-id="14471-153">DLL</span></span> | <span data-ttu-id="14471-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="14471-154">Kernel32.dll</span></span> |
| <span data-ttu-id="14471-155">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="14471-155">Unicode and ANSI names</span></span> | <span data-ttu-id="14471-156">**WriteConsoleW** (Unicode) e **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="14471-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="14471-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="14471-157">See also</span></span>

[<span data-ttu-id="14471-158">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="14471-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="14471-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="14471-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="14471-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="14471-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="14471-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="14471-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="14471-162">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="14471-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="14471-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="14471-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="14471-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="14471-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="14471-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="14471-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="14471-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="14471-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="14471-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="14471-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="14471-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="14471-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="14471-169">**SetCursorPos**</span><span class="sxs-lookup"><span data-stu-id="14471-169">**SetCursorPos**</span></span>](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[<span data-ttu-id="14471-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="14471-170">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)