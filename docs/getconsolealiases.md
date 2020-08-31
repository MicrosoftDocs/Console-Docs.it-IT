---
title: GetConsoleAliases (funzione)
description: Recupera tutti gli alias di console definiti per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059817"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="f988b-104">GetConsoleAliases (funzione)</span><span class="sxs-lookup"><span data-stu-id="f988b-104">GetConsoleAliases function</span></span>


<span data-ttu-id="f988b-105">Recupera tutti gli alias della console definiti per il file eseguibile specificato.</span><span class="sxs-lookup"><span data-stu-id="f988b-105">Retrieves all defined console aliases for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="f988b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f988b-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="f988b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="f988b-107">Parameters</span></span>
----------

<span data-ttu-id="f988b-108">*lpAliasBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="f988b-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="f988b-109">Puntatore a un buffer che riceve gli alias.</span><span class="sxs-lookup"><span data-stu-id="f988b-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="f988b-110">Il formato dei dati è il seguente: *source1* = *Target1* \\ 0*source2* = *Target2* \\ 0... *Origine dati* = *Destinazione* \\ 0, dove *N* è il numero di alias di console definito.</span><span class="sxs-lookup"><span data-stu-id="f988b-110">The format of the data is as follows: *Source1*=*Target1*\\0*Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="f988b-111">*AliasBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f988b-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="f988b-112">Dimensioni del buffer a cui punta *lpAliasBuffer*in byte.</span><span class="sxs-lookup"><span data-stu-id="f988b-112">The size of the buffer pointed to by *lpAliasBuffer*, in bytes.</span></span>

<span data-ttu-id="f988b-113">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f988b-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="f988b-114">File eseguibile di cui devono essere recuperati gli alias.</span><span class="sxs-lookup"><span data-stu-id="f988b-114">The executable file whose aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="f988b-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f988b-115">Return value</span></span>
------------

<span data-ttu-id="f988b-116">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="f988b-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f988b-117">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="f988b-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f988b-118">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f988b-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f988b-119">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f988b-119">Remarks</span></span>
-------

<span data-ttu-id="f988b-120">Per determinare le dimensioni necessarie per il buffer *lpExeName* , usare la funzione [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .</span><span class="sxs-lookup"><span data-stu-id="f988b-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="f988b-121">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="f988b-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="f988b-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="f988b-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="f988b-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f988b-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f988b-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f988b-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f988b-125">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f988b-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f988b-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f988b-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f988b-127">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f988b-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f988b-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="f988b-128">Header</span></span></p></td>
<td><span data-ttu-id="f988b-129">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f988b-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f988b-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="f988b-130">Library</span></span></p></td>
<td><span data-ttu-id="f988b-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f988b-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f988b-132">DLL</span><span class="sxs-lookup"><span data-stu-id="f988b-132">DLL</span></span></p></td>
<td><span data-ttu-id="f988b-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f988b-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f988b-134">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="f988b-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="f988b-135"><strong>GetConsoleAliasesW</strong> (Unicode) e <strong>GetConsoleAliasesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f988b-135"><strong>GetConsoleAliasesW</strong> (Unicode) and <strong>GetConsoleAliasesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f988b-136"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f988b-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f988b-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="f988b-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="f988b-138">Alias di console</span><span class="sxs-lookup"><span data-stu-id="f988b-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="f988b-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="f988b-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f988b-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="f988b-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="f988b-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="f988b-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="f988b-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="f988b-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




