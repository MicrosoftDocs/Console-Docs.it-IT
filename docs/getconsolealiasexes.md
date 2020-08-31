---
title: GetConsoleAliasExes (funzione)
description: Recupera i nomi di tutti i file eseguibili con alias di console definiti.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e112112fc1510ab4c3f0a99ff9b208cc364e361a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059820"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="cbce9-104">GetConsoleAliasExes (funzione)</span><span class="sxs-lookup"><span data-stu-id="cbce9-104">GetConsoleAliasExes function</span></span>


<span data-ttu-id="cbce9-105">Recupera i nomi di tutti i file eseguibili con alias di console definiti.</span><span class="sxs-lookup"><span data-stu-id="cbce9-105">Retrieves the names of all executable files with console aliases defined.</span></span>

<a name="syntax"></a><span data-ttu-id="cbce9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cbce9-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

<a name="parameters"></a><span data-ttu-id="cbce9-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="cbce9-107">Parameters</span></span>
----------

<span data-ttu-id="cbce9-108">*lpExeNameBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="cbce9-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="cbce9-109">Puntatore a un buffer che riceve i nomi dei file eseguibili.</span><span class="sxs-lookup"><span data-stu-id="cbce9-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="cbce9-110">*ExeNameBufferLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="cbce9-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="cbce9-111">Dimensioni del buffer a cui punta *lpExeNameBuffer*in byte.</span><span class="sxs-lookup"><span data-stu-id="cbce9-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

<a name="return-value"></a><span data-ttu-id="cbce9-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="cbce9-112">Return value</span></span>
------------

<span data-ttu-id="cbce9-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="cbce9-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cbce9-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="cbce9-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cbce9-115">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="cbce9-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="cbce9-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cbce9-116">Remarks</span></span>
-------

<span data-ttu-id="cbce9-117">Per determinare le dimensioni necessarie per il buffer *lpExeNameBuffer* , usare la funzione [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="cbce9-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="cbce9-118">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="cbce9-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="cbce9-119">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="cbce9-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="cbce9-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cbce9-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="cbce9-121">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cbce9-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="cbce9-122">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="cbce9-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cbce9-123">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="cbce9-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="cbce9-124">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="cbce9-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cbce9-125">Intestazione</span><span class="sxs-lookup"><span data-stu-id="cbce9-125">Header</span></span></p></td>
<td><span data-ttu-id="cbce9-126">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cbce9-126">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cbce9-127">Libreria</span><span class="sxs-lookup"><span data-stu-id="cbce9-127">Library</span></span></p></td>
<td><span data-ttu-id="cbce9-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cbce9-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cbce9-129">DLL</span><span class="sxs-lookup"><span data-stu-id="cbce9-129">DLL</span></span></p></td>
<td><span data-ttu-id="cbce9-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cbce9-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cbce9-131">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="cbce9-131">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="cbce9-132"><strong>GetConsoleAliasExesW</strong> (Unicode) e <strong>GetConsoleAliasExesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="cbce9-132"><strong>GetConsoleAliasExesW</strong> (Unicode) and <strong>GetConsoleAliasExesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="cbce9-133"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cbce9-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="cbce9-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="cbce9-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="cbce9-135">Alias di console</span><span class="sxs-lookup"><span data-stu-id="cbce9-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="cbce9-136">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="cbce9-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cbce9-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="cbce9-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="cbce9-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="cbce9-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="cbce9-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="cbce9-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)

 

 




