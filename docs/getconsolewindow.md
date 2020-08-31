---
title: GetConsoleWindow (funzione)
description: Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059676"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="d0a6e-104">GetConsoleWindow (funzione)</span><span class="sxs-lookup"><span data-stu-id="d0a6e-104">GetConsoleWindow function</span></span>


<span data-ttu-id="d0a6e-105">Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="d0a6e-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="d0a6e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d0a6e-106">Syntax</span></span>
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a><span data-ttu-id="d0a6e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d0a6e-107">Parameters</span></span>
----------

<span data-ttu-id="d0a6e-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="d0a6e-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="d0a6e-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d0a6e-109">Return value</span></span>
------------

<span data-ttu-id="d0a6e-110">Il valore restituito è un handle per la finestra utilizzata dalla console associata al processo chiamante oppure **null** se tale console associata non è presente.</span><span class="sxs-lookup"><span data-stu-id="d0a6e-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

<a name="remarks"></a><span data-ttu-id="d0a6e-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d0a6e-111">Remarks</span></span>
-------

<span data-ttu-id="d0a6e-112">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="d0a6e-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="d0a6e-113">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="d0a6e-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="d0a6e-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d0a6e-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d0a6e-115">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d0a6e-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d0a6e-116">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="d0a6e-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d0a6e-117">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d0a6e-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d0a6e-118">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="d0a6e-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d0a6e-119">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d0a6e-119">Header</span></span></p></td>
<td><span data-ttu-id="d0a6e-120">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d0a6e-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d0a6e-121">Libreria</span><span class="sxs-lookup"><span data-stu-id="d0a6e-121">Library</span></span></p></td>
<td><span data-ttu-id="d0a6e-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d0a6e-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d0a6e-123">DLL</span><span class="sxs-lookup"><span data-stu-id="d0a6e-123">DLL</span></span></p></td>
<td><span data-ttu-id="d0a6e-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d0a6e-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d0a6e-125"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0a6e-125"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d0a6e-126">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="d0a6e-126">Console Functions</span></span>](console-functions.md)

 

 




