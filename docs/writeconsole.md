---
title: WriteConsole (funzione)
description: Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060480"
---
# <a name="writeconsole-function"></a><span data-ttu-id="aa10c-104">WriteConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="aa10c-104">WriteConsole function</span></span>


<span data-ttu-id="aa10c-105">Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="aa10c-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

<a name="syntax"></a><span data-ttu-id="aa10c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa10c-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a><span data-ttu-id="aa10c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="aa10c-107">Parameters</span></span>
----------

<span data-ttu-id="aa10c-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="aa10c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="aa10c-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="aa10c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="aa10c-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="aa10c-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="aa10c-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="aa10c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="aa10c-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="aa10c-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="aa10c-113">Puntatore a un buffer che contiene caratteri da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="aa10c-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="aa10c-114">*nNumberOfCharsToWrite* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="aa10c-114">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="aa10c-115">Numero di caratteri da scrivere.</span><span class="sxs-lookup"><span data-stu-id="aa10c-115">The number of characters to be written.</span></span> <span data-ttu-id="aa10c-116">Se la dimensione totale del numero specificato di caratteri supera l'heap disponibile, la funzione ha esito negativo e l' **errore non è sufficiente per la \_ \_ \_ memoria**.</span><span class="sxs-lookup"><span data-stu-id="aa10c-116">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="aa10c-117">*lpNumberOfCharsWritten* \[ out, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="aa10c-117">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="aa10c-118">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="aa10c-118">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="aa10c-119">*lpReserved* </span><span class="sxs-lookup"><span data-stu-id="aa10c-119">*lpReserved* </span></span>  
<span data-ttu-id="aa10c-120">Riservati deve essere **null**.</span><span class="sxs-lookup"><span data-stu-id="aa10c-120">Reserved; must be **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="aa10c-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="aa10c-121">Return value</span></span>
------------

<span data-ttu-id="aa10c-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="aa10c-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="aa10c-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="aa10c-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="aa10c-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="aa10c-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="aa10c-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="aa10c-125">Remarks</span></span>
-------

<span data-ttu-id="aa10c-126">La funzione **WriteConsole** scrive i caratteri nel buffer dello schermo della console in corrispondenza della posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="aa10c-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="aa10c-127">La posizione del cursore viene spostata come caratteri.</span><span class="sxs-lookup"><span data-stu-id="aa10c-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="aa10c-128">La funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) imposta la posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="aa10c-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="aa10c-129">I caratteri vengono scritti usando gli attributi del colore di primo piano e di sfondo associati al buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="aa10c-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="aa10c-130">La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifica questi colori.</span><span class="sxs-lookup"><span data-stu-id="aa10c-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="aa10c-131">Per determinare gli attributi di colore correnti e la posizione corrente del cursore, utilizzare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="aa10c-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="aa10c-132">Tutte le modalità di input che influiscono sul comportamento della funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) hanno lo stesso effetto su **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="aa10c-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="aa10c-133">Per recuperare e impostare le modalità di output di un buffer dello schermo della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="aa10c-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="aa10c-134">La funzione **WriteConsole** usa caratteri Unicode o ANSI dalla tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="aa10c-134">The **WriteConsole** function uses either Unicode characters or ANSI characters from the console's current code page.</span></span> <span data-ttu-id="aa10c-135">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="aa10c-135">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="aa10c-136">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="aa10c-136">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="aa10c-137">**WriteConsole** ha esito negativo se viene usato con un handle standard che viene reindirizzato a un file.</span><span class="sxs-lookup"><span data-stu-id="aa10c-137">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="aa10c-138">Se un'applicazione elabora l'output multilingue che può essere reindirizzato, determinare se l'handle di output è un handle della console (un metodo consiste nel chiamare la funzione [**GetConsoleMode**](getconsolemode.md) e controllare se ha esito positivo).</span><span class="sxs-lookup"><span data-stu-id="aa10c-138">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="aa10c-139">Se l'handle è un handle di console, chiamare **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="aa10c-139">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="aa10c-140">Se l'handle non è un handle di console, l'output viene reindirizzato ed è necessario chiamare [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) per eseguire l'i/O.</span><span class="sxs-lookup"><span data-stu-id="aa10c-140">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="aa10c-141">Assicurarsi di anteporre un prefisso a un file di testo normale Unicode con un byte order mark.</span><span class="sxs-lookup"><span data-stu-id="aa10c-141">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="aa10c-142">Per ulteriori informazioni, vedere [utilizzo dei byte order mark](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="aa10c-142">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="aa10c-143">Sebbene un'applicazione possa usare **WriteConsole** in modalità ANSI per scrivere caratteri ANSI, le console non supportano le sequenze di escape ANSI.</span><span class="sxs-lookup"><span data-stu-id="aa10c-143">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support ANSI escape sequences.</span></span> <span data-ttu-id="aa10c-144">Tuttavia, alcune funzioni forniscono funzionalità equivalenti.</span><span class="sxs-lookup"><span data-stu-id="aa10c-144">However, some functions provide equivalent functionality.</span></span> <span data-ttu-id="aa10c-145">Per ulteriori informazioni, vedere [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)e [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="aa10c-145">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

<a name="requirements"></a><span data-ttu-id="aa10c-146">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aa10c-146">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="aa10c-147">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa10c-147">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="aa10c-148">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="aa10c-148">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="aa10c-149">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="aa10c-149">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="aa10c-150">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="aa10c-150">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="aa10c-151">Intestazione</span><span class="sxs-lookup"><span data-stu-id="aa10c-151">Header</span></span></p></td>
<td><span data-ttu-id="aa10c-152">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="aa10c-152">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="aa10c-153">Libreria</span><span class="sxs-lookup"><span data-stu-id="aa10c-153">Library</span></span></p></td>
<td><span data-ttu-id="aa10c-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="aa10c-154">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="aa10c-155">DLL</span><span class="sxs-lookup"><span data-stu-id="aa10c-155">DLL</span></span></p></td>
<td><span data-ttu-id="aa10c-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="aa10c-156">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="aa10c-157">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="aa10c-157">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="aa10c-158"><strong>WriteConsoleW</strong> (Unicode) e <strong>WriteConsoleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="aa10c-158"><strong>WriteConsoleW</strong> (Unicode) and <strong>WriteConsoleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="aa10c-159"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa10c-159"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="aa10c-160">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="aa10c-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="aa10c-161">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="aa10c-161">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="aa10c-162">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="aa10c-162">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="aa10c-163">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="aa10c-163">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="aa10c-164">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="aa10c-164">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="aa10c-165">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="aa10c-165">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="aa10c-166">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="aa10c-166">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="aa10c-167">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="aa10c-167">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="aa10c-168">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="aa10c-168">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="aa10c-169">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="aa10c-169">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="aa10c-170">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="aa10c-170">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="aa10c-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="aa10c-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="aa10c-172">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="aa10c-172">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




