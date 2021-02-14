---
title: CreateConsoleScreenBuffer (funzione)
description: La funzione CreateConsoleScreenBuffer crea un buffer dello schermo per la console di Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357961"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="9581d-104">CreateConsoleScreenBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="9581d-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9581d-105">Crea un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9581d-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9581d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9581d-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="9581d-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="9581d-107">Parameters</span></span>

<span data-ttu-id="9581d-108">*dwDesiredAccess* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9581d-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="9581d-109">Accesso al buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9581d-109">The access to the console screen buffer.</span></span> <span data-ttu-id="9581d-110">Per un elenco dei diritti di accesso, vedere [diritti di accesso e sicurezza del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9581d-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9581d-111">*dwShareMode* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9581d-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="9581d-112">Questo parametro può essere zero, a indicare che il buffer non può essere condiviso oppure può essere uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="9581d-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="9581d-113">Valore</span><span class="sxs-lookup"><span data-stu-id="9581d-113">Value</span></span> | <span data-ttu-id="9581d-114">Significato</span><span class="sxs-lookup"><span data-stu-id="9581d-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9581d-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="9581d-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="9581d-116">È possibile eseguire altre operazioni aperte sul buffer dello schermo della console per l'accesso in lettura.</span><span class="sxs-lookup"><span data-stu-id="9581d-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="9581d-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="9581d-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="9581d-118">È possibile eseguire altre operazioni aperte sul buffer dello schermo della console per l'accesso in scrittura.</span><span class="sxs-lookup"><span data-stu-id="9581d-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="9581d-119">*lpSecurityAttributes* \[ in, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="9581d-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="9581d-120">Puntatore a una struttura [**di \_ attributi di sicurezza**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) che determina se l'handle restituito può essere ereditato dai processi figlio.</span><span class="sxs-lookup"><span data-stu-id="9581d-120">A pointer to a [**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="9581d-121">Se *lpSecurityAttributes* è **null**, l'handle non può essere ereditato.</span><span class="sxs-lookup"><span data-stu-id="9581d-121">If *lpSecurityAttributes* is **NULL**, the handle cannot be inherited.</span></span> <span data-ttu-id="9581d-122">Il membro **lpSecurityDescriptor** della struttura specifica un descrittore di sicurezza per il nuovo buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9581d-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="9581d-123">Se *lpSecurityAttributes* è **null**, il buffer dello schermo della console ottiene un descrittore di sicurezza predefinito.</span><span class="sxs-lookup"><span data-stu-id="9581d-123">If *lpSecurityAttributes* is **NULL**, the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="9581d-124">Gli ACL nel descrittore di sicurezza predefinito per un buffer dello schermo della console provengono dal token primario o di rappresentazione del creatore.</span><span class="sxs-lookup"><span data-stu-id="9581d-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="9581d-125">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9581d-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="9581d-126">Tipo di buffer dello schermo della console da creare.</span><span class="sxs-lookup"><span data-stu-id="9581d-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="9581d-127">L'unico tipo di buffer dello schermo supportato è il **\_ \_ buffer testuale della console**.</span><span class="sxs-lookup"><span data-stu-id="9581d-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER**.</span></span>

<span data-ttu-id="9581d-128">*lpScreenBufferData*</span><span class="sxs-lookup"><span data-stu-id="9581d-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="9581d-129">Riservati deve essere **null**.</span><span class="sxs-lookup"><span data-stu-id="9581d-129">Reserved; should be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="9581d-130">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9581d-130">Return value</span></span>

<span data-ttu-id="9581d-131">Se la funzione ha esito positivo, il valore restituito è un handle per il nuovo buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9581d-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="9581d-132">Se la funzione ha esito negativo, il valore restituito è **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="9581d-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="9581d-133">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="9581d-133">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="9581d-134">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9581d-134">Remarks</span></span>

<span data-ttu-id="9581d-135">Una console può avere più buffer dello schermo, ma solo un buffer attivo dello schermo.</span><span class="sxs-lookup"><span data-stu-id="9581d-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="9581d-136">È possibile accedere ai buffer dello schermo inattivi per la lettura e la scrittura, ma viene visualizzato solo il buffer attivo dello schermo.</span><span class="sxs-lookup"><span data-stu-id="9581d-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="9581d-137">Per fare in modo che la nuova schermata ripresenti il buffer dello schermo attivo, utilizzare la funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="9581d-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="9581d-138">Il buffer dello schermo appena creato copierà alcune proprietà dal buffer dello schermo attivo nel momento in cui viene chiamata la funzione.</span><span class="sxs-lookup"><span data-stu-id="9581d-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="9581d-139">Il comportamento è il seguente:</span><span class="sxs-lookup"><span data-stu-id="9581d-139">The behavior is as follows:</span></span>

- <span data-ttu-id="9581d-140">`Font` -copiato dal buffer dello schermo attivo</span><span class="sxs-lookup"><span data-stu-id="9581d-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="9581d-141">`Display Window Size` -copiato dal buffer dello schermo attivo</span><span class="sxs-lookup"><span data-stu-id="9581d-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="9581d-142">`Buffer Size` -corrispondente a `Display Window Size` (**non** copiato)</span><span class="sxs-lookup"><span data-stu-id="9581d-142">`Buffer Size` - matched to `Display Window Size` (**NOT** copied)</span></span>
- <span data-ttu-id="9581d-143">`Default Attributes` (colori)-copiato dal buffer dello schermo attivo</span><span class="sxs-lookup"><span data-stu-id="9581d-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="9581d-144">`Default Popup Attributes` (colori)-copiato dal buffer dello schermo attivo</span><span class="sxs-lookup"><span data-stu-id="9581d-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="9581d-145">Il processo chiamante può usare l'handle restituito in qualsiasi funzione che richiede un handle a un buffer dello schermo della console, in base alle limitazioni di accesso specificate dal parametro *dwDesiredAccess* .</span><span class="sxs-lookup"><span data-stu-id="9581d-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="9581d-146">Il processo chiamante può utilizzare la funzione [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) per creare un handle duplicato del buffer dello schermo con accesso o ereditarietà diversi dall'handle originale.</span><span class="sxs-lookup"><span data-stu-id="9581d-146">The calling process can use the [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="9581d-147">Tuttavia, non è possibile usare **DuplicateHandle** per creare un duplicato valido per un processo diverso (tranne tramite ereditarietà).</span><span class="sxs-lookup"><span data-stu-id="9581d-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="9581d-148">Per chiudere l'handle del buffer dello schermo della console, usare la funzione [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) .</span><span class="sxs-lookup"><span data-stu-id="9581d-148">To close the console screen buffer handle, use the [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="9581d-149">Esempio</span><span class="sxs-lookup"><span data-stu-id="9581d-149">Examples</span></span>

<span data-ttu-id="9581d-150">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9581d-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9581d-151">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9581d-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9581d-152">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9581d-152">Minimum supported client</span></span> | <span data-ttu-id="9581d-153">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="9581d-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9581d-154">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9581d-154">Minimum supported server</span></span> | <span data-ttu-id="9581d-155">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="9581d-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9581d-156">Intestazione</span><span class="sxs-lookup"><span data-stu-id="9581d-156">Header</span></span> | <span data-ttu-id="9581d-157">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9581d-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9581d-158">Libreria</span><span class="sxs-lookup"><span data-stu-id="9581d-158">Library</span></span> | <span data-ttu-id="9581d-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="9581d-159">Kernel32.lib</span></span> |
| <span data-ttu-id="9581d-160">DLL</span><span class="sxs-lookup"><span data-stu-id="9581d-160">DLL</span></span> | <span data-ttu-id="9581d-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9581d-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9581d-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9581d-162">See also</span></span>

[<span data-ttu-id="9581d-163">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="9581d-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9581d-164">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="9581d-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="9581d-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="9581d-165">**CloseHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[<span data-ttu-id="9581d-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="9581d-166">**DuplicateHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[<span data-ttu-id="9581d-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9581d-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

<span data-ttu-id="9581d-168">[**attributi di sicurezza \_**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9581d-168">[**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span></span>

[<span data-ttu-id="9581d-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="9581d-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="9581d-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="9581d-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)