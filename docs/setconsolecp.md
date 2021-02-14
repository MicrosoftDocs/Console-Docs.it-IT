---
title: SetConsoleCP (funzione)
description: Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 040a97360f455fec2ebd043de21e390959f1db0a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357721"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="2ea70-104">SetConsoleCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="2ea70-104">SetConsoleCP function</span></span>

<span data-ttu-id="2ea70-105">Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="2ea70-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="2ea70-106">Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.</span><span class="sxs-lookup"><span data-stu-id="2ea70-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ea70-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2ea70-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="2ea70-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="2ea70-108">Parameters</span></span>

<span data-ttu-id="2ea70-109">*wCodePageID* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2ea70-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="2ea70-110">Identificatore della tabella codici da impostare.</span><span class="sxs-lookup"><span data-stu-id="2ea70-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="2ea70-111">Per altre informazioni, vedere la sezione Osservazioni.</span><span class="sxs-lookup"><span data-stu-id="2ea70-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ea70-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2ea70-112">Return value</span></span>

<span data-ttu-id="2ea70-113">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2ea70-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2ea70-114">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2ea70-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2ea70-115">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="2ea70-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="2ea70-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2ea70-116">Remarks</span></span>

<span data-ttu-id="2ea70-117">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="2ea70-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="2ea70-118">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="2ea70-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="2ea70-119">Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) .</span><span class="sxs-lookup"><span data-stu-id="2ea70-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="2ea70-120">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:</span><span class="sxs-lookup"><span data-stu-id="2ea70-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="2ea70-121">Tuttavia, è preferibile usare [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="2ea70-121">However, it is better to use [**EnumSystemCodePages**](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="2ea70-122">Per determinare se una determinata tabella codici è valida, utilizzare la funzione [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) .</span><span class="sxs-lookup"><span data-stu-id="2ea70-122">To determine whether a particular code page is valid, use the [**IsValidCodePage**](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="2ea70-123">Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="2ea70-123">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="2ea70-124">Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](/windows/win32/intl/code-page-identifiers)delle tabelle codici.</span><span class="sxs-lookup"><span data-stu-id="2ea70-124">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="2ea70-125">Per determinare la tabella codici di input corrente di una console, usare la funzione [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="2ea70-125">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="2ea70-126">Per impostare e recuperare la tabella codici di output di una console, usare le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="2ea70-126">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ea70-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2ea70-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2ea70-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2ea70-128">Minimum supported client</span></span> | <span data-ttu-id="2ea70-129">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="2ea70-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ea70-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2ea70-130">Minimum supported server</span></span> | <span data-ttu-id="2ea70-131">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="2ea70-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2ea70-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2ea70-132">Header</span></span> | <span data-ttu-id="2ea70-133">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2ea70-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2ea70-134">Libreria</span><span class="sxs-lookup"><span data-stu-id="2ea70-134">Library</span></span> | <span data-ttu-id="2ea70-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="2ea70-135">Kernel32.lib</span></span> |
| <span data-ttu-id="2ea70-136">DLL</span><span class="sxs-lookup"><span data-stu-id="2ea70-136">DLL</span></span> | <span data-ttu-id="2ea70-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2ea70-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="2ea70-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2ea70-138">See also</span></span>

[<span data-ttu-id="2ea70-139">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="2ea70-139">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="2ea70-140">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="2ea70-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2ea70-141">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="2ea70-141">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="2ea70-142">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2ea70-142">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="2ea70-143">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="2ea70-143">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)