---
title: GetConsoleTitle (funzione)
description: Recupera il titolo e le dimensioni del titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037879"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="253c5-104">GetConsoleTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="253c5-104">GetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="253c5-105">Recupera il titolo per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="253c5-105">Retrieves the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="253c5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="253c5-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="253c5-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="253c5-107">Parameters</span></span>

<span data-ttu-id="253c5-108">*lpConsoleTitle* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="253c5-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="253c5-109">Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo.</span><span class="sxs-lookup"><span data-stu-id="253c5-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="253c5-110">Se il buffer è troppo piccolo per archiviare il titolo, la funzione archivia il numero di caratteri del titolo che rientrerà nel buffer, terminando con un carattere di terminazione null.</span><span class="sxs-lookup"><span data-stu-id="253c5-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="253c5-111">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="253c5-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="253c5-112">Dimensioni del buffer a cui punta il parametro *lpConsoleTitle* , in caratteri.</span><span class="sxs-lookup"><span data-stu-id="253c5-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="253c5-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="253c5-113">Return value</span></span>

<span data-ttu-id="253c5-114">Se la funzione ha esito positivo, il valore restituito è la lunghezza del titolo della finestra della console, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="253c5-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="253c5-115">Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce il codice di errore.</span><span class="sxs-lookup"><span data-stu-id="253c5-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="253c5-116">Commenti</span><span class="sxs-lookup"><span data-stu-id="253c5-116">Remarks</span></span>

<span data-ttu-id="253c5-117">Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="253c5-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="253c5-118">Per recuperare la stringa del titolo originale, usare la funzione [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="253c5-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="253c5-119">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="253c5-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="253c5-120">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="253c5-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="253c5-121">Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.</span><span class="sxs-lookup"><span data-stu-id="253c5-121">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="examples"></a><span data-ttu-id="253c5-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="253c5-122">Examples</span></span>

<span data-ttu-id="253c5-123">Per un esempio, vedere [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="253c5-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="253c5-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="253c5-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="253c5-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="253c5-125">Minimum supported client</span></span> | <span data-ttu-id="253c5-126">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="253c5-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="253c5-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="253c5-127">Minimum supported server</span></span> | <span data-ttu-id="253c5-128">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="253c5-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="253c5-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="253c5-129">Header</span></span> | <span data-ttu-id="253c5-130">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="253c5-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="253c5-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="253c5-131">Library</span></span> | <span data-ttu-id="253c5-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="253c5-132">Kernel32.lib</span></span> |
| <span data-ttu-id="253c5-133">DLL</span><span class="sxs-lookup"><span data-stu-id="253c5-133">DLL</span></span> | <span data-ttu-id="253c5-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="253c5-134">Kernel32.dll</span></span> |
| <span data-ttu-id="253c5-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="253c5-135">Unicode and ANSI names</span></span> | <span data-ttu-id="253c5-136">**GetConsoleTitleW** (Unicode) e **GetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="253c5-136">**GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="253c5-137">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="253c5-137">See also</span></span>

[<span data-ttu-id="253c5-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="253c5-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="253c5-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="253c5-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="253c5-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="253c5-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="253c5-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="253c5-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="253c5-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="253c5-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)
