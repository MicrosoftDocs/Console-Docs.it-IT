---
title: GetStdHandle (funzione)
description: Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358751"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="39349-104">GetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="39349-104">GetStdHandle function</span></span>

<span data-ttu-id="39349-105">Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="39349-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="39349-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39349-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="39349-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="39349-107">Parameters</span></span>

<span data-ttu-id="39349-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="39349-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="39349-109">Il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="39349-109">The standard device.</span></span> <span data-ttu-id="39349-110">Questo parametro può avere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="39349-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="39349-111">Valore</span><span class="sxs-lookup"><span data-stu-id="39349-111">Value</span></span> | <span data-ttu-id="39349-112">Significato</span><span class="sxs-lookup"><span data-stu-id="39349-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="39349-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="39349-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="39349-114">Il dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="39349-114">The standard input device.</span></span> <span data-ttu-id="39349-115">Inizialmente si tratta del buffer di input della console, ovvero `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="39349-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="39349-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="39349-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="39349-117">Il dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="39349-117">The standard output device.</span></span> <span data-ttu-id="39349-118">Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="39349-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="39349-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="39349-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="39349-120">Il dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="39349-120">The standard error device.</span></span> <span data-ttu-id="39349-121">Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="39349-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="39349-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="39349-122">Return value</span></span>

<span data-ttu-id="39349-123">Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente su [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="39349-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="39349-124">L'handle dispone dei diritti di accesso **GENERIC\_READ** e **GENERIC\_WRITE**, a meno che l'applicazione non abbia usato **SetStdHandle** per impostare un handle standard con un livello di accesso inferiore.</span><span class="sxs-lookup"><span data-stu-id="39349-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="39349-125">Se la funzione ha esito negativo, il valore restituito è **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="39349-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="39349-126">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="39349-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="39349-127">Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo, e non sono stati reindirizzati, il valore restituito sarà **NULL**.</span><span class="sxs-lookup"><span data-stu-id="39349-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="39349-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="39349-128">Remarks</span></span>

<span data-ttu-id="39349-129">Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console.</span><span class="sxs-lookup"><span data-stu-id="39349-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="39349-130">Al momento della creazione di una console, l'handle di input standard è un handle per il buffer di input della console e gli handle di output standard e di errore standard sono handle del buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="39349-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="39349-131">Questi handle possono essere usati dalle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o da qualsiasi funzione della console che accede al buffer di input della console o a un buffer dello schermo, ad esempio [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="39349-131">These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="39349-132">Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="39349-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="39349-133">Se gli handle standard sono stati reindirizzati, è possibile specificare il valore `CONIN$` in una chiamata alla funzione [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="39349-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="39349-134">Analogamente, è possibile specificare il valore `CONOUT$` per ottenere un handle per il buffer dello schermo attivo di una console.</span><span class="sxs-lookup"><span data-stu-id="39349-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="39349-135">Gli handle standard di un processo all'immissione del metodo principale sono determinati dalla configurazione del flag [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) passato al linker al momento della compilazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="39349-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="39349-136">Se si specifica **/SUBSYSTEM:CONSOLE**, si richiede al sistema operativo di riempire gli handle con una sessione della console all'avvio, se il padre non ha già riempito la tabella di handle standard mediante ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="39349-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="39349-137">Viceversa, **/SUBSYSTEM:WINDOWS** implica che l'applicazione non necessita di una console e probabilmente non userà gli handle standard.</span><span class="sxs-lookup"><span data-stu-id="39349-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="39349-138">Altre informazioni sull'ereditarietà degli handle sono disponibili nella documentazione relativa a [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="39349-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="39349-139">Alcune applicazioni operano all'esterno dei limiti del sottosistema dichiarato. Ad esempio, un'applicazione **/SUBSYSTEM:WINDOWS** potrebbe controllare/usare gli handle standard per la registrazione o il debug, ma funzionare normalmente con un'interfaccia utente grafica.</span><span class="sxs-lookup"><span data-stu-id="39349-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="39349-140">Queste applicazioni dovranno verificare accuratamente lo stato degli handle standard all'avvio e usare [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) per aggiungere/rimuovere una console, se necessario.</span><span class="sxs-lookup"><span data-stu-id="39349-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="39349-141">Alcune applicazioni possono anche variare il comportamento in base al tipo di handle ereditato.</span><span class="sxs-lookup"><span data-stu-id="39349-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="39349-142">La distinzione del tipo tra console, pipe, file e altri può essere eseguita con [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span><span class="sxs-lookup"><span data-stu-id="39349-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="39349-143">Comportamento di collegamento/scollegamento</span><span class="sxs-lookup"><span data-stu-id="39349-143">Attach/detach behavior</span></span>

<span data-ttu-id="39349-144">Quando ci si collega a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF\_USESTDHANDLES** durante la creazione del processo.</span><span class="sxs-lookup"><span data-stu-id="39349-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="39349-145">Se il valore esistente dell'handle standard è **NULL** o se ha l'aspetto di uno pseudohandle della console, l'handle viene sostituito con un handle della console.</span><span class="sxs-lookup"><span data-stu-id="39349-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="39349-146">Quando un padre usa sia **CREATE\_NEW\_CONSOLE** che **STARTF\_USESTDHANDLES** per creare un processo della console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia **NULL** o uno pseudohandle della console.</span><span class="sxs-lookup"><span data-stu-id="39349-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="39349-147">I processi della console *devono* iniziare con gli handle standard riempiti, altrimenti verranno riempiti automaticamente con gli handle appropriati per una nuova console.</span><span class="sxs-lookup"><span data-stu-id="39349-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="39349-148">Le applicazioni GUI (interfaccia utente grafica) possono essere avviate senza gli handle standard e non verranno riempite automaticamente.</span><span class="sxs-lookup"><span data-stu-id="39349-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="39349-149">Esempi</span><span class="sxs-lookup"><span data-stu-id="39349-149">Examples</span></span>

<span data-ttu-id="39349-150">Un esempio è disponibile in [Lettura di eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="39349-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="39349-151">Requisiti</span><span class="sxs-lookup"><span data-stu-id="39349-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="39349-152">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="39349-152">Minimum supported client</span></span> | <span data-ttu-id="39349-153">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="39349-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="39349-154">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="39349-154">Minimum supported server</span></span> | <span data-ttu-id="39349-155">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="39349-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="39349-156">Intestazione</span><span class="sxs-lookup"><span data-stu-id="39349-156">Header</span></span> | <span data-ttu-id="39349-157">ProcessEnv.h (tramite Winbase.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="39349-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="39349-158">Libreria</span><span class="sxs-lookup"><span data-stu-id="39349-158">Library</span></span> | <span data-ttu-id="39349-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="39349-159">Kernel32.lib</span></span> |
| <span data-ttu-id="39349-160">DLL</span><span class="sxs-lookup"><span data-stu-id="39349-160">DLL</span></span> | <span data-ttu-id="39349-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="39349-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="39349-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39349-162">See also</span></span>

[<span data-ttu-id="39349-163">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="39349-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="39349-164">Handle della console</span><span class="sxs-lookup"><span data-stu-id="39349-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="39349-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="39349-165">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="39349-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="39349-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="39349-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="39349-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="39349-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="39349-168">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="39349-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="39349-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="39349-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="39349-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="39349-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="39349-171">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)