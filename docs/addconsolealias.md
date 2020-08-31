---
title: AddConsoleAlias (funzione)
description: Vedere le informazioni di riferimento sulla funzione AddConsoleAlias, che definisce un alias di console per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060241"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="49684-104">AddConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="49684-104">AddConsoleAlias function</span></span>


<span data-ttu-id="49684-105">Definisce un alias di console per il file eseguibile specificato.</span><span class="sxs-lookup"><span data-stu-id="49684-105">Defines a console alias for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="49684-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="49684-106">Syntax</span></span>
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a><span data-ttu-id="49684-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="49684-107">Parameters</span></span>
----------

<span data-ttu-id="49684-108">*Origine* \[ dati in\]</span><span class="sxs-lookup"><span data-stu-id="49684-108">*Source* \[in\]</span></span>  
<span data-ttu-id="49684-109">Alias della console di cui eseguire il mapping al testo specificato dalla *destinazione*.</span><span class="sxs-lookup"><span data-stu-id="49684-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="49684-110">*Destinazione* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="49684-110">*Target* \[in\]</span></span>  
<span data-ttu-id="49684-111">Testo da sostituire con l' *origine*.</span><span class="sxs-lookup"><span data-stu-id="49684-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="49684-112">Se questo parametro è **null**, l'alias della console verrà rimosso.</span><span class="sxs-lookup"><span data-stu-id="49684-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="49684-113">*Exename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="49684-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="49684-114">Nome del file eseguibile per cui definire l'alias della console.</span><span class="sxs-lookup"><span data-stu-id="49684-114">The name of the executable file for which the console alias is to be defined.</span></span>

<a name="return-value"></a><span data-ttu-id="49684-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="49684-115">Return value</span></span>
------------

<span data-ttu-id="49684-116">Se la funzione ha esito positivo, il valore restituito è **true**.</span><span class="sxs-lookup"><span data-stu-id="49684-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="49684-117">Se la funzione ha esito negativo, il valore restituito è **false**.</span><span class="sxs-lookup"><span data-stu-id="49684-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="49684-118">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="49684-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="49684-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="49684-119">Remarks</span></span>
-------

<span data-ttu-id="49684-120">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="49684-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="49684-121">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="49684-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="examples"></a><span data-ttu-id="49684-122">Esempi</span><span class="sxs-lookup"><span data-stu-id="49684-122">Examples</span></span>
--------

<span data-ttu-id="49684-123">Per un esempio, vedere [alias di console](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="49684-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

<a name="requirements"></a><span data-ttu-id="49684-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="49684-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="49684-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="49684-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="49684-126">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="49684-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="49684-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="49684-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="49684-128">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="49684-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="49684-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="49684-129">Header</span></span></p></td>
<td><span data-ttu-id="49684-130">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="49684-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="49684-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="49684-131">Library</span></span></p></td>
<td><span data-ttu-id="49684-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="49684-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="49684-133">DLL</span><span class="sxs-lookup"><span data-stu-id="49684-133">DLL</span></span></p></td>
<td><span data-ttu-id="49684-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="49684-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="49684-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="49684-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="49684-136"><strong>AddConsoleAliasW</strong> (Unicode) e <strong>AddConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="49684-136"><strong>AddConsoleAliasW</strong> (Unicode) and <strong>AddConsoleAliasA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="49684-137"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="49684-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="49684-138">Alias di console</span><span class="sxs-lookup"><span data-stu-id="49684-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="49684-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="49684-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="49684-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="49684-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="49684-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="49684-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="49684-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="49684-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




