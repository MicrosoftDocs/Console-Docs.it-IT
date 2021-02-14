---
title: GetCurrentConsoleFont (funzione)
description: Recupera le informazioni sul tipo di carattere della console corrente per un buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 93f22e1b1d1fa6d60e5d97b7650809d19e01f03c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357261"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="9425b-104">GetCurrentConsoleFont (funzione)</span><span class="sxs-lookup"><span data-stu-id="9425b-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9425b-105">Recupera le informazioni sul tipo di carattere della console corrente.</span><span class="sxs-lookup"><span data-stu-id="9425b-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="9425b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9425b-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="9425b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="9425b-107">Parameters</span></span>

<span data-ttu-id="9425b-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9425b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9425b-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9425b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9425b-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="9425b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9425b-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9425b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9425b-112">*bMaximumWindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9425b-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="9425b-113">Se questo parametro è **true**, vengono recuperate le informazioni relative al tipo di carattere per la dimensione massima della finestra.</span><span class="sxs-lookup"><span data-stu-id="9425b-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="9425b-114">Se questo parametro è **false**, vengono recuperate le informazioni relative al tipo di carattere per le dimensioni correnti della finestra.</span><span class="sxs-lookup"><span data-stu-id="9425b-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="9425b-115">*lpConsoleCurrentFont* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="9425b-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="9425b-116">Puntatore a una struttura [**di \_ \_ informazioni sul tipo di carattere della console**](console-font-info-str.md) che riceve le informazioni sul tipo di carattere richieste.</span><span class="sxs-lookup"><span data-stu-id="9425b-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="9425b-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9425b-117">Return value</span></span>

<span data-ttu-id="9425b-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="9425b-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9425b-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="9425b-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9425b-120">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="9425b-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="9425b-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9425b-121">Remarks</span></span>

<span data-ttu-id="9425b-122">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="9425b-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="9425b-123">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="9425b-123">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="9425b-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9425b-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9425b-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9425b-125">Minimum supported client</span></span> | <span data-ttu-id="9425b-126">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="9425b-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="9425b-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9425b-127">Minimum supported server</span></span> | <span data-ttu-id="9425b-128">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="9425b-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="9425b-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="9425b-129">Header</span></span> | <span data-ttu-id="9425b-130">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9425b-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9425b-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="9425b-131">Library</span></span> | <span data-ttu-id="9425b-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="9425b-132">Kernel32.lib</span></span> |
| <span data-ttu-id="9425b-133">DLL</span><span class="sxs-lookup"><span data-stu-id="9425b-133">DLL</span></span> | <span data-ttu-id="9425b-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9425b-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9425b-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9425b-135">See also</span></span>

[<span data-ttu-id="9425b-136">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="9425b-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9425b-137">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="9425b-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="9425b-138">**informazioni sul tipo di carattere della CONSOLE \_ \_**</span><span class="sxs-lookup"><span data-stu-id="9425b-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="9425b-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="9425b-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)