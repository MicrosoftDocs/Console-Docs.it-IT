---
title: GetConsoleDisplayMode (funzione)
description: Vedere informazioni di riferimento sulla funzione GetConsoleDisplayMode, che consente di recuperare la modalità di visualizzazione della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358351"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="642a7-104">GetConsoleDisplayMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="642a7-104">GetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="642a7-105">Recupera la modalità di visualizzazione della console corrente.</span><span class="sxs-lookup"><span data-stu-id="642a7-105">Retrieves the display mode of the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="642a7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="642a7-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a><span data-ttu-id="642a7-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="642a7-107">Parameters</span></span>

<span data-ttu-id="642a7-108">*lpModeFlags* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="642a7-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="642a7-109">Modalità di visualizzazione della console.</span><span class="sxs-lookup"><span data-stu-id="642a7-109">The display mode of the console.</span></span> <span data-ttu-id="642a7-110">Il parametro può essere costituito da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="642a7-110">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="642a7-111">Valore</span><span class="sxs-lookup"><span data-stu-id="642a7-111">Value</span></span> | <span data-ttu-id="642a7-112">Significato</span><span class="sxs-lookup"><span data-stu-id="642a7-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="642a7-113">**CONSOLE_FULLSCREEN** 1</span><span class="sxs-lookup"><span data-stu-id="642a7-113">**CONSOLE_FULLSCREEN** 1</span></span> | <span data-ttu-id="642a7-114">Console a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="642a7-114">Full-screen console.</span></span> <span data-ttu-id="642a7-115">La console è in questa modalità non appena la finestra è ingrandita.</span><span class="sxs-lookup"><span data-stu-id="642a7-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="642a7-116">A questo punto, la transizione alla modalità schermo intero può comunque avere esito negativo.</span><span class="sxs-lookup"><span data-stu-id="642a7-116">At this point, the transition to full-screen mode can still fail.</span></span> |
| <span data-ttu-id="642a7-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span><span class="sxs-lookup"><span data-stu-id="642a7-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span></span> | <span data-ttu-id="642a7-118">Console a schermo intero che comunica direttamente con l'hardware del video.</span><span class="sxs-lookup"><span data-stu-id="642a7-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="642a7-119">Questa modalità viene impostata dopo che la console è in modalità **CONSOLE_FULLSCREEN** per indicare che la transizione alla modalità schermo intero è stata completata.</span><span class="sxs-lookup"><span data-stu-id="642a7-119">This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed.</span></span> |

> [!NOTE]
> <span data-ttu-id="642a7-120">La transizione a una modalità hardware video a schermo intero 100% è stata rimossa in Windows Vista con la ripiattaforma dello stack di grafica su [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span><span class="sxs-lookup"><span data-stu-id="642a7-120">The transition to a 100% full screen video hardware mode was removed in Windows Vista with the replatforming of the graphics stack to [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span></span> <span data-ttu-id="642a7-121">Nelle versioni successive di Windows, lo stato massimo risultante è **CONSOLE_FULLSCREEN** che rappresenta una finestra senza frame visualizzata a schermo intero, ma non è in esclusiva per il controllo dell'hardware.</span><span class="sxs-lookup"><span data-stu-id="642a7-121">On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.</span></span>

## <a name="return-value"></a><span data-ttu-id="642a7-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="642a7-122">Return value</span></span>

<span data-ttu-id="642a7-123">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="642a7-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="642a7-124">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="642a7-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="642a7-125">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="642a7-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="642a7-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="642a7-126">Remarks</span></span>

<span data-ttu-id="642a7-127">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="642a7-127">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="642a7-128">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="642a7-128">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="642a7-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="642a7-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="642a7-130">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="642a7-130">Minimum supported client</span></span> | <span data-ttu-id="642a7-131">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="642a7-131">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="642a7-132">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="642a7-132">Minimum supported server</span></span> | <span data-ttu-id="642a7-133">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="642a7-133">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="642a7-134">Intestazione</span><span class="sxs-lookup"><span data-stu-id="642a7-134">Header</span></span> | <span data-ttu-id="642a7-135">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="642a7-135">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="642a7-136">Libreria</span><span class="sxs-lookup"><span data-stu-id="642a7-136">Library</span></span> | <span data-ttu-id="642a7-137">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="642a7-137">Kernel32.lib</span></span> |
| <span data-ttu-id="642a7-138">DLL</span><span class="sxs-lookup"><span data-stu-id="642a7-138">DLL</span></span> | <span data-ttu-id="642a7-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="642a7-139">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="642a7-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="642a7-140">See also</span></span>

[<span data-ttu-id="642a7-141">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="642a7-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="642a7-142">Modalità della console</span><span class="sxs-lookup"><span data-stu-id="642a7-142">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="642a7-143">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="642a7-143">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)