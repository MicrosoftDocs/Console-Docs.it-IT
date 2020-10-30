---
title: GetConsoleCursorInfo (funzione)
description: Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2d9869c5c291addaf94a06fa67e11e3195ead686
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038919"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="21da1-104">GetConsoleCursorInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="21da1-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="21da1-105">Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="21da1-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="21da1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="21da1-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="21da1-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="21da1-107">Parameters</span></span>

<span data-ttu-id="21da1-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="21da1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="21da1-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="21da1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="21da1-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="21da1-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="21da1-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="21da1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="21da1-112">*lpConsoleCursorInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="21da1-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="21da1-113">Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che riceve informazioni sul cursore della console.</span><span class="sxs-lookup"><span data-stu-id="21da1-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="21da1-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="21da1-114">Return value</span></span>

<span data-ttu-id="21da1-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="21da1-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="21da1-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="21da1-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="21da1-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="21da1-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="21da1-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="21da1-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="21da1-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="21da1-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="21da1-120">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="21da1-120">Minimum supported client</span></span> | <span data-ttu-id="21da1-121">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="21da1-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="21da1-122">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="21da1-122">Minimum supported server</span></span> | <span data-ttu-id="21da1-123">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="21da1-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="21da1-124">Intestazione</span><span class="sxs-lookup"><span data-stu-id="21da1-124">Header</span></span> | <span data-ttu-id="21da1-125">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="21da1-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="21da1-126">Libreria</span><span class="sxs-lookup"><span data-stu-id="21da1-126">Library</span></span> | <span data-ttu-id="21da1-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="21da1-127">Kernel32.lib</span></span> |
| <span data-ttu-id="21da1-128">DLL</span><span class="sxs-lookup"><span data-stu-id="21da1-128">DLL</span></span> | <span data-ttu-id="21da1-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="21da1-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="21da1-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="21da1-130">See also</span></span>

[<span data-ttu-id="21da1-131">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="21da1-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="21da1-132">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="21da1-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="21da1-133">**\_informazioni cursore \_ console**</span><span class="sxs-lookup"><span data-stu-id="21da1-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="21da1-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="21da1-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
