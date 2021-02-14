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
ms.openlocfilehash: abe04e2be5256097e19742bfbc8566c3ab613c4d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357521"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="6fb70-104">SetConsoleOutputCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="6fb70-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="6fb70-105">Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="6fb70-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="6fb70-106">Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="6fb70-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fb70-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6fb70-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="6fb70-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="6fb70-108">Parameters</span></span>

<span data-ttu-id="6fb70-109">*wCodePageID* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6fb70-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="6fb70-110">Identificatore della tabella codici da impostare.</span><span class="sxs-lookup"><span data-stu-id="6fb70-110">The identifier of the code page to set.</span></span> <span data-ttu-id="6fb70-111">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="6fb70-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="6fb70-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6fb70-112">Return value</span></span>

<span data-ttu-id="6fb70-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="6fb70-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6fb70-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="6fb70-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6fb70-115">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="6fb70-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6fb70-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6fb70-116">Remarks</span></span>

<span data-ttu-id="6fb70-117">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="6fb70-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="6fb70-118">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="6fb70-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="6fb70-119">Se il tipo di carattere corrente è un tipo di carattere Unicode a passo fisso, **SetConsoleOutputCP** modifica il mapping dei valori di carattere nel set di glifi del tipo di carattere, anziché caricare un tipo di carattere separato ogni volta che viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="6fb70-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="6fb70-120">Ciò influiscono sul modo in cui i caratteri estesi (valore ASCII maggiore di 127) vengono visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="6fb70-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="6fb70-121">Tuttavia, se il tipo di carattere corrente è un tipo di carattere raster, **SetConsoleOutputCP** non influisce sulla modalità di visualizzazione dei caratteri estesi.</span><span class="sxs-lookup"><span data-stu-id="6fb70-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="6fb70-122">Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) .</span><span class="sxs-lookup"><span data-stu-id="6fb70-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="6fb70-123">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:</span><span class="sxs-lookup"><span data-stu-id="6fb70-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="6fb70-124">Tuttavia, è preferibile usare [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="6fb70-124">However, it is better to use [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="6fb70-125">Per determinare se una determinata tabella codici è valida, utilizzare la funzione [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) .</span><span class="sxs-lookup"><span data-stu-id="6fb70-125">To determine whether a particular code page is valid, use the [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="6fb70-126">Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="6fb70-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="6fb70-127">Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](/windows/win32/intl/code-page-identifiers)delle tabelle codici.</span><span class="sxs-lookup"><span data-stu-id="6fb70-127">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="6fb70-128">Per determinare la tabella codici di output corrente di una console, usare la funzione [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="6fb70-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="6fb70-129">Per impostare e recuperare la tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="6fb70-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fb70-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6fb70-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6fb70-131">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6fb70-131">Minimum supported client</span></span> | <span data-ttu-id="6fb70-132">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="6fb70-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6fb70-133">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6fb70-133">Minimum supported server</span></span> | <span data-ttu-id="6fb70-134">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="6fb70-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6fb70-135">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6fb70-135">Header</span></span> | <span data-ttu-id="6fb70-136">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6fb70-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6fb70-137">Libreria</span><span class="sxs-lookup"><span data-stu-id="6fb70-137">Library</span></span> | <span data-ttu-id="6fb70-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6fb70-138">Kernel32.lib</span></span> |
| <span data-ttu-id="6fb70-139">DLL</span><span class="sxs-lookup"><span data-stu-id="6fb70-139">DLL</span></span> | <span data-ttu-id="6fb70-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6fb70-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6fb70-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6fb70-141">See also</span></span>

[<span data-ttu-id="6fb70-142">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="6fb70-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="6fb70-143">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="6fb70-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6fb70-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="6fb70-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="6fb70-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="6fb70-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="6fb70-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="6fb70-146">**SetConsoleCP**</span></span>](setconsolecp.md)