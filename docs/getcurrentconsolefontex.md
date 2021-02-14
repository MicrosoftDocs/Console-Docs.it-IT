---
title: GetCurrentConsoleFontEx (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetCurrentConsoleFontEx, che recupera le informazioni estese sul tipo di carattere della console attualmente utilizzato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e7932d286723886f671be051294fcffb23155bf6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358881"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="c311b-104">GetCurrentConsoleFontEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="c311b-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c311b-105">Recupera le informazioni estese sul tipo di carattere della console corrente.</span><span class="sxs-lookup"><span data-stu-id="c311b-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="c311b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c311b-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="c311b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c311b-107">Parameters</span></span>

<span data-ttu-id="c311b-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c311b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c311b-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="c311b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c311b-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="c311b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c311b-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="c311b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c311b-112">*bMaximumWindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c311b-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="c311b-113">Se questo parametro è **true**, vengono recuperate le informazioni relative al tipo di carattere per la dimensione massima della finestra.</span><span class="sxs-lookup"><span data-stu-id="c311b-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="c311b-114">Se questo parametro è **false**, vengono recuperate le informazioni relative al tipo di carattere per le dimensioni correnti della finestra.</span><span class="sxs-lookup"><span data-stu-id="c311b-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="c311b-115">*lpConsoleCurrentFontEx* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="c311b-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="c311b-116">Puntatore a una struttura [**\_ \_ INFOEX del tipo di carattere della console**](console-font-infoex.md) che riceve le informazioni sul tipo di carattere richieste.</span><span class="sxs-lookup"><span data-stu-id="c311b-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="c311b-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c311b-117">Return value</span></span>

<span data-ttu-id="c311b-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="c311b-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c311b-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="c311b-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c311b-120">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c311b-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="c311b-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c311b-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c311b-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c311b-122">Minimum supported client</span></span> | <span data-ttu-id="c311b-123">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="c311b-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="c311b-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c311b-124">Minimum supported server</span></span> | <span data-ttu-id="c311b-125">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="c311b-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c311b-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c311b-126">Header</span></span> | <span data-ttu-id="c311b-127">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c311b-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c311b-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="c311b-128">Library</span></span> | <span data-ttu-id="c311b-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c311b-129">Kernel32.lib</span></span> |
| <span data-ttu-id="c311b-130">DLL</span><span class="sxs-lookup"><span data-stu-id="c311b-130">DLL</span></span> | <span data-ttu-id="c311b-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c311b-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c311b-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c311b-132">See also</span></span>

[<span data-ttu-id="c311b-133">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="c311b-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c311b-134">**\_INFOEX carattere \_ console**</span><span class="sxs-lookup"><span data-stu-id="c311b-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)