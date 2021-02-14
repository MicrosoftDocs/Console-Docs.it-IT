---
title: GetConsoleAlias (funzione)
description: Recupera il testo per l'alias della console specificato e il nome del file eseguibile.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d3706ddb86c270aeaf22f46e08e5381c79fea0bb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357541"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="105d4-104">GetConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="105d4-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="105d4-105">Recupera il testo per l'alias e l'eseguibile della console specificati.</span><span class="sxs-lookup"><span data-stu-id="105d4-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="105d4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="105d4-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="105d4-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="105d4-107">Parameters</span></span>

<span data-ttu-id="105d4-108">*lpSource* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="105d4-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="105d4-109">Alias della console di cui deve essere recuperato il testo.</span><span class="sxs-lookup"><span data-stu-id="105d4-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="105d4-110">*lpTargetBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="105d4-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="105d4-111">Puntatore a un buffer che riceve il testo associato all'alias della console.</span><span class="sxs-lookup"><span data-stu-id="105d4-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="105d4-112">*TargetBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="105d4-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="105d4-113">Dimensioni del buffer a cui punta *lpTargetBuffer* in byte.</span><span class="sxs-lookup"><span data-stu-id="105d4-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="105d4-114">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="105d4-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="105d4-115">Nome del file eseguibile.</span><span class="sxs-lookup"><span data-stu-id="105d4-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="105d4-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="105d4-116">Return value</span></span>

<span data-ttu-id="105d4-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="105d4-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="105d4-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="105d4-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="105d4-119">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="105d4-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="105d4-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="105d4-120">Remarks</span></span>

<span data-ttu-id="105d4-121">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="105d4-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="105d4-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="105d4-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="105d4-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="105d4-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="105d4-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="105d4-124">Minimum supported client</span></span> | <span data-ttu-id="105d4-125">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="105d4-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="105d4-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="105d4-126">Minimum supported server</span></span> | <span data-ttu-id="105d4-127">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="105d4-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="105d4-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="105d4-128">Header</span></span> | <span data-ttu-id="105d4-129">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="105d4-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="105d4-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="105d4-130">Library</span></span> | <span data-ttu-id="105d4-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="105d4-131">Kernel32.lib</span></span> |
| <span data-ttu-id="105d4-132">DLL</span><span class="sxs-lookup"><span data-stu-id="105d4-132">DLL</span></span> | <span data-ttu-id="105d4-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="105d4-133">Kernel32.dll</span></span> |
| <span data-ttu-id="105d4-134">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="105d4-134">Unicode and ANSI names</span></span> | <span data-ttu-id="105d4-135">**GetConsoleAliasW** (Unicode) e **GetConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="105d4-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="105d4-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="105d4-136">See also</span></span>

[<span data-ttu-id="105d4-137">Alias di console</span><span class="sxs-lookup"><span data-stu-id="105d4-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="105d4-138">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="105d4-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="105d4-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="105d4-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="105d4-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="105d4-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="105d4-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="105d4-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)