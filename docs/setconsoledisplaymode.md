---
title: SetConsoleDisplayMode (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleDisplayMode, che imposta la modalità di visualizzazione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039389"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="9a42b-104">SetConsoleDisplayMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="9a42b-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9a42b-105">Imposta la modalità di visualizzazione del buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="9a42b-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a42b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a42b-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="9a42b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="9a42b-107">Parameters</span></span>

<span data-ttu-id="9a42b-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9a42b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9a42b-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9a42b-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="9a42b-110">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9a42b-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="9a42b-111">Modalità di visualizzazione della console.</span><span class="sxs-lookup"><span data-stu-id="9a42b-111">The display mode of the console.</span></span> <span data-ttu-id="9a42b-112">Il parametro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="9a42b-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="9a42b-113">Valore</span><span class="sxs-lookup"><span data-stu-id="9a42b-113">Value</span></span> | <span data-ttu-id="9a42b-114">Significato</span><span class="sxs-lookup"><span data-stu-id="9a42b-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9a42b-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="9a42b-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="9a42b-116">Il testo viene visualizzato in modalità schermo intero.</span><span class="sxs-lookup"><span data-stu-id="9a42b-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="9a42b-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="9a42b-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="9a42b-118">Il testo viene visualizzato in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="9a42b-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="9a42b-119">*lpNewScreenBufferDimensions* \[ out, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="9a42b-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="9a42b-120">Puntatore a una struttura [**Coord**](coord-str.md) che riceve le nuove dimensioni del buffer dello schermo, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="9a42b-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="9a42b-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9a42b-121">Return value</span></span>

<span data-ttu-id="9a42b-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="9a42b-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9a42b-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="9a42b-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9a42b-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9a42b-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9a42b-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9a42b-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="9a42b-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9a42b-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9a42b-127">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9a42b-127">Minimum supported client</span></span> | <span data-ttu-id="9a42b-128">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="9a42b-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="9a42b-129">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9a42b-129">Minimum supported server</span></span> | <span data-ttu-id="9a42b-130">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="9a42b-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="9a42b-131">Intestazione</span><span class="sxs-lookup"><span data-stu-id="9a42b-131">Header</span></span> | <span data-ttu-id="9a42b-132">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9a42b-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9a42b-133">Libreria</span><span class="sxs-lookup"><span data-stu-id="9a42b-133">Library</span></span> | <span data-ttu-id="9a42b-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9a42b-134">Kernel32.lib</span></span> |
| <span data-ttu-id="9a42b-135">DLL</span><span class="sxs-lookup"><span data-stu-id="9a42b-135">DLL</span></span> | <span data-ttu-id="9a42b-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9a42b-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9a42b-137">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9a42b-137">See also</span></span>

[<span data-ttu-id="9a42b-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="9a42b-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9a42b-139">Modalità console</span><span class="sxs-lookup"><span data-stu-id="9a42b-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="9a42b-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="9a42b-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)
