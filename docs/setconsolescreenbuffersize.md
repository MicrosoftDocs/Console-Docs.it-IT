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
ms.openlocfilehash: 66c8eee2b3c4cd50e74ac17404dd30c571e47f96
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357581"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="57915-104">SetConsoleScreenBufferSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="57915-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="57915-105">Modifica la dimensione del buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="57915-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="57915-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57915-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="57915-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="57915-107">Parameters</span></span>

<span data-ttu-id="57915-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="57915-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="57915-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="57915-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="57915-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="57915-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="57915-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="57915-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="57915-112">*dwSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="57915-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="57915-113">Struttura [**Coord**](coord-str.md) che specifica la nuova dimensione del buffer dello schermo della console, in righe e colonne di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="57915-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="57915-114">La larghezza e l'altezza specificate non possono essere minori della larghezza e dell'altezza della finestra del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="57915-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="57915-115">Anche le dimensioni specificate non possono essere inferiori alle dimensioni minime consentite dal sistema.</span><span class="sxs-lookup"><span data-stu-id="57915-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="57915-116">Questo valore minimo dipende dalle dimensioni correnti del carattere per la console (selezionate dall'utente) e dai valori **\_ CYMIN** **SM \_ CXMIN** e SM restituiti dalla funzione [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) .</span><span class="sxs-lookup"><span data-stu-id="57915-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="57915-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="57915-117">Return value</span></span>

<span data-ttu-id="57915-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="57915-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="57915-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="57915-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="57915-120">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="57915-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="57915-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="57915-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="57915-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="57915-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="57915-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="57915-123">Minimum supported client</span></span> | <span data-ttu-id="57915-124">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="57915-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="57915-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="57915-125">Minimum supported server</span></span> | <span data-ttu-id="57915-126">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="57915-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="57915-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="57915-127">Header</span></span> | <span data-ttu-id="57915-128">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="57915-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="57915-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="57915-129">Library</span></span> | <span data-ttu-id="57915-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="57915-130">Kernel32.lib</span></span> |
| <span data-ttu-id="57915-131">DLL</span><span class="sxs-lookup"><span data-stu-id="57915-131">DLL</span></span> | <span data-ttu-id="57915-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="57915-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="57915-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57915-133">See also</span></span>

[<span data-ttu-id="57915-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="57915-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="57915-135">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="57915-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="57915-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="57915-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="57915-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="57915-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="57915-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="57915-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)