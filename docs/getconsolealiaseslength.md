---
title: GetConsoleAliasesLength (funzione)
description: Recupera la dimensione richiesta per il buffer usato dalla funzione GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 78f9d718c960478e491b76a12f2a670c03529242
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357500"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="fff43-104">GetConsoleAliasesLength (funzione)</span><span class="sxs-lookup"><span data-stu-id="fff43-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="fff43-105">Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="fff43-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="fff43-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fff43-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="fff43-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="fff43-107">Parameters</span></span>

<span data-ttu-id="fff43-108">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fff43-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="fff43-109">Nome del file eseguibile di cui devono essere recuperati gli alias della console.</span><span class="sxs-lookup"><span data-stu-id="fff43-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="fff43-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="fff43-110">Return value</span></span>

<span data-ttu-id="fff43-111">Dimensioni del buffer necessarie per archiviare tutti gli alias di console definiti per il file eseguibile, in byte.</span><span class="sxs-lookup"><span data-stu-id="fff43-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="fff43-112">Commenti</span><span class="sxs-lookup"><span data-stu-id="fff43-112">Remarks</span></span>

<span data-ttu-id="fff43-113">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="fff43-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="fff43-114">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="fff43-114">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="fff43-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fff43-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fff43-116">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fff43-116">Minimum supported client</span></span> | <span data-ttu-id="fff43-117">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="fff43-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fff43-118">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fff43-118">Minimum supported server</span></span> | <span data-ttu-id="fff43-119">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="fff43-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fff43-120">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fff43-120">Header</span></span> | <span data-ttu-id="fff43-121">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fff43-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fff43-122">Libreria</span><span class="sxs-lookup"><span data-stu-id="fff43-122">Library</span></span> | <span data-ttu-id="fff43-123">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="fff43-123">Kernel32.lib</span></span> |
| <span data-ttu-id="fff43-124">DLL</span><span class="sxs-lookup"><span data-stu-id="fff43-124">DLL</span></span> | <span data-ttu-id="fff43-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fff43-125">Kernel32.dll</span></span> |
| <span data-ttu-id="fff43-126">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="fff43-126">Unicode and ANSI names</span></span> | <span data-ttu-id="fff43-127">**GetConsoleAliasesLengthW** (Unicode) e **GetConsoleAliasesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="fff43-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fff43-128">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fff43-128">See also</span></span>

[<span data-ttu-id="fff43-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="fff43-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="fff43-130">Alias di console</span><span class="sxs-lookup"><span data-stu-id="fff43-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="fff43-131">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="fff43-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fff43-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="fff43-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="fff43-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="fff43-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="fff43-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="fff43-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)