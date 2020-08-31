---
title: GetConsoleAliasesLength (funzione)
description: Recupera la dimensione richiesta per il buffer usato dalla funzione GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 23d820574aab837c89f2598e9934536b91715426
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059809"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="5e3ad-104">GetConsoleAliasesLength (funzione)</span><span class="sxs-lookup"><span data-stu-id="5e3ad-104">GetConsoleAliasesLength function</span></span>


<span data-ttu-id="5e3ad-105">Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="5e3ad-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="5e3ad-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5e3ad-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="5e3ad-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5e3ad-107">Parameters</span></span>
----------

<span data-ttu-id="5e3ad-108">*lpExeName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="5e3ad-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="5e3ad-109">Nome del file eseguibile di cui devono essere recuperati gli alias della console.</span><span class="sxs-lookup"><span data-stu-id="5e3ad-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="5e3ad-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5e3ad-110">Return value</span></span>
------------

<span data-ttu-id="5e3ad-111">Dimensioni del buffer necessarie per archiviare tutti gli alias di console definiti per il file eseguibile, in byte.</span><span class="sxs-lookup"><span data-stu-id="5e3ad-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="5e3ad-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5e3ad-112">Remarks</span></span>
-------

<span data-ttu-id="5e3ad-113">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="5e3ad-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="5e3ad-114">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="5e3ad-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="5e3ad-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5e3ad-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5e3ad-116">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5e3ad-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5e3ad-117">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5e3ad-117">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e3ad-118">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5e3ad-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5e3ad-119">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="5e3ad-119">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5e3ad-120">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5e3ad-120">Header</span></span></p></td>
<td><span data-ttu-id="5e3ad-121">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5e3ad-121">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e3ad-122">Libreria</span><span class="sxs-lookup"><span data-stu-id="5e3ad-122">Library</span></span></p></td>
<td><span data-ttu-id="5e3ad-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5e3ad-123">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5e3ad-124">DLL</span><span class="sxs-lookup"><span data-stu-id="5e3ad-124">DLL</span></span></p></td>
<td><span data-ttu-id="5e3ad-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5e3ad-125">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e3ad-126">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="5e3ad-126">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="5e3ad-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) e <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5e3ad-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) and <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5e3ad-128"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5e3ad-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5e3ad-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="5e3ad-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="5e3ad-130">Alias di console</span><span class="sxs-lookup"><span data-stu-id="5e3ad-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="5e3ad-131">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="5e3ad-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5e3ad-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="5e3ad-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="5e3ad-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="5e3ad-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="5e3ad-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="5e3ad-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




