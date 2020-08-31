---
title: GetConsoleAliasExesLength (funzione)
description: Recupera la dimensione richiesta per il buffer usato dalla funzione GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059801"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="201ce-104">GetConsoleAliasExesLength (funzione)</span><span class="sxs-lookup"><span data-stu-id="201ce-104">GetConsoleAliasExesLength function</span></span>


<span data-ttu-id="201ce-105">Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="201ce-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="201ce-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="201ce-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a><span data-ttu-id="201ce-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="201ce-107">Parameters</span></span>
----------

<span data-ttu-id="201ce-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="201ce-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="201ce-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="201ce-109">Return value</span></span>
------------

<span data-ttu-id="201ce-110">Dimensioni del buffer necessarie per archiviare i nomi di tutti i file eseguibili con alias di console definiti, in byte.</span><span class="sxs-lookup"><span data-stu-id="201ce-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="201ce-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="201ce-111">Remarks</span></span>
-------

<span data-ttu-id="201ce-112">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="201ce-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="201ce-113">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="201ce-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="201ce-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="201ce-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="201ce-115">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="201ce-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="201ce-116">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="201ce-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="201ce-117">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="201ce-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="201ce-118">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="201ce-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="201ce-119">Intestazione</span><span class="sxs-lookup"><span data-stu-id="201ce-119">Header</span></span></p></td>
<td><span data-ttu-id="201ce-120">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="201ce-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="201ce-121">Libreria</span><span class="sxs-lookup"><span data-stu-id="201ce-121">Library</span></span></p></td>
<td><span data-ttu-id="201ce-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="201ce-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="201ce-123">DLL</span><span class="sxs-lookup"><span data-stu-id="201ce-123">DLL</span></span></p></td>
<td><span data-ttu-id="201ce-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="201ce-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="201ce-125">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="201ce-125">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="201ce-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) e <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="201ce-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) and <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="201ce-127"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="201ce-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="201ce-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="201ce-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="201ce-129">Alias di console</span><span class="sxs-lookup"><span data-stu-id="201ce-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="201ce-130">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="201ce-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="201ce-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="201ce-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="201ce-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="201ce-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="201ce-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="201ce-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




