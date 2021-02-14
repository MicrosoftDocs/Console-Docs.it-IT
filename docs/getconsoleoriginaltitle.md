---
title: GetConsoleOriginalTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleOriginalTitle, che recupera il titolo originale per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359001"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="dcef9-104">GetConsoleOriginalTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="dcef9-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="dcef9-105">Recupera il titolo originale per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="dcef9-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcef9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dcef9-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="dcef9-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="dcef9-107">Parameters</span></span>

<span data-ttu-id="dcef9-108">*lpConsoleTitle* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="dcef9-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="dcef9-109">Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo originale.</span><span class="sxs-lookup"><span data-stu-id="dcef9-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="dcef9-110">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="dcef9-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="dcef9-111">Dimensioni del buffer *lpConsoleTitle* , in caratteri.</span><span class="sxs-lookup"><span data-stu-id="dcef9-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="dcef9-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="dcef9-112">Return value</span></span>

<span data-ttu-id="dcef9-113">Se la funzione ha esito positivo, il valore restituito corrisponde alla lunghezza della stringa copiata nel buffer, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="dcef9-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="dcef9-114">Se il buffer non è abbastanza grande per archiviare il titolo, il valore restituito è zero e [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) restituisce un **errore di \_ esito positivo**.</span><span class="sxs-lookup"><span data-stu-id="dcef9-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="dcef9-115">Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) restituisce il codice di errore.</span><span class="sxs-lookup"><span data-stu-id="dcef9-115">If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcef9-116">Commenti</span><span class="sxs-lookup"><span data-stu-id="dcef9-116">Remarks</span></span>

<span data-ttu-id="dcef9-117">Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="dcef9-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="dcef9-118">Per recuperare la stringa del titolo corrente, usare la funzione [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="dcef9-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="dcef9-119">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0600 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="dcef9-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="dcef9-120">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="dcef9-120">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

> [!TIP]
> <span data-ttu-id="dcef9-121">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="dcef9-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="dcef9-122">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="dcef9-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="dcef9-123">Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.</span><span class="sxs-lookup"><span data-stu-id="dcef9-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcef9-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dcef9-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="dcef9-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="dcef9-125">Minimum supported client</span></span> | <span data-ttu-id="dcef9-126">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="dcef9-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="dcef9-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="dcef9-127">Minimum supported server</span></span> | <span data-ttu-id="dcef9-128">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="dcef9-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="dcef9-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="dcef9-129">Header</span></span> | <span data-ttu-id="dcef9-130">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="dcef9-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="dcef9-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="dcef9-131">Library</span></span> | <span data-ttu-id="dcef9-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="dcef9-132">Kernel32.lib</span></span> |
| <span data-ttu-id="dcef9-133">DLL</span><span class="sxs-lookup"><span data-stu-id="dcef9-133">DLL</span></span> | <span data-ttu-id="dcef9-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="dcef9-134">Kernel32.dll</span></span> |
| <span data-ttu-id="dcef9-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="dcef9-135">Unicode and ANSI names</span></span> | <span data-ttu-id="dcef9-136">**GetConsoleOriginalTitleW** (Unicode) e **GetConsoleOriginalTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="dcef9-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="dcef9-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dcef9-137">See also</span></span>

[<span data-ttu-id="dcef9-138">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="dcef9-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="dcef9-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="dcef9-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="dcef9-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="dcef9-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)