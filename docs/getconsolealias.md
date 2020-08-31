---
title: GetConsoleAlias (funzione)
description: Recupera il testo per l'alias della console specificato e il nome del file eseguibile.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 3a7797db4b559e66c1ec30f72e148ff00e79e7aa
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059825"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="5733e-104">GetConsoleAlias (funzione)</span><span class="sxs-lookup"><span data-stu-id="5733e-104">GetConsoleAlias function</span></span>


<span data-ttu-id="5733e-105">Recupera il testo per l'alias e l'eseguibile della console specificati.</span><span class="sxs-lookup"><span data-stu-id="5733e-105">Retrieves the text for the specified console alias and executable.</span></span>

<a name="syntax"></a><span data-ttu-id="5733e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5733e-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="5733e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5733e-107">Parameters</span></span>
----------

<span data-ttu-id="5733e-108">*lpSource* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5733e-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="5733e-109">Alias della console di cui deve essere recuperato il testo.</span><span class="sxs-lookup"><span data-stu-id="5733e-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="5733e-110">*lpTargetBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="5733e-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="5733e-111">Puntatore a un buffer che riceve il testo associato all'alias della console.</span><span class="sxs-lookup"><span data-stu-id="5733e-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="5733e-112">*TargetBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5733e-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="5733e-113">Dimensioni del buffer a cui punta *lpTargetBuffer*in byte.</span><span class="sxs-lookup"><span data-stu-id="5733e-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="5733e-114">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5733e-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="5733e-115">Nome del file eseguibile.</span><span class="sxs-lookup"><span data-stu-id="5733e-115">The name of the executable file.</span></span>

<a name="return-value"></a><span data-ttu-id="5733e-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5733e-116">Return value</span></span>
------------

<span data-ttu-id="5733e-117">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="5733e-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5733e-118">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="5733e-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5733e-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="5733e-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="5733e-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5733e-120">Remarks</span></span>
-------

<span data-ttu-id="5733e-121">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="5733e-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="5733e-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="5733e-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="5733e-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5733e-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5733e-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5733e-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5733e-125">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5733e-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5733e-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5733e-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5733e-127">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5733e-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5733e-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5733e-128">Header</span></span></p></td>
<td><span data-ttu-id="5733e-129">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5733e-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5733e-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="5733e-130">Library</span></span></p></td>
<td><span data-ttu-id="5733e-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5733e-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5733e-132">DLL</span><span class="sxs-lookup"><span data-stu-id="5733e-132">DLL</span></span></p></td>
<td><span data-ttu-id="5733e-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5733e-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5733e-134">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="5733e-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="5733e-135"><strong>GetConsoleAliasW</strong> (Unicode) e <strong>GetConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5733e-135"><strong>GetConsoleAliasW</strong> (Unicode) and <strong>GetConsoleAliasA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5733e-136"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5733e-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5733e-137">Alias di console</span><span class="sxs-lookup"><span data-stu-id="5733e-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="5733e-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="5733e-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5733e-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="5733e-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="5733e-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="5733e-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="5733e-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="5733e-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




