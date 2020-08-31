---
title: ReadConsole (funzione)
description: Legge l'input di caratteri dal buffer di input della console e lo rimuove dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059577"
---
# <a name="readconsole-function"></a><span data-ttu-id="6c274-104">ReadConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="6c274-104">ReadConsole function</span></span>


<span data-ttu-id="6c274-105">Legge l'input di caratteri dal buffer di input della console e lo rimuove dal buffer.</span><span class="sxs-lookup"><span data-stu-id="6c274-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="6c274-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6c274-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a><span data-ttu-id="6c274-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="6c274-107">Parameters</span></span>
----------

<span data-ttu-id="6c274-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6c274-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="6c274-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="6c274-109">A handle to the console input buffer.</span></span> <span data-ttu-id="6c274-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="6c274-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6c274-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6c274-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6c274-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="6c274-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="6c274-113">Puntatore a un buffer che riceve i dati letti dal buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="6c274-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="6c274-114">*nNumberOfCharsToRead* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6c274-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="6c274-115">Numero di caratteri da leggere.</span><span class="sxs-lookup"><span data-stu-id="6c274-115">The number of characters to be read.</span></span> <span data-ttu-id="6c274-116">La dimensione del buffer a cui punta il parametro *lpBuffer* deve essere di almeno `nNumberOfCharsToRead * sizeof(TCHAR)` byte.</span><span class="sxs-lookup"><span data-stu-id="6c274-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="6c274-117">*lpNumberOfCharsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="6c274-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="6c274-118">Puntatore a una variabile che riceve il numero di caratteri effettivamente letti.</span><span class="sxs-lookup"><span data-stu-id="6c274-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="6c274-119">*pInputControl* \[ in, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="6c274-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="6c274-120">Puntatore a una struttura [**di \_ \_ controllo READCONSOLE della console**](console-readconsole-control.md) che specifica un carattere di controllo per segnalare la fine dell'operazione di lettura.</span><span class="sxs-lookup"><span data-stu-id="6c274-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="6c274-121">Questo parametro può essere **null**.</span><span class="sxs-lookup"><span data-stu-id="6c274-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="6c274-122">Per impostazione predefinita, questo parametro richiede l'input Unicode.</span><span class="sxs-lookup"><span data-stu-id="6c274-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="6c274-123">Per la modalità ANSI, impostare questo parametro su **null**.</span><span class="sxs-lookup"><span data-stu-id="6c274-123">For ANSI mode, set this parameter to **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="6c274-124">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6c274-124">Return value</span></span>
------------

<span data-ttu-id="6c274-125">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="6c274-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6c274-126">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="6c274-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6c274-127">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6c274-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="6c274-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6c274-128">Remarks</span></span>
-------

<span data-ttu-id="6c274-129">**ReadConsole** legge l'input da tastiera da un buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="6c274-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="6c274-130">Si comporta come la funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , ad eccezione del fatto che può leggere in modalità Unicode (wide character) o ANSI.</span><span class="sxs-lookup"><span data-stu-id="6c274-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="6c274-131">Per avere applicazioni che gestiscono un singolo set di origini compatibili con entrambe le modalità, usare **ReadConsole** anziché **ReadFile**.</span><span class="sxs-lookup"><span data-stu-id="6c274-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="6c274-132">Sebbene **ReadConsole** possa essere usato solo con un handle del buffer di input della console, **ReadFile** può essere usato con altri handle, ad esempio file o pipe.</span><span class="sxs-lookup"><span data-stu-id="6c274-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="6c274-133">**ReadConsole** ha esito negativo se usato con un handle standard che è stato reindirizzato a un elemento diverso da un handle di console.</span><span class="sxs-lookup"><span data-stu-id="6c274-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="6c274-134">Tutte le modalità di input che influiscono sul comportamento di [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) hanno lo stesso effetto su **ReadConsole**.</span><span class="sxs-lookup"><span data-stu-id="6c274-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="6c274-135">Per recuperare e impostare le modalità di input di un buffer di input della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="6c274-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="6c274-136">Se il buffer di input contiene eventi di input diversi dagli eventi di tastiera, ad esempio gli eventi del mouse o gli eventi di ridimensionamento delle finestre, vengono eliminati.</span><span class="sxs-lookup"><span data-stu-id="6c274-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="6c274-137">Questi eventi possono essere letti solo tramite la funzione [**ReadConsoleInput**](readconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="6c274-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

<span data-ttu-id="6c274-138">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="6c274-138">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="6c274-139">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="6c274-139">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="6c274-140">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="6c274-140">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="6c274-141">Il parametro *pInputControl* può essere usato per abilitare riattivazioni intermedie dalla lettura in risposta a un carattere di controllo di completamento file specificato in una struttura di [\*\* \_ \_ controllo READCONSOLE console\*\*](console-readconsole-control.md) .</span><span class="sxs-lookup"><span data-stu-id="6c274-141">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="6c274-142">Questa funzionalità richiede l'abilitazione delle estensioni del comando, l'handle di output standard come handle di output della console e l'input come Unicode.</span><span class="sxs-lookup"><span data-stu-id="6c274-142">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="6c274-143">**Windows Server 2003 e Windows XP/2000:** La funzionalità di lettura intermedia non è supportata.</span><span class="sxs-lookup"><span data-stu-id="6c274-143">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

<a name="requirements"></a><span data-ttu-id="6c274-144">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6c274-144">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6c274-145">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6c274-145">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6c274-146">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6c274-146">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c274-147">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6c274-147">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6c274-148">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="6c274-148">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c274-149">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6c274-149">Header</span></span></p></td>
<td><span data-ttu-id="6c274-150">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6c274-150">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c274-151">Libreria</span><span class="sxs-lookup"><span data-stu-id="6c274-151">Library</span></span></p></td>
<td><span data-ttu-id="6c274-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6c274-152">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c274-153">DLL</span><span class="sxs-lookup"><span data-stu-id="6c274-153">DLL</span></span></p></td>
<td><span data-ttu-id="6c274-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6c274-154">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c274-155">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="6c274-155">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="6c274-156"><strong>ReadConsoleW</strong> (Unicode) e <strong>ReadConsoleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="6c274-156"><strong>ReadConsoleW</strong> (Unicode) and <strong>ReadConsoleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6c274-157"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6c274-157"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6c274-158">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="6c274-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6c274-159">**\_controllo READCONSOLE \_ console**</span><span class="sxs-lookup"><span data-stu-id="6c274-159">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="6c274-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6c274-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="6c274-161">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="6c274-161">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="6c274-162">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="6c274-162">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="6c274-163">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="6c274-163">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="6c274-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="6c274-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="6c274-165">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6c274-165">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="6c274-166">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="6c274-166">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="6c274-167">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="6c274-167">**WriteConsole**</span></span>](writeconsole.md)

 

 




