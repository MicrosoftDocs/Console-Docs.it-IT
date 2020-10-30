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
ms.openlocfilehash: 03925af2668774a36de33bfe6ea5fcdc1b475d5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039319"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="fcb44-104">SetConsoleTextAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="fcb44-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="fcb44-105">Imposta gli attributi dei caratteri scritti nel buffer dello schermo della console tramite la funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) o con l'eco della funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="fcb44-106">Questa funzione influiscono sul testo scritto dopo la chiamata di funzione.</span><span class="sxs-lookup"><span data-stu-id="fcb44-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb44-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fcb44-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="fcb44-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="fcb44-108">Parameters</span></span>

<span data-ttu-id="fcb44-109">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fcb44-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="fcb44-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="fcb44-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="fcb44-111">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="fcb44-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="fcb44-112">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="fcb44-113">*wAttributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fcb44-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="fcb44-114">[Attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="fcb44-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="fcb44-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="fcb44-115">Return value</span></span>

<span data-ttu-id="fcb44-116">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="fcb44-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fcb44-117">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="fcb44-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fcb44-118">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fcb44-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="fcb44-119">Commenti</span><span class="sxs-lookup"><span data-stu-id="fcb44-119">Remarks</span></span>

<span data-ttu-id="fcb44-120">Per determinare gli attributi di colore correnti di un buffer dello schermo, chiamare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="fcb44-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="fcb44-121">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** .</span><span class="sxs-lookup"><span data-stu-id="fcb44-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="fcb44-122">Le _sequenze di terminali virtuali_ sono consigliate per lo sviluppo nuovo e continuo.</span><span class="sxs-lookup"><span data-stu-id="fcb44-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="fcb44-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="fcb44-123">Examples</span></span>

<span data-ttu-id="fcb44-124">Per un esempio, vedere [uso delle funzioni di input e output di High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="fcb44-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="fcb44-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fcb44-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fcb44-126">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fcb44-126">Minimum supported client</span></span> | <span data-ttu-id="fcb44-127">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="fcb44-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fcb44-128">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fcb44-128">Minimum supported server</span></span> | <span data-ttu-id="fcb44-129">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="fcb44-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fcb44-130">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fcb44-130">Header</span></span> | <span data-ttu-id="fcb44-131">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fcb44-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fcb44-132">Libreria</span><span class="sxs-lookup"><span data-stu-id="fcb44-132">Library</span></span> | <span data-ttu-id="fcb44-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fcb44-133">Kernel32.lib</span></span> |
| <span data-ttu-id="fcb44-134">DLL</span><span class="sxs-lookup"><span data-stu-id="fcb44-134">DLL</span></span> | <span data-ttu-id="fcb44-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fcb44-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="fcb44-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fcb44-136">See also</span></span>

[<span data-ttu-id="fcb44-137">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="fcb44-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fcb44-138">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="fcb44-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="fcb44-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="fcb44-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="fcb44-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="fcb44-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="fcb44-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="fcb44-141">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="fcb44-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="fcb44-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="fcb44-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="fcb44-143">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
