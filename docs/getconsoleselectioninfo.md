---
title: GetConsoleSelectionInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleSelectionInfo, che recupera le informazioni sulla selezione corrente della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e10bc2f2c82091311a2c050498748d4b43b1cd80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358931"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="e7bb5-104">GetConsoleSelectionInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="e7bb5-104">GetConsoleSelectionInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e7bb5-105">Recupera le informazioni sulla selezione corrente della console.</span><span class="sxs-lookup"><span data-stu-id="e7bb5-105">Retrieves information about the current console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7bb5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e7bb5-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

## <a name="parameters"></a><span data-ttu-id="e7bb5-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="e7bb5-107">Parameters</span></span>

<span data-ttu-id="e7bb5-108">*lpConsoleSelectionInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="e7bb5-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="e7bb5-109">Puntatore a una struttura [**di \_ \_ informazioni di selezione della console**](console-selection-info-str.md) che riceve le informazioni di selezione.</span><span class="sxs-lookup"><span data-stu-id="e7bb5-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7bb5-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e7bb5-110">Return value</span></span>

<span data-ttu-id="e7bb5-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e7bb5-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e7bb5-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e7bb5-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e7bb5-113">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="e7bb5-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e7bb5-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e7bb5-114">Remarks</span></span>

<span data-ttu-id="e7bb5-115">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="e7bb5-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="e7bb5-116">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="e7bb5-116">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="e7bb5-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e7bb5-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e7bb5-118">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e7bb5-118">Minimum supported client</span></span> | <span data-ttu-id="e7bb5-119">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="e7bb5-119">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="e7bb5-120">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e7bb5-120">Minimum supported server</span></span> | <span data-ttu-id="e7bb5-121">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="e7bb5-121">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e7bb5-122">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e7bb5-122">Header</span></span> | <span data-ttu-id="e7bb5-123">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e7bb5-123">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e7bb5-124">Libreria</span><span class="sxs-lookup"><span data-stu-id="e7bb5-124">Library</span></span> | <span data-ttu-id="e7bb5-125">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e7bb5-125">Kernel32.lib</span></span> |
| <span data-ttu-id="e7bb5-126">DLL</span><span class="sxs-lookup"><span data-stu-id="e7bb5-126">DLL</span></span> | <span data-ttu-id="e7bb5-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e7bb5-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e7bb5-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7bb5-128">See also</span></span>

[<span data-ttu-id="e7bb5-129">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="e7bb5-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e7bb5-130">Selezione nella console</span><span class="sxs-lookup"><span data-stu-id="e7bb5-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="e7bb5-131">**\_informazioni selezione \_ console**</span><span class="sxs-lookup"><span data-stu-id="e7bb5-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)