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
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037554"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="58102-104">AddConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="58102-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="58102-105">Definisce un alias di console per il file eseguibile specificato.</span><span class="sxs-lookup"><span data-stu-id="58102-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="58102-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="58102-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="58102-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="58102-107">Parameters</span></span>

<span data-ttu-id="58102-108">*Origine* \[ dati in\]</span><span class="sxs-lookup"><span data-stu-id="58102-108">*Source* \[in\]</span></span>  
<span data-ttu-id="58102-109">Alias della console di cui eseguire il mapping al testo specificato dalla *destinazione* .</span><span class="sxs-lookup"><span data-stu-id="58102-109">The console alias to be mapped to the text specified by *Target* .</span></span>

<span data-ttu-id="58102-110">*Destinazione* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="58102-110">*Target* \[in\]</span></span>  
<span data-ttu-id="58102-111">Testo da sostituire con l' *origine* .</span><span class="sxs-lookup"><span data-stu-id="58102-111">The text to be substituted for *Source* .</span></span> <span data-ttu-id="58102-112">Se questo parametro è **null** , l'alias della console verrà rimosso.</span><span class="sxs-lookup"><span data-stu-id="58102-112">If this parameter is **NULL** , then the console alias is removed.</span></span>

<span data-ttu-id="58102-113">*Exename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="58102-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="58102-114">Nome del file eseguibile per cui definire l'alias della console.</span><span class="sxs-lookup"><span data-stu-id="58102-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="58102-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="58102-115">Return value</span></span>

<span data-ttu-id="58102-116">Se la funzione ha esito positivo, il valore restituito è **true** .</span><span class="sxs-lookup"><span data-stu-id="58102-116">If the function succeeds, the return value is **TRUE** .</span></span>

<span data-ttu-id="58102-117">Se la funzione ha esito negativo, il valore restituito è **false** .</span><span class="sxs-lookup"><span data-stu-id="58102-117">If the function fails, the return value is **FALSE** .</span></span> <span data-ttu-id="58102-118">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="58102-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="58102-119">Commenti</span><span class="sxs-lookup"><span data-stu-id="58102-119">Remarks</span></span>

<span data-ttu-id="58102-120">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="58102-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="58102-121">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="58102-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="58102-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="58102-122">Examples</span></span>

<span data-ttu-id="58102-123">Per un esempio, vedere [alias di console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="58102-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="58102-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="58102-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="58102-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="58102-125">Minimum supported client</span></span> | <span data-ttu-id="58102-126">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="58102-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="58102-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="58102-127">Minimum supported server</span></span> | <span data-ttu-id="58102-128">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="58102-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="58102-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="58102-129">Header</span></span> | <span data-ttu-id="58102-130">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="58102-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="58102-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="58102-131">Library</span></span> | <span data-ttu-id="58102-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="58102-132">Kernel32.lib</span></span> |
| <span data-ttu-id="58102-133">DLL</span><span class="sxs-lookup"><span data-stu-id="58102-133">DLL</span></span> | <span data-ttu-id="58102-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="58102-134">Kernel32.dll</span></span> |
| <span data-ttu-id="58102-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="58102-135">Unicode and ANSI names</span></span> | <span data-ttu-id="58102-136">**AddConsoleAliasW** (Unicode) e **AddConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="58102-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="58102-137">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="58102-137">See also</span></span>

[<span data-ttu-id="58102-138">Alias di console</span><span class="sxs-lookup"><span data-stu-id="58102-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="58102-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="58102-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="58102-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="58102-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="58102-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="58102-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="58102-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="58102-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
