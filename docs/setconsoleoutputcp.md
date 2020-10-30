---
title: SetConsoleOutputCP (funzione)
description: Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 85b6ba4d829b86b99138efbdaa14284429d2aa81
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039339"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="7d338-104">SetConsoleOutputCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="7d338-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="7d338-105">Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="7d338-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="7d338-106">Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="7d338-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d338-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7d338-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="7d338-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="7d338-108">Parameters</span></span>

<span data-ttu-id="7d338-109">*wCodePageID* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="7d338-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="7d338-110">Identificatore della tabella codici da impostare.</span><span class="sxs-lookup"><span data-stu-id="7d338-110">The identifier of the code page to set.</span></span> <span data-ttu-id="7d338-111">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="7d338-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="7d338-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="7d338-112">Return value</span></span>

<span data-ttu-id="7d338-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="7d338-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7d338-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="7d338-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7d338-115">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7d338-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="7d338-116">Commenti</span><span class="sxs-lookup"><span data-stu-id="7d338-116">Remarks</span></span>

<span data-ttu-id="7d338-117">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="7d338-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="7d338-118">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="7d338-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="7d338-119">Se il tipo di carattere corrente è un tipo di carattere Unicode a passo fisso, **SetConsoleOutputCP** modifica il mapping dei valori di carattere nel set di glifi del tipo di carattere, anziché caricare un tipo di carattere separato ogni volta che viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="7d338-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="7d338-120">Ciò influiscono sul modo in cui i caratteri estesi (valore ASCII maggiore di 127) vengono visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="7d338-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="7d338-121">Tuttavia, se il tipo di carattere corrente è un tipo di carattere raster, **SetConsoleOutputCP** non influisce sulla modalità di visualizzazione dei caratteri estesi.</span><span class="sxs-lookup"><span data-stu-id="7d338-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="7d338-122">Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) .</span><span class="sxs-lookup"><span data-stu-id="7d338-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="7d338-123">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:</span><span class="sxs-lookup"><span data-stu-id="7d338-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="7d338-124">Tuttavia, è preferibile usare [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="7d338-124">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="7d338-125">Per determinare se una determinata tabella codici è valida, utilizzare la funzione [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) .</span><span class="sxs-lookup"><span data-stu-id="7d338-125">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="7d338-126">Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="7d338-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="7d338-127">Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](https://msdn.microsoft.com/library/windows/desktop/dd317756)delle tabelle codici.</span><span class="sxs-lookup"><span data-stu-id="7d338-127">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="7d338-128">Per determinare la tabella codici di output corrente di una console, usare la funzione [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="7d338-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="7d338-129">Per impostare e recuperare la tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="7d338-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d338-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7d338-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7d338-131">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7d338-131">Minimum supported client</span></span> | <span data-ttu-id="7d338-132">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="7d338-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7d338-133">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7d338-133">Minimum supported server</span></span> | <span data-ttu-id="7d338-134">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="7d338-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7d338-135">Intestazione</span><span class="sxs-lookup"><span data-stu-id="7d338-135">Header</span></span> | <span data-ttu-id="7d338-136">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7d338-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7d338-137">Libreria</span><span class="sxs-lookup"><span data-stu-id="7d338-137">Library</span></span> | <span data-ttu-id="7d338-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7d338-138">Kernel32.lib</span></span> |
| <span data-ttu-id="7d338-139">DLL</span><span class="sxs-lookup"><span data-stu-id="7d338-139">DLL</span></span> | <span data-ttu-id="7d338-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7d338-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7d338-141">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="7d338-141">See also</span></span>

[<span data-ttu-id="7d338-142">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="7d338-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="7d338-143">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="7d338-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7d338-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7d338-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="7d338-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="7d338-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="7d338-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7d338-146">**SetConsoleCP**</span></span>](setconsolecp.md)
