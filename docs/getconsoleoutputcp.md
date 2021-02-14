---
title: GetConsoleOutputCP (funzione)
description: Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358951"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="97c7d-104">GetConsoleOutputCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="97c7d-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="97c7d-105">Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="97c7d-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="97c7d-106">Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="97c7d-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="97c7d-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="97c7d-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="97c7d-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="97c7d-108">Parameters</span></span>

<span data-ttu-id="97c7d-109">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="97c7d-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="97c7d-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="97c7d-110">Return value</span></span>

<span data-ttu-id="97c7d-111">Il valore restituito è un codice che identifica la tabella codici.</span><span class="sxs-lookup"><span data-stu-id="97c7d-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="97c7d-112">Per un elenco di identificatori, vedere [identificatori della tabella codici](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="97c7d-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="97c7d-113">Se il valore restituito è zero, la funzione ha avuto esito negativo.</span><span class="sxs-lookup"><span data-stu-id="97c7d-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="97c7d-114">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="97c7d-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="97c7d-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="97c7d-115">Remarks</span></span>

<span data-ttu-id="97c7d-116">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="97c7d-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="97c7d-117">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="97c7d-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="97c7d-118">Per recuperare altre informazioni su una tabella codici, incluso il relativo nome, vedere la funzione [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="97c7d-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="97c7d-119">Per impostare la tabella codici di output di una console, usare la funzione [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="97c7d-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="97c7d-120">Per impostare ed eseguire una query sulla tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="97c7d-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="97c7d-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="97c7d-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="97c7d-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="97c7d-122">Minimum supported client</span></span> | <span data-ttu-id="97c7d-123">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="97c7d-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="97c7d-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="97c7d-124">Minimum supported server</span></span> | <span data-ttu-id="97c7d-125">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="97c7d-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="97c7d-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="97c7d-126">Header</span></span> | <span data-ttu-id="97c7d-127">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="97c7d-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="97c7d-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="97c7d-128">Library</span></span> | <span data-ttu-id="97c7d-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="97c7d-129">Kernel32.lib</span></span> |
| <span data-ttu-id="97c7d-130">DLL</span><span class="sxs-lookup"><span data-stu-id="97c7d-130">DLL</span></span> | <span data-ttu-id="97c7d-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="97c7d-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="97c7d-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="97c7d-132">See also</span></span>

[<span data-ttu-id="97c7d-133">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="97c7d-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="97c7d-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="97c7d-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="97c7d-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="97c7d-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="97c7d-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="97c7d-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="97c7d-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="97c7d-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)