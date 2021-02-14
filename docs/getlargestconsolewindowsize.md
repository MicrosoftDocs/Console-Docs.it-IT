---
title: GetLargestConsoleWindowSize (funzione)
description: Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3fe4ddf83f25f1951defed52eaf8fea18e1ff2dc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358871"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="c81c9-104">GetLargestConsoleWindowSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="c81c9-104">GetLargestConsoleWindowSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c81c9-105">Recupera la dimensione della finestra della console più grande possibile, in base al tipo di carattere corrente e alla dimensione dello schermo.</span><span class="sxs-lookup"><span data-stu-id="c81c9-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

## <a name="syntax"></a><span data-ttu-id="c81c9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c81c9-106">Syntax</span></span>

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="c81c9-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c81c9-107">Parameters</span></span>

<span data-ttu-id="c81c9-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c81c9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c81c9-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c81c9-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="c81c9-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c81c9-110">Return value</span></span>

<span data-ttu-id="c81c9-111">Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che specifica il numero di colonne di celle di tipo carattere (membro **X** ) e le righe (membro **Y** ) nella finestra della console più grande possibile.</span><span class="sxs-lookup"><span data-stu-id="c81c9-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="c81c9-112">In caso contrario, i membri della struttura sono pari a zero.</span><span class="sxs-lookup"><span data-stu-id="c81c9-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="c81c9-113">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c81c9-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c81c9-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c81c9-114">Remarks</span></span>

<span data-ttu-id="c81c9-115">La funzione non prende in considerazione le dimensioni del buffer dello schermo della console, il che significa che le dimensioni della finestra restituite possono essere maggiori delle dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c81c9-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="c81c9-116">La funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) può essere usata per determinare le dimensioni massime della finestra della console, date le dimensioni correnti del buffer dello schermo, il tipo di carattere corrente e le dimensioni di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c81c9-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="c81c9-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c81c9-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c81c9-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c81c9-118">Minimum supported client</span></span> | <span data-ttu-id="c81c9-119">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="c81c9-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c81c9-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c81c9-120">Minimum supported server</span></span> | <span data-ttu-id="c81c9-121">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="c81c9-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c81c9-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c81c9-122">Header</span></span> | <span data-ttu-id="c81c9-123">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c81c9-123">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c81c9-124">Libreria</span><span class="sxs-lookup"><span data-stu-id="c81c9-124">Library</span></span> | <span data-ttu-id="c81c9-125">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c81c9-125">Kernel32.lib</span></span> |
| <span data-ttu-id="c81c9-126">DLL</span><span class="sxs-lookup"><span data-stu-id="c81c9-126">DLL</span></span> | <span data-ttu-id="c81c9-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c81c9-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c81c9-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c81c9-128">See also</span></span>

[<span data-ttu-id="c81c9-129">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="c81c9-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c81c9-130">**COORD**</span><span class="sxs-lookup"><span data-stu-id="c81c9-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="c81c9-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="c81c9-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="c81c9-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="c81c9-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="c81c9-133">Dimensioni del buffer della finestra e dello schermo</span><span class="sxs-lookup"><span data-stu-id="c81c9-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)