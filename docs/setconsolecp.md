---
title: SetConsoleCP (funzione)
description: Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060297"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="2a6e5-104">SetConsoleCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-104">SetConsoleCP function</span></span>


<span data-ttu-id="2a6e5-105">Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="2a6e5-106">Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="2a6e5-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2a6e5-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="2a6e5-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="2a6e5-108">Parameters</span></span>
----------

<span data-ttu-id="2a6e5-109">*wCodePageID* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2a6e5-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="2a6e5-110">Identificatore della tabella codici da impostare.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="2a6e5-111">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="2a6e5-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2a6e5-112">Return value</span></span>
------------

<span data-ttu-id="2a6e5-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2a6e5-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2a6e5-115">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2a6e5-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2a6e5-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2a6e5-116">Remarks</span></span>
-------

<span data-ttu-id="2a6e5-117">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="2a6e5-118">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="2a6e5-119">Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) .</span><span class="sxs-lookup"><span data-stu-id="2a6e5-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="2a6e5-120">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:</span><span class="sxs-lookup"><span data-stu-id="2a6e5-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="2a6e5-121">**Tabella \_ \_ \\ \\ \\ codici NLS del controllo CurrentControlSet \\ di HKEY Local Machine System \\**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-121">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="2a6e5-122">Tuttavia, è preferibile usare [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-122">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="2a6e5-123">Per determinare se una determinata tabella codici è valida, utilizzare la funzione [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) .</span><span class="sxs-lookup"><span data-stu-id="2a6e5-123">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="2a6e5-124">Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="2a6e5-124">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="2a6e5-125">Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](https://msdn.microsoft.com/library/windows/desktop/dd317756)delle tabelle codici.</span><span class="sxs-lookup"><span data-stu-id="2a6e5-125">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="2a6e5-126">Per determinare la tabella codici di input corrente di una console, usare la funzione [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="2a6e5-126">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="2a6e5-127">Per impostare e recuperare la tabella codici di output di una console, usare le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="2a6e5-127">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="2a6e5-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2a6e5-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2a6e5-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2a6e5-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2a6e5-130">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2a6e5-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2a6e5-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2a6e5-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2a6e5-132">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2a6e5-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2a6e5-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2a6e5-133">Header</span></span></p></td>
<td><span data-ttu-id="2a6e5-134">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2a6e5-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2a6e5-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="2a6e5-135">Library</span></span></p></td>
<td><span data-ttu-id="2a6e5-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2a6e5-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2a6e5-137">DLL</span><span class="sxs-lookup"><span data-stu-id="2a6e5-137">DLL</span></span></p></td>
<td><span data-ttu-id="2a6e5-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2a6e5-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2a6e5-139"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2a6e5-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2a6e5-140">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="2a6e5-140">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="2a6e5-141">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="2a6e5-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2a6e5-142">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-142">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="2a6e5-143">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-143">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="2a6e5-144">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2a6e5-144">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




