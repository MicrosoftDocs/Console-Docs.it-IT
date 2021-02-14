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
ms.openlocfilehash: c920e5dd279a23b07702fa12b80da4245561548f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358451"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="d889e-104">GetConsoleCursorInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="d889e-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d889e-105">Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="d889e-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d889e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d889e-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="d889e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d889e-107">Parameters</span></span>

<span data-ttu-id="d889e-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d889e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d889e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="d889e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d889e-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="d889e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d889e-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d889e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d889e-112">*lpConsoleCursorInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="d889e-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="d889e-113">Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che riceve informazioni sul cursore della console.</span><span class="sxs-lookup"><span data-stu-id="d889e-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="d889e-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d889e-114">Return value</span></span>

<span data-ttu-id="d889e-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="d889e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d889e-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="d889e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d889e-117">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="d889e-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d889e-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d889e-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="d889e-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d889e-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d889e-120">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d889e-120">Minimum supported client</span></span> | <span data-ttu-id="d889e-121">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="d889e-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d889e-122">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d889e-122">Minimum supported server</span></span> | <span data-ttu-id="d889e-123">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="d889e-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d889e-124">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d889e-124">Header</span></span> | <span data-ttu-id="d889e-125">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d889e-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d889e-126">Libreria</span><span class="sxs-lookup"><span data-stu-id="d889e-126">Library</span></span> | <span data-ttu-id="d889e-127">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d889e-127">Kernel32.lib</span></span> |
| <span data-ttu-id="d889e-128">DLL</span><span class="sxs-lookup"><span data-stu-id="d889e-128">DLL</span></span> | <span data-ttu-id="d889e-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d889e-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d889e-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d889e-130">See also</span></span>

[<span data-ttu-id="d889e-131">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="d889e-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d889e-132">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="d889e-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="d889e-133">**\_informazioni cursore \_ console**</span><span class="sxs-lookup"><span data-stu-id="d889e-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="d889e-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="d889e-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)