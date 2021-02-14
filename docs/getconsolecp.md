---
title: GetConsoleCP (funzione)
description: Recupera la tabella codici di input utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: fd581c1f11f457054257e1e36e55b726f48b34fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358461"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="528ff-104">GetConsoleCP (funzione)</span><span class="sxs-lookup"><span data-stu-id="528ff-104">GetConsoleCP function</span></span>

<span data-ttu-id="528ff-105">Recupera la tabella codici di input utilizzata dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="528ff-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="528ff-106">Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.</span><span class="sxs-lookup"><span data-stu-id="528ff-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="528ff-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="528ff-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a><span data-ttu-id="528ff-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="528ff-108">Parameters</span></span>

<span data-ttu-id="528ff-109">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="528ff-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="528ff-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="528ff-110">Return value</span></span>

<span data-ttu-id="528ff-111">Il valore restituito è un codice che identifica la tabella codici.</span><span class="sxs-lookup"><span data-stu-id="528ff-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="528ff-112">Per un elenco di identificatori, vedere [identificatori della tabella codici](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="528ff-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="528ff-113">Se il valore restituito è zero, la funzione ha avuto esito negativo.</span><span class="sxs-lookup"><span data-stu-id="528ff-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="528ff-114">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="528ff-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="528ff-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="528ff-115">Remarks</span></span>

<span data-ttu-id="528ff-116">Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="528ff-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="528ff-117">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="528ff-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="528ff-118">Per recuperare altre informazioni su una tabella codici, incluso il relativo nome, vedere la funzione [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="528ff-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="528ff-119">Per impostare la tabella codici di input di una console, usare la funzione [**SetConsoleCP**](setconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="528ff-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="528ff-120">Per impostare ed eseguire una query sulla tabella codici di output di una console, usare le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="528ff-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="528ff-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="528ff-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="528ff-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="528ff-122">Minimum supported client</span></span> | <span data-ttu-id="528ff-123">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="528ff-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="528ff-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="528ff-124">Minimum supported server</span></span> | <span data-ttu-id="528ff-125">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="528ff-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="528ff-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="528ff-126">Header</span></span> | <span data-ttu-id="528ff-127">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="528ff-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="528ff-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="528ff-128">Library</span></span> | <span data-ttu-id="528ff-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="528ff-129">Kernel32.lib</span></span> |
| <span data-ttu-id="528ff-130">DLL</span><span class="sxs-lookup"><span data-stu-id="528ff-130">DLL</span></span> | <span data-ttu-id="528ff-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="528ff-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="528ff-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="528ff-132">See also</span></span>

[<span data-ttu-id="528ff-133">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="528ff-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="528ff-134">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="528ff-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="528ff-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="528ff-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="528ff-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="528ff-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="528ff-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="528ff-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)