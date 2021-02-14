---
title: SetConsoleScreenBufferInfoEx (funzione)
description: Imposta le informazioni estese sul buffer dello schermo della console specificato sul buffer specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 677df94d6397c1515ad96757788c9a044b6ed87e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358651"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="cfb01-104">SetConsoleScreenBufferInfoEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="cfb01-104">SetConsoleScreenBufferInfoEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="cfb01-105">Imposta le informazioni estese sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="cfb01-105">Sets extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="cfb01-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cfb01-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="cfb01-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="cfb01-107">Parameters</span></span>

<span data-ttu-id="cfb01-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cfb01-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="cfb01-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="cfb01-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="cfb01-110">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="cfb01-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="cfb01-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="cfb01-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="cfb01-112">*lpConsoleScreenBufferInfoEx* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="cfb01-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="cfb01-113">Struttura [**\_ \_ \_ INFOEX buffer dello schermo**](console-screen-buffer-infoex.md) della console che contiene le informazioni sul buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="cfb01-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="cfb01-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="cfb01-114">Return value</span></span>

<span data-ttu-id="cfb01-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="cfb01-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cfb01-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="cfb01-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cfb01-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="cfb01-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="cfb01-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cfb01-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="cfb01-119">Questa API ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** parziale.</span><span class="sxs-lookup"><span data-stu-id="cfb01-119">This API has a partial **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="cfb01-120">Il **[buffer di posizionamento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)** e **[gli attributi di testo](console-virtual-terminal-sequences.md#text-formatting)** hanno equivalenti di sequenza specifici.</span><span class="sxs-lookup"><span data-stu-id="cfb01-120">**[Cursor positioning buffer](console-virtual-terminal-sequences.md#cursor-positioning)** and **[text attributes](console-virtual-terminal-sequences.md#text-formatting)** have specific sequence equivalents.</span></span> <span data-ttu-id="cfb01-121">La tabella dei colori non è configurabile, ma **[i colori estesi](console-virtual-terminal-sequences.md#extended-colors)** sono disponibili oltre quelli normalmente disponibili tramite le **[funzioni della console](console-functions.md)**.</span><span class="sxs-lookup"><span data-stu-id="cfb01-121">The color table is not configurable, but **[extended colors](console-virtual-terminal-sequences.md#extended-colors)** are available beyond what is normally available through **[console functions](console-functions.md)**.</span></span> <span data-ttu-id="cfb01-122">Gli attributi popup non hanno alcun equivalente perché i menu popup sono la responsabilità dell'applicazione client dalla riga di comando nel mondo dei **terminali virtuali** .</span><span class="sxs-lookup"><span data-stu-id="cfb01-122">Popup attributes have no equivalent as popup menus are the responsibility of the command-line client application in the **virtual terminal** world.</span></span> <span data-ttu-id="cfb01-123">Infine, le dimensioni della finestra e dello stato schermo intero sono considerati privilegi di proprietà dell'utente nel mondo del **terminale virtuale** e non hanno una sequenza equivalente.</span><span class="sxs-lookup"><span data-stu-id="cfb01-123">Finally, the size of the window and the full screen status are considered privileges owned by the user in the **virtual terminal** world and have no equivalent sequence.</span></span>

## <a name="requirements"></a><span data-ttu-id="cfb01-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cfb01-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cfb01-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cfb01-125">Minimum supported client</span></span> | <span data-ttu-id="cfb01-126">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="cfb01-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="cfb01-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cfb01-127">Minimum supported server</span></span> | <span data-ttu-id="cfb01-128">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="cfb01-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="cfb01-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="cfb01-129">Header</span></span> | <span data-ttu-id="cfb01-130">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cfb01-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cfb01-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="cfb01-131">Library</span></span> | <span data-ttu-id="cfb01-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="cfb01-132">Kernel32.lib</span></span> |
| <span data-ttu-id="cfb01-133">DLL</span><span class="sxs-lookup"><span data-stu-id="cfb01-133">DLL</span></span> | <span data-ttu-id="cfb01-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cfb01-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cfb01-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cfb01-135">See also</span></span>

[<span data-ttu-id="cfb01-136">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="cfb01-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cfb01-137">**\_INFOEX buffer dello schermo della console \_ \_**</span><span class="sxs-lookup"><span data-stu-id="cfb01-137">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="cfb01-138">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="cfb01-138">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)