---
title: SetConsoleTextAttribute (funzione)
description: Imposta gli attributi dei caratteri scritti nel buffer dello schermo della console tramite la funzione WriteFile o WriteConsole o con l'eco della funzione ReadFile o ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358561"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="82dec-104">SetConsoleTextAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="82dec-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="82dec-105">Imposta gli attributi dei caratteri scritti nel buffer dello schermo della console tramite la funzione [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md) o con l'eco della funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="82dec-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="82dec-106">Questa funzione influiscono sul testo scritto dopo la chiamata di funzione.</span><span class="sxs-lookup"><span data-stu-id="82dec-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="82dec-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="82dec-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="82dec-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="82dec-108">Parameters</span></span>

<span data-ttu-id="82dec-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="82dec-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="82dec-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="82dec-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="82dec-111">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="82dec-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="82dec-112">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="82dec-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="82dec-113">*wAttributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="82dec-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="82dec-114">[Attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="82dec-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="82dec-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="82dec-115">Return value</span></span>

<span data-ttu-id="82dec-116">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="82dec-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="82dec-117">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="82dec-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="82dec-118">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="82dec-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="82dec-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="82dec-119">Remarks</span></span>

<span data-ttu-id="82dec-120">Per determinare gli attributi di colore correnti di un buffer dello schermo, chiamare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="82dec-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="82dec-121">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="82dec-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="82dec-122">Le _sequenze di terminali virtuali_ sono consigliate per lo sviluppo nuovo e continuo.</span><span class="sxs-lookup"><span data-stu-id="82dec-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="82dec-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="82dec-123">Examples</span></span>

<span data-ttu-id="82dec-124">Per un esempio, vedere [uso delle funzioni di input e output di High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="82dec-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="82dec-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="82dec-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="82dec-126">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="82dec-126">Minimum supported client</span></span> | <span data-ttu-id="82dec-127">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="82dec-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="82dec-128">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="82dec-128">Minimum supported server</span></span> | <span data-ttu-id="82dec-129">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="82dec-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="82dec-130">Intestazione</span><span class="sxs-lookup"><span data-stu-id="82dec-130">Header</span></span> | <span data-ttu-id="82dec-131">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="82dec-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="82dec-132">Libreria</span><span class="sxs-lookup"><span data-stu-id="82dec-132">Library</span></span> | <span data-ttu-id="82dec-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="82dec-133">Kernel32.lib</span></span> |
| <span data-ttu-id="82dec-134">DLL</span><span class="sxs-lookup"><span data-stu-id="82dec-134">DLL</span></span> | <span data-ttu-id="82dec-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="82dec-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="82dec-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="82dec-136">See also</span></span>

[<span data-ttu-id="82dec-137">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="82dec-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="82dec-138">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="82dec-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="82dec-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="82dec-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="82dec-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="82dec-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="82dec-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="82dec-141">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="82dec-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="82dec-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="82dec-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="82dec-143">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)