---
title: SetConsoleTextAttribute (funzione)
description: Imposta gli attributi dei caratteri scritti nel buffer dello schermo della console tramite la funzione WriteFile o WriteConsole o con l'eco della funzione ReadFile o ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 2242466e4255b0d92c9bb1d1eac5431b59346e7b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060507"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="25f1f-104">SetConsoleTextAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="25f1f-104">SetConsoleTextAttribute function</span></span>


<span data-ttu-id="25f1f-105">Imposta gli attributi dei caratteri scritti nel buffer dello schermo della console tramite la funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) o con l'eco della funzione [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="25f1f-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="25f1f-106">Questa funzione influiscono sul testo scritto dopo la chiamata di funzione.</span><span class="sxs-lookup"><span data-stu-id="25f1f-106">This function affects text written after the function call.</span></span>

<a name="syntax"></a><span data-ttu-id="25f1f-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="25f1f-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

<a name="parameters"></a><span data-ttu-id="25f1f-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="25f1f-108">Parameters</span></span>
----------

<span data-ttu-id="25f1f-109">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="25f1f-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="25f1f-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="25f1f-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="25f1f-111">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="25f1f-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="25f1f-112">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="25f1f-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="25f1f-113">*wAttributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="25f1f-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="25f1f-114">[Attributi carattere](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="25f1f-114">The [character attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<a name="return-value"></a><span data-ttu-id="25f1f-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="25f1f-115">Return value</span></span>
------------

<span data-ttu-id="25f1f-116">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="25f1f-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="25f1f-117">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="25f1f-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="25f1f-118">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="25f1f-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="25f1f-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="25f1f-119">Remarks</span></span>
-------

<span data-ttu-id="25f1f-120">Per determinare gli attributi di colore correnti di un buffer dello schermo, chiamare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="25f1f-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="25f1f-121">Esempi</span><span class="sxs-lookup"><span data-stu-id="25f1f-121">Examples</span></span>
--------

<span data-ttu-id="25f1f-122">Per un esempio, vedere [utilizzo delle funzioni di input e output di alto livello](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="25f1f-122">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="25f1f-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="25f1f-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="25f1f-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="25f1f-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="25f1f-125">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="25f1f-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="25f1f-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="25f1f-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="25f1f-127">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="25f1f-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="25f1f-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="25f1f-128">Header</span></span></p></td>
<td><span data-ttu-id="25f1f-129">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="25f1f-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="25f1f-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="25f1f-130">Library</span></span></p></td>
<td><span data-ttu-id="25f1f-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="25f1f-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="25f1f-132">DLL</span><span class="sxs-lookup"><span data-stu-id="25f1f-132">DLL</span></span></p></td>
<td><span data-ttu-id="25f1f-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="25f1f-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="25f1f-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25f1f-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="25f1f-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="25f1f-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="25f1f-136">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="25f1f-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="25f1f-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="25f1f-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="25f1f-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="25f1f-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="25f1f-139">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="25f1f-139">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="25f1f-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="25f1f-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="25f1f-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="25f1f-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




