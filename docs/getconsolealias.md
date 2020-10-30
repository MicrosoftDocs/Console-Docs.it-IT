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
ms.openlocfilehash: 37c441c48c2bb71fc8e590d4f8a80032561f833e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039029"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="01350-104">GetConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="01350-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="01350-105">Recupera il testo per l'alias e l'eseguibile della console specificati.</span><span class="sxs-lookup"><span data-stu-id="01350-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="01350-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="01350-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="01350-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="01350-107">Parameters</span></span>

<span data-ttu-id="01350-108">*lpSource* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="01350-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="01350-109">Alias della console di cui deve essere recuperato il testo.</span><span class="sxs-lookup"><span data-stu-id="01350-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="01350-110">*lpTargetBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="01350-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="01350-111">Puntatore a un buffer che riceve il testo associato all'alias della console.</span><span class="sxs-lookup"><span data-stu-id="01350-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="01350-112">*TargetBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="01350-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="01350-113">Dimensioni del buffer a cui punta *lpTargetBuffer* in byte.</span><span class="sxs-lookup"><span data-stu-id="01350-113">The size of the buffer pointed to by *lpTargetBuffer* , in bytes.</span></span>

<span data-ttu-id="01350-114">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="01350-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="01350-115">Nome del file eseguibile.</span><span class="sxs-lookup"><span data-stu-id="01350-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="01350-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="01350-116">Return value</span></span>

<span data-ttu-id="01350-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="01350-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="01350-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="01350-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="01350-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="01350-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="01350-120">Commenti</span><span class="sxs-lookup"><span data-stu-id="01350-120">Remarks</span></span>

<span data-ttu-id="01350-121">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="01350-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="01350-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="01350-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="01350-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="01350-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="01350-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="01350-124">Minimum supported client</span></span> | <span data-ttu-id="01350-125">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="01350-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="01350-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="01350-126">Minimum supported server</span></span> | <span data-ttu-id="01350-127">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="01350-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="01350-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="01350-128">Header</span></span> | <span data-ttu-id="01350-129">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="01350-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="01350-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="01350-130">Library</span></span> | <span data-ttu-id="01350-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="01350-131">Kernel32.lib</span></span> |
| <span data-ttu-id="01350-132">DLL</span><span class="sxs-lookup"><span data-stu-id="01350-132">DLL</span></span> | <span data-ttu-id="01350-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="01350-133">Kernel32.dll</span></span> |
| <span data-ttu-id="01350-134">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="01350-134">Unicode and ANSI names</span></span> | <span data-ttu-id="01350-135">**GetConsoleAliasW** (Unicode) e **GetConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="01350-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="01350-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="01350-136">See also</span></span>

[<span data-ttu-id="01350-137">Alias di console</span><span class="sxs-lookup"><span data-stu-id="01350-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="01350-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="01350-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="01350-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="01350-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="01350-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="01350-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="01350-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="01350-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
