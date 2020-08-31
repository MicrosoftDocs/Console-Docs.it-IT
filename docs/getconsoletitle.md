---
title: GetConsoleTitle (funzione)
description: Recupera il titolo e le dimensioni del titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059700"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="79250-104">GetConsoleTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="79250-104">GetConsoleTitle function</span></span>


<span data-ttu-id="79250-105">Recupera il titolo per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="79250-105">Retrieves the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="79250-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="79250-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="79250-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="79250-107">Parameters</span></span>
----------

<span data-ttu-id="79250-108">*lpConsoleTitle* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="79250-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="79250-109">Puntatore a un buffer che riceve una stringa con terminazione null che contiene il titolo.</span><span class="sxs-lookup"><span data-stu-id="79250-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="79250-110">Se il buffer è troppo piccolo per archiviare il titolo, la funzione archivia il numero di caratteri del titolo che rientrerà nel buffer, terminando con un carattere di terminazione null.</span><span class="sxs-lookup"><span data-stu-id="79250-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="79250-111">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="79250-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="79250-112">Dimensioni del buffer a cui punta il parametro *lpConsoleTitle* , in caratteri.</span><span class="sxs-lookup"><span data-stu-id="79250-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="79250-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="79250-113">Return value</span></span>
------------

<span data-ttu-id="79250-114">Se la funzione ha esito positivo, il valore restituito è la lunghezza del titolo della finestra della console, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="79250-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="79250-115">Se la funzione ha esito negativo, il valore restituito è zero e [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) restituisce il codice di errore.</span><span class="sxs-lookup"><span data-stu-id="79250-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="79250-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="79250-116">Remarks</span></span>
-------

<span data-ttu-id="79250-117">Per impostare il titolo di una finestra della console, usare la funzione [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="79250-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="79250-118">Per recuperare la stringa del titolo originale, usare la funzione [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="79250-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

<span data-ttu-id="79250-119">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="79250-119">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="79250-120">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="79250-120">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="79250-121">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="79250-121">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="79250-122">Esempi</span><span class="sxs-lookup"><span data-stu-id="79250-122">Examples</span></span>
--------

<span data-ttu-id="79250-123">Per un esempio, vedere [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="79250-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

<a name="requirements"></a><span data-ttu-id="79250-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="79250-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="79250-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="79250-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="79250-126">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="79250-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="79250-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="79250-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="79250-128">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="79250-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="79250-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="79250-129">Header</span></span></p></td>
<td><span data-ttu-id="79250-130">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="79250-130">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="79250-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="79250-131">Library</span></span></p></td>
<td><span data-ttu-id="79250-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="79250-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="79250-133">DLL</span><span class="sxs-lookup"><span data-stu-id="79250-133">DLL</span></span></p></td>
<td><span data-ttu-id="79250-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="79250-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="79250-135">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="79250-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="79250-136"><strong>GetConsoleTitleW</strong> (Unicode) e <strong>GetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="79250-136"><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="79250-137"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="79250-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="79250-138">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="79250-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="79250-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="79250-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="79250-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="79250-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="79250-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="79250-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="79250-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="79250-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




