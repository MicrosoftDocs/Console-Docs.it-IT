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
ms.openlocfilehash: 395acba39600fe1a98a80ed06ea23646b0b9f174
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038959"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="78309-104">GetConsoleAliasesLength (funzione)</span><span class="sxs-lookup"><span data-stu-id="78309-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="78309-105">Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="78309-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="78309-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="78309-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="78309-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="78309-107">Parameters</span></span>

<span data-ttu-id="78309-108">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="78309-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="78309-109">Nome del file eseguibile di cui devono essere recuperati gli alias della console.</span><span class="sxs-lookup"><span data-stu-id="78309-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="78309-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="78309-110">Return value</span></span>

<span data-ttu-id="78309-111">Dimensioni del buffer necessarie per archiviare tutti gli alias di console definiti per il file eseguibile, in byte.</span><span class="sxs-lookup"><span data-stu-id="78309-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="78309-112">Commenti</span><span class="sxs-lookup"><span data-stu-id="78309-112">Remarks</span></span>

<span data-ttu-id="78309-113">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="78309-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="78309-114">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="78309-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="78309-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="78309-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="78309-116">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="78309-116">Minimum supported client</span></span> | <span data-ttu-id="78309-117">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="78309-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="78309-118">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="78309-118">Minimum supported server</span></span> | <span data-ttu-id="78309-119">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="78309-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="78309-120">Intestazione</span><span class="sxs-lookup"><span data-stu-id="78309-120">Header</span></span> | <span data-ttu-id="78309-121">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="78309-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="78309-122">Libreria</span><span class="sxs-lookup"><span data-stu-id="78309-122">Library</span></span> | <span data-ttu-id="78309-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="78309-123">Kernel32.lib</span></span> |
| <span data-ttu-id="78309-124">DLL</span><span class="sxs-lookup"><span data-stu-id="78309-124">DLL</span></span> | <span data-ttu-id="78309-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="78309-125">Kernel32.dll</span></span> |
| <span data-ttu-id="78309-126">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="78309-126">Unicode and ANSI names</span></span> | <span data-ttu-id="78309-127">**GetConsoleAliasesLengthW** (Unicode) e **GetConsoleAliasesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="78309-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="78309-128">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="78309-128">See also</span></span>

[<span data-ttu-id="78309-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="78309-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="78309-130">Alias di console</span><span class="sxs-lookup"><span data-stu-id="78309-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="78309-131">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="78309-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="78309-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="78309-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="78309-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="78309-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="78309-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="78309-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
