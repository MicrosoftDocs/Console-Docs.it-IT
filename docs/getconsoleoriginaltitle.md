---
title: GetConsoleOriginalTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleOriginalTitle, che recupera il titolo originale per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059737"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="8462c-104">GetConsoleOriginalTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="8462c-104">GetConsoleOriginalTitle function</span></span>


<span data-ttu-id="8462c-105">Recupera il titolo originale per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="8462c-105">Retrieves the original title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="8462c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8462c-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="8462c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8462c-107">Parameters</span></span>
----------

<span data-ttu-id="8462c-108">*lpConsoleTitle* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8462c-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="8462c-109">Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo originale.</span><span class="sxs-lookup"><span data-stu-id="8462c-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="8462c-110">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8462c-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="8462c-111">Dimensioni del buffer *lpConsoleTitle* , in caratteri.</span><span class="sxs-lookup"><span data-stu-id="8462c-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="8462c-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8462c-112">Return value</span></span>
------------

<span data-ttu-id="8462c-113">Se la funzione ha esito positivo, il valore restituito corrisponde alla lunghezza della stringa copiata nel buffer, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="8462c-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="8462c-114">Se il buffer non è abbastanza grande per archiviare il titolo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce un **errore di \_ esito positivo**.</span><span class="sxs-lookup"><span data-stu-id="8462c-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="8462c-115">Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce il codice di errore.</span><span class="sxs-lookup"><span data-stu-id="8462c-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="8462c-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8462c-116">Remarks</span></span>
-------

<span data-ttu-id="8462c-117">Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="8462c-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="8462c-118">Per recuperare la stringa del titolo corrente, usare la funzione [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="8462c-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="8462c-119">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0600 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="8462c-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="8462c-120">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="8462c-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="8462c-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8462c-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8462c-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8462c-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8462c-123">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8462c-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8462c-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8462c-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8462c-125">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8462c-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8462c-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8462c-126">Header</span></span></p></td>
<td><span data-ttu-id="8462c-127">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8462c-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8462c-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="8462c-128">Library</span></span></p></td>
<td><span data-ttu-id="8462c-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8462c-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8462c-130">DLL</span><span class="sxs-lookup"><span data-stu-id="8462c-130">DLL</span></span></p></td>
<td><span data-ttu-id="8462c-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8462c-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8462c-132">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="8462c-132">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="8462c-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) e <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="8462c-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8462c-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8462c-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8462c-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="8462c-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8462c-136">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="8462c-136">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="8462c-137">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="8462c-137">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




