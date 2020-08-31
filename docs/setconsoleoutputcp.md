---
title: SetConsoleOutputCP (funzione)
description: Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060501"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="84778-104">SetConsoleOutputCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="84778-104">SetConsoleOutputCP function</span></span>


<span data-ttu-id="84778-105">Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="84778-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="84778-106">Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="84778-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="84778-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="84778-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="84778-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="84778-108">Parameters</span></span>
----------

<span data-ttu-id="84778-109">*wCodePageID* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="84778-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="84778-110">Identificatore della tabella codici da impostare.</span><span class="sxs-lookup"><span data-stu-id="84778-110">The identifier of the code page to set.</span></span> <span data-ttu-id="84778-111">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="84778-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="84778-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="84778-112">Return value</span></span>
------------

<span data-ttu-id="84778-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="84778-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="84778-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="84778-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="84778-115">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="84778-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="84778-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="84778-116">Remarks</span></span>
-------

<span data-ttu-id="84778-117">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="84778-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="84778-118">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="84778-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="84778-119">Se il tipo di carattere corrente è un tipo di carattere Unicode a passo fisso, **SetConsoleOutputCP** modifica il mapping dei valori di carattere nel set di glifi del tipo di carattere, anziché caricare un tipo di carattere separato ogni volta che viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="84778-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="84778-120">Ciò influiscono sul modo in cui i caratteri estesi (valore ASCII maggiore di 127) vengono visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="84778-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="84778-121">Tuttavia, se il tipo di carattere corrente è un tipo di carattere raster, **SetConsoleOutputCP** non influisce sulla modalità di visualizzazione dei caratteri estesi.</span><span class="sxs-lookup"><span data-stu-id="84778-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="84778-122">Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) .</span><span class="sxs-lookup"><span data-stu-id="84778-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="84778-123">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:</span><span class="sxs-lookup"><span data-stu-id="84778-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="84778-124">**Tabella \_ \_ \\ \\ \\ codici NLS del controllo CurrentControlSet \\ di HKEY Local Machine System \\**</span><span class="sxs-lookup"><span data-stu-id="84778-124">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="84778-125">Tuttavia, è preferibile usare [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="84778-125">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="84778-126">Per determinare se una determinata tabella codici è valida, utilizzare la funzione [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) .</span><span class="sxs-lookup"><span data-stu-id="84778-126">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="84778-127">Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="84778-127">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="84778-128">Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](https://msdn.microsoft.com/library/windows/desktop/dd317756)delle tabelle codici.</span><span class="sxs-lookup"><span data-stu-id="84778-128">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="84778-129">Per determinare la tabella codici di output corrente di una console, usare la funzione [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="84778-129">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="84778-130">Per impostare e recuperare la tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="84778-130">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="84778-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="84778-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="84778-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="84778-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="84778-133">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="84778-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="84778-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="84778-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="84778-135">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="84778-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="84778-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="84778-136">Header</span></span></p></td>
<td><span data-ttu-id="84778-137">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="84778-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="84778-138">Libreria</span><span class="sxs-lookup"><span data-stu-id="84778-138">Library</span></span></p></td>
<td><span data-ttu-id="84778-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="84778-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="84778-140">DLL</span><span class="sxs-lookup"><span data-stu-id="84778-140">DLL</span></span></p></td>
<td><span data-ttu-id="84778-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="84778-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="84778-142"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="84778-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="84778-143">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="84778-143">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="84778-144">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="84778-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="84778-145">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="84778-145">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="84778-146">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="84778-146">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="84778-147">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="84778-147">**SetConsoleCP**</span></span>](setconsolecp.md)

 

 




