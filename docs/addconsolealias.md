---
title: AddConsoleAlias (funzione)
description: Vedere le informazioni di riferimento sulla funzione AddConsoleAlias, che definisce un alias di console per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357871"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="cd729-104">AddConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="cd729-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="cd729-105">Definisce un alias di console per il file eseguibile specificato.</span><span class="sxs-lookup"><span data-stu-id="cd729-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd729-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cd729-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="cd729-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="cd729-107">Parameters</span></span>

<span data-ttu-id="cd729-108">*Origine* \[ dati in\]</span><span class="sxs-lookup"><span data-stu-id="cd729-108">*Source* \[in\]</span></span>  
<span data-ttu-id="cd729-109">Alias della console di cui eseguire il mapping al testo specificato dalla *destinazione*.</span><span class="sxs-lookup"><span data-stu-id="cd729-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="cd729-110">*Destinazione* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="cd729-110">*Target* \[in\]</span></span>  
<span data-ttu-id="cd729-111">Testo da sostituire con l' *origine*.</span><span class="sxs-lookup"><span data-stu-id="cd729-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="cd729-112">Se questo parametro è **null**, l'alias della console verrà rimosso.</span><span class="sxs-lookup"><span data-stu-id="cd729-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="cd729-113">*Exename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="cd729-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="cd729-114">Nome del file eseguibile per cui definire l'alias della console.</span><span class="sxs-lookup"><span data-stu-id="cd729-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd729-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="cd729-115">Return value</span></span>

<span data-ttu-id="cd729-116">Se la funzione ha esito positivo, il valore restituito è **true**.</span><span class="sxs-lookup"><span data-stu-id="cd729-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="cd729-117">Se la funzione ha esito negativo, il valore restituito è **false**.</span><span class="sxs-lookup"><span data-stu-id="cd729-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="cd729-118">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="cd729-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="cd729-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cd729-119">Remarks</span></span>

<span data-ttu-id="cd729-120">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="cd729-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="cd729-121">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="cd729-121">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="cd729-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="cd729-122">Examples</span></span>

<span data-ttu-id="cd729-123">Per un esempio, vedere [alias di console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="cd729-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cd729-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cd729-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cd729-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cd729-125">Minimum supported client</span></span> | <span data-ttu-id="cd729-126">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="cd729-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cd729-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cd729-127">Minimum supported server</span></span> | <span data-ttu-id="cd729-128">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="cd729-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cd729-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="cd729-129">Header</span></span> | <span data-ttu-id="cd729-130">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cd729-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cd729-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="cd729-131">Library</span></span> | <span data-ttu-id="cd729-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="cd729-132">Kernel32.lib</span></span> |
| <span data-ttu-id="cd729-133">DLL</span><span class="sxs-lookup"><span data-stu-id="cd729-133">DLL</span></span> | <span data-ttu-id="cd729-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cd729-134">Kernel32.dll</span></span> |
| <span data-ttu-id="cd729-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="cd729-135">Unicode and ANSI names</span></span> | <span data-ttu-id="cd729-136">**AddConsoleAliasW** (Unicode) e **AddConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="cd729-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="cd729-137">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="cd729-137">See also</span></span>

[<span data-ttu-id="cd729-138">Alias di console</span><span class="sxs-lookup"><span data-stu-id="cd729-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="cd729-139">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="cd729-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cd729-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="cd729-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="cd729-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="cd729-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="cd729-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="cd729-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)