---
title: SetConsoleCursorInfo (funzione)
description: Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357691"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="7b313-104">SetConsoleCursorInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="7b313-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7b313-105">Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="7b313-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b313-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7b313-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="7b313-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="7b313-107">Parameters</span></span>

<span data-ttu-id="7b313-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7b313-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="7b313-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="7b313-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="7b313-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="7b313-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="7b313-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="7b313-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7b313-112">*lpConsoleCursorInfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="7b313-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="7b313-113">Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che fornisce le nuove specifiche per il cursore del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="7b313-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b313-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="7b313-114">Return value</span></span>

<span data-ttu-id="7b313-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="7b313-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7b313-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="7b313-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7b313-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="7b313-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="7b313-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7b313-118">Remarks</span></span>

<span data-ttu-id="7b313-119">Quando il cursore di un buffer dello schermo è visibile, l'aspetto può variare, a partire dal riempimento completo di una cella di tipo carattere per essere visualizzata come linea orizzontale nella parte inferiore della cella.</span><span class="sxs-lookup"><span data-stu-id="7b313-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="7b313-120">Il membro **dwSize** della struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) specifica la percentuale di una cella di tipo carattere compilata dal cursore.</span><span class="sxs-lookup"><span data-stu-id="7b313-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="7b313-121">Se questo membro è minore di 1 o maggiore di 100, **SetConsoleCursorInfo** ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="7b313-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="7b313-122">Questa API dispone di un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nella sezione **[visibilità del cursore](console-virtual-terminal-sequences.md#cursor-visibility)** con le `^[[?25h` sequenze e `^[[?25l` .</span><span class="sxs-lookup"><span data-stu-id="7b313-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="7b313-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7b313-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7b313-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7b313-124">Minimum supported client</span></span> | <span data-ttu-id="7b313-125">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="7b313-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7b313-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7b313-126">Minimum supported server</span></span> | <span data-ttu-id="7b313-127">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="7b313-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7b313-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="7b313-128">Header</span></span> | <span data-ttu-id="7b313-129">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7b313-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7b313-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="7b313-130">Library</span></span> | <span data-ttu-id="7b313-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7b313-131">Kernel32.lib</span></span> |
| <span data-ttu-id="7b313-132">DLL</span><span class="sxs-lookup"><span data-stu-id="7b313-132">DLL</span></span> | <span data-ttu-id="7b313-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7b313-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7b313-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b313-134">See also</span></span>

[<span data-ttu-id="7b313-135">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="7b313-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7b313-136">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="7b313-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="7b313-137">**\_informazioni cursore \_ console**</span><span class="sxs-lookup"><span data-stu-id="7b313-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="7b313-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="7b313-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="7b313-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="7b313-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)