---
title: GetConsoleAliasExesLength (funzione)
description: Recupera la dimensione richiesta per il buffer usato dalla funzione GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4285bb64e919851a38494383a440afa6b94c8032
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358471"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="64bc5-104">GetConsoleAliasExesLength (funzione)</span><span class="sxs-lookup"><span data-stu-id="64bc5-104">GetConsoleAliasExesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="64bc5-105">Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="64bc5-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="64bc5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="64bc5-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a><span data-ttu-id="64bc5-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="64bc5-107">Parameters</span></span>

<span data-ttu-id="64bc5-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="64bc5-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="64bc5-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="64bc5-109">Return value</span></span>

<span data-ttu-id="64bc5-110">Dimensioni del buffer necessarie per archiviare i nomi di tutti i file eseguibili con alias di console definiti, in byte.</span><span class="sxs-lookup"><span data-stu-id="64bc5-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="64bc5-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="64bc5-111">Remarks</span></span>

<span data-ttu-id="64bc5-112">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="64bc5-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="64bc5-113">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="64bc5-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="64bc5-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="64bc5-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="64bc5-115">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="64bc5-115">Minimum supported client</span></span> | <span data-ttu-id="64bc5-116">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="64bc5-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="64bc5-117">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="64bc5-117">Minimum supported server</span></span> | <span data-ttu-id="64bc5-118">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="64bc5-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="64bc5-119">Intestazione</span><span class="sxs-lookup"><span data-stu-id="64bc5-119">Header</span></span> | <span data-ttu-id="64bc5-120">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="64bc5-120">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="64bc5-121">Libreria</span><span class="sxs-lookup"><span data-stu-id="64bc5-121">Library</span></span> | <span data-ttu-id="64bc5-122">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="64bc5-122">Kernel32.lib</span></span> |
| <span data-ttu-id="64bc5-123">DLL</span><span class="sxs-lookup"><span data-stu-id="64bc5-123">DLL</span></span> | <span data-ttu-id="64bc5-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64bc5-124">Kernel32.dll</span></span> |
| <span data-ttu-id="64bc5-125">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="64bc5-125">Unicode and ANSI names</span></span> | <span data-ttu-id="64bc5-126">**GetConsoleAliasExesLengthW** (Unicode) e **GetConsoleAliasExesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="64bc5-126">**GetConsoleAliasExesLengthW** (Unicode) and **GetConsoleAliasExesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="64bc5-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="64bc5-127">See also</span></span>

[<span data-ttu-id="64bc5-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="64bc5-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="64bc5-129">Alias di console</span><span class="sxs-lookup"><span data-stu-id="64bc5-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="64bc5-130">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="64bc5-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="64bc5-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="64bc5-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="64bc5-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="64bc5-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="64bc5-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="64bc5-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)