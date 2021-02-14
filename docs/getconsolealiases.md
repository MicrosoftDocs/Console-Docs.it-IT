---
title: GetConsoleAliases (funzione)
description: Recupera tutti gli alias di console definiti per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a2a59f75c41f929660f6f4af1573b470fccd6511
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357571"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="26143-104">GetConsoleAliases (funzione)</span><span class="sxs-lookup"><span data-stu-id="26143-104">GetConsoleAliases function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="26143-105">Recupera tutti gli alias della console definiti per il file eseguibile specificato.</span><span class="sxs-lookup"><span data-stu-id="26143-105">Retrieves all defined console aliases for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="26143-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="26143-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="26143-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="26143-107">Parameters</span></span>

<span data-ttu-id="26143-108">*lpAliasBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="26143-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="26143-109">Puntatore a un buffer che riceve gli alias.</span><span class="sxs-lookup"><span data-stu-id="26143-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="26143-110">Il formato dei dati è il seguente: *source1* = *Target1* \\ 0 *source2* = *Target2* \\ 0... *Origine dati* = *Destinazione* \\ 0, dove *N* è il numero di alias di console definito.</span><span class="sxs-lookup"><span data-stu-id="26143-110">The format of the data is as follows: *Source1*=*Target1*\\0 *Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="26143-111">*AliasBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="26143-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="26143-112">Dimensioni del buffer a cui punta *lpAliasBuffer* in byte.</span><span class="sxs-lookup"><span data-stu-id="26143-112">The size of the buffer pointed to by *lpAliasBuffer*, in bytes.</span></span>

<span data-ttu-id="26143-113">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="26143-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="26143-114">File eseguibile di cui devono essere recuperati gli alias.</span><span class="sxs-lookup"><span data-stu-id="26143-114">The executable file whose aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="26143-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="26143-115">Return value</span></span>

<span data-ttu-id="26143-116">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="26143-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="26143-117">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="26143-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="26143-118">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="26143-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="26143-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="26143-119">Remarks</span></span>

<span data-ttu-id="26143-120">Per determinare le dimensioni necessarie per il buffer *lpExeName* , usare la funzione [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .</span><span class="sxs-lookup"><span data-stu-id="26143-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="26143-121">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="26143-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="26143-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="26143-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="26143-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="26143-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="26143-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="26143-124">Minimum supported client</span></span> | <span data-ttu-id="26143-125">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="26143-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="26143-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="26143-126">Minimum supported server</span></span> | <span data-ttu-id="26143-127">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="26143-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="26143-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="26143-128">Header</span></span> | <span data-ttu-id="26143-129">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="26143-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="26143-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="26143-130">Library</span></span> | <span data-ttu-id="26143-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="26143-131">Kernel32.lib</span></span> |
| <span data-ttu-id="26143-132">DLL</span><span class="sxs-lookup"><span data-stu-id="26143-132">DLL</span></span> | <span data-ttu-id="26143-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="26143-133">Kernel32.dll</span></span> |
| <span data-ttu-id="26143-134">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="26143-134">Unicode and ANSI names</span></span> | <span data-ttu-id="26143-135">**GetConsoleAliasesW** (Unicode) e **GetConsoleAliasesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="26143-135">**GetConsoleAliasesW** (Unicode) and **GetConsoleAliasesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="26143-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="26143-136">See also</span></span>

[<span data-ttu-id="26143-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="26143-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="26143-138">Alias di console</span><span class="sxs-lookup"><span data-stu-id="26143-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="26143-139">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="26143-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="26143-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="26143-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="26143-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="26143-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="26143-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="26143-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)