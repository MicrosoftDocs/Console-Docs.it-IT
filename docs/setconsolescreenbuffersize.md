---
title: SetConsoleScreenBufferSize (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleScreenBufferSize, che modifica la dimensione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039329"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="031e8-104">SetConsoleScreenBufferSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="031e8-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="031e8-105">Modifica la dimensione del buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="031e8-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="031e8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="031e8-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="031e8-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="031e8-107">Parameters</span></span>

<span data-ttu-id="031e8-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="031e8-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="031e8-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="031e8-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="031e8-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="031e8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="031e8-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="031e8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="031e8-112">*dwSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="031e8-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="031e8-113">Struttura [**Coord**](coord-str.md) che specifica la nuova dimensione del buffer dello schermo della console, in righe e colonne di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="031e8-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="031e8-114">La larghezza e l'altezza specificate non possono essere minori della larghezza e dell'altezza della finestra del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="031e8-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="031e8-115">Anche le dimensioni specificate non possono essere inferiori alle dimensioni minime consentite dal sistema.</span><span class="sxs-lookup"><span data-stu-id="031e8-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="031e8-116">Questo valore minimo dipende dalle dimensioni correnti del carattere per la console (selezionate dall'utente) e dai valori **\_ CYMIN** **SM \_ CXMIN** e SM restituiti dalla funzione [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="031e8-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="031e8-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="031e8-117">Return value</span></span>

<span data-ttu-id="031e8-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="031e8-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="031e8-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="031e8-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="031e8-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="031e8-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="031e8-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="031e8-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="031e8-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="031e8-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="031e8-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="031e8-123">Minimum supported client</span></span> | <span data-ttu-id="031e8-124">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="031e8-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="031e8-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="031e8-125">Minimum supported server</span></span> | <span data-ttu-id="031e8-126">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="031e8-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="031e8-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="031e8-127">Header</span></span> | <span data-ttu-id="031e8-128">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="031e8-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="031e8-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="031e8-129">Library</span></span> | <span data-ttu-id="031e8-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="031e8-130">Kernel32.lib</span></span> |
| <span data-ttu-id="031e8-131">DLL</span><span class="sxs-lookup"><span data-stu-id="031e8-131">DLL</span></span> | <span data-ttu-id="031e8-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="031e8-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="031e8-133">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="031e8-133">See also</span></span>

[<span data-ttu-id="031e8-134">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="031e8-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="031e8-135">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="031e8-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="031e8-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="031e8-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="031e8-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="031e8-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="031e8-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="031e8-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)
