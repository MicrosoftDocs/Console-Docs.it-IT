---
title: SetConsoleActiveScreenBuffer (funzione)
description: Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039439"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="eb80e-104">SetConsoleActiveScreenBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="eb80e-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="eb80e-105">Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato.</span><span class="sxs-lookup"><span data-stu-id="eb80e-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb80e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="eb80e-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="eb80e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="eb80e-107">Parameters</span></span>

<span data-ttu-id="eb80e-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="eb80e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="eb80e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="eb80e-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb80e-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="eb80e-110">Return value</span></span>

<span data-ttu-id="eb80e-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="eb80e-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="eb80e-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="eb80e-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="eb80e-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="eb80e-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="eb80e-114">Commenti</span><span class="sxs-lookup"><span data-stu-id="eb80e-114">Remarks</span></span>

<span data-ttu-id="eb80e-115">Una console può avere più buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="eb80e-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="eb80e-116">**SetConsoleActiveScreenBuffer** determina quale viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="eb80e-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="eb80e-117">È possibile scrivere in un buffer dello schermo inattivo e quindi usare **SetConsoleActiveScreenBuffer** per visualizzare il contenuto del buffer.</span><span class="sxs-lookup"><span data-stu-id="eb80e-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="eb80e-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="eb80e-118">Examples</span></span>

<span data-ttu-id="eb80e-119">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="eb80e-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="eb80e-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="eb80e-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="eb80e-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="eb80e-121">Minimum supported client</span></span> | <span data-ttu-id="eb80e-122">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="eb80e-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="eb80e-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="eb80e-123">Minimum supported server</span></span> | <span data-ttu-id="eb80e-124">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="eb80e-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="eb80e-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="eb80e-125">Header</span></span> | <span data-ttu-id="eb80e-126">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="eb80e-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="eb80e-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="eb80e-127">Library</span></span> | <span data-ttu-id="eb80e-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="eb80e-128">Kernel32.lib</span></span> |
| <span data-ttu-id="eb80e-129">DLL</span><span class="sxs-lookup"><span data-stu-id="eb80e-129">DLL</span></span> | <span data-ttu-id="eb80e-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="eb80e-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="eb80e-131">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="eb80e-131">See also</span></span>

[<span data-ttu-id="eb80e-132">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="eb80e-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="eb80e-133">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="eb80e-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="eb80e-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="eb80e-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)
