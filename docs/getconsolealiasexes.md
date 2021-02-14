---
title: GetConsoleAliasExes (funzione)
description: Recupera i nomi di tutti i file eseguibili con alias di console definiti.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357494"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="ec8f4-104">GetConsoleAliasExes (funzione)</span><span class="sxs-lookup"><span data-stu-id="ec8f4-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ec8f4-105">Recupera i nomi di tutti i file eseguibili con alias di console definiti.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec8f4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ec8f4-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="ec8f4-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ec8f4-107">Parameters</span></span>

<span data-ttu-id="ec8f4-108">*lpExeNameBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="ec8f4-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="ec8f4-109">Puntatore a un buffer che riceve i nomi dei file eseguibili.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="ec8f4-110">*ExeNameBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ec8f4-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="ec8f4-111">Dimensioni del buffer a cui punta *lpExeNameBuffer* in byte.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec8f4-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ec8f4-112">Return value</span></span>

<span data-ttu-id="ec8f4-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ec8f4-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ec8f4-115">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="ec8f4-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ec8f4-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ec8f4-116">Remarks</span></span>

<span data-ttu-id="ec8f4-117">Per determinare le dimensioni necessarie per il buffer *lpExeNameBuffer* , usare la funzione [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="ec8f4-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="ec8f4-118">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ec8f4-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ec8f4-119">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="ec8f4-119">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ec8f4-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ec8f4-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ec8f4-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ec8f4-121">Minimum supported client</span></span> | <span data-ttu-id="ec8f4-122">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="ec8f4-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec8f4-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ec8f4-123">Minimum supported server</span></span> | <span data-ttu-id="ec8f4-124">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="ec8f4-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ec8f4-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="ec8f4-125">Header</span></span> | <span data-ttu-id="ec8f4-126">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ec8f4-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ec8f4-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="ec8f4-127">Library</span></span> | <span data-ttu-id="ec8f4-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ec8f4-128">Kernel32.lib</span></span> |
| <span data-ttu-id="ec8f4-129">DLL</span><span class="sxs-lookup"><span data-stu-id="ec8f4-129">DLL</span></span> | <span data-ttu-id="ec8f4-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ec8f4-130">Kernel32.dll</span></span> |
| <span data-ttu-id="ec8f4-131">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="ec8f4-131">Unicode and ANSI names</span></span> | <span data-ttu-id="ec8f4-132">**GetConsoleAliasExesW** (Unicode) e **GetConsoleAliasExesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ec8f4-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec8f4-133">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ec8f4-133">See also</span></span>

[<span data-ttu-id="ec8f4-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ec8f4-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ec8f4-135">Alias di console</span><span class="sxs-lookup"><span data-stu-id="ec8f4-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ec8f4-136">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="ec8f4-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ec8f4-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ec8f4-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="ec8f4-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="ec8f4-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="ec8f4-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="ec8f4-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)