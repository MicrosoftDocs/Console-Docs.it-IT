---
title: SetCurrentConsoleFontEx (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetCurrentConsoleFontEx, che imposta le informazioni estese sul tipo di carattere della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1ba89b90a0362261aafbe5ac6462224b3c0172dc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037054"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="d9460-104">SetCurrentConsoleFontEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="d9460-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d9460-105">Imposta le informazioni estese sul tipo di carattere della console corrente.</span><span class="sxs-lookup"><span data-stu-id="d9460-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9460-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d9460-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="d9460-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d9460-107">Parameters</span></span>

<span data-ttu-id="d9460-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d9460-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d9460-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="d9460-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d9460-110">L'handle deve avere il diritto di accesso in **\_ scrittura generico** .</span><span class="sxs-lookup"><span data-stu-id="d9460-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d9460-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d9460-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d9460-112">*bMaximumWindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d9460-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="d9460-113">Se questo parametro è **true** , le informazioni sul tipo di carattere sono impostate per la dimensione massima della finestra.</span><span class="sxs-lookup"><span data-stu-id="d9460-113">If this parameter is **TRUE** , font information is set for the maximum window size.</span></span> <span data-ttu-id="d9460-114">Se questo parametro è **false** , le informazioni sul tipo di carattere vengono impostate per le dimensioni correnti della finestra.</span><span class="sxs-lookup"><span data-stu-id="d9460-114">If this parameter is **FALSE** , font information is set for the current window size.</span></span>

<span data-ttu-id="d9460-115">*lpConsoleCurrentFontEx* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d9460-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="d9460-116">Puntatore a una struttura [**\_ \_ INFOEX del tipo di carattere della console**](console-font-infoex.md) che contiene le informazioni sul tipo di carattere.</span><span class="sxs-lookup"><span data-stu-id="d9460-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9460-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d9460-117">Return value</span></span>

<span data-ttu-id="d9460-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="d9460-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d9460-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="d9460-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d9460-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d9460-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="d9460-121">Commenti</span><span class="sxs-lookup"><span data-stu-id="d9460-121">Remarks</span></span>

<span data-ttu-id="d9460-122">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="d9460-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="d9460-123">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="d9460-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="d9460-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d9460-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d9460-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d9460-125">Minimum supported client</span></span> | <span data-ttu-id="d9460-126">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="d9460-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="d9460-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="d9460-127">Minimum supported server</span></span> | <span data-ttu-id="d9460-128">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="d9460-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="d9460-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="d9460-129">Header</span></span> | <span data-ttu-id="d9460-130">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d9460-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d9460-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="d9460-131">Library</span></span> | <span data-ttu-id="d9460-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d9460-132">Kernel32.lib</span></span> |
| <span data-ttu-id="d9460-133">DLL</span><span class="sxs-lookup"><span data-stu-id="d9460-133">DLL</span></span> | <span data-ttu-id="d9460-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d9460-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d9460-135">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d9460-135">See also</span></span>

[<span data-ttu-id="d9460-136">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="d9460-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d9460-137">**\_INFOEX carattere \_ console**</span><span class="sxs-lookup"><span data-stu-id="d9460-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)
