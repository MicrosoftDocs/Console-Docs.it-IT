---
title: SetConsoleHistoryInfo (funzione)
description: Imposta le impostazioni della cronologia per la console di Windows del processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 618661b8c59506e2ba5e1f2b2b283ccf823b831a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039379"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="4dfc3-104">SetConsoleHistoryInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="4dfc3-104">SetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4dfc3-105">Imposta le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="4dfc3-105">Sets the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="4dfc3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4dfc3-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="4dfc3-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4dfc3-107">Parameters</span></span>

<span data-ttu-id="4dfc3-108">*lpConsoleHistoryInfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4dfc3-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="4dfc3-109">Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che contiene le impostazioni di cronologia per la console del processo.</span><span class="sxs-lookup"><span data-stu-id="4dfc3-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="4dfc3-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4dfc3-110">Return value</span></span>

<span data-ttu-id="4dfc3-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="4dfc3-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4dfc3-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="4dfc3-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4dfc3-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4dfc3-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4dfc3-114">Commenti</span><span class="sxs-lookup"><span data-stu-id="4dfc3-114">Remarks</span></span>

<span data-ttu-id="4dfc3-115">Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo codice di errore su **\_ accesso \_ negato** .</span><span class="sxs-lookup"><span data-stu-id="4dfc3-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED** .</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="4dfc3-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4dfc3-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4dfc3-117">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4dfc3-117">Minimum supported client</span></span> | <span data-ttu-id="4dfc3-118">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="4dfc3-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="4dfc3-119">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4dfc3-119">Minimum supported server</span></span> | <span data-ttu-id="4dfc3-120">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="4dfc3-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="4dfc3-121">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4dfc3-121">Header</span></span> | <span data-ttu-id="4dfc3-122">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4dfc3-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4dfc3-123">Libreria</span><span class="sxs-lookup"><span data-stu-id="4dfc3-123">Library</span></span> | <span data-ttu-id="4dfc3-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4dfc3-124">Kernel32.lib</span></span> |
| <span data-ttu-id="4dfc3-125">DLL</span><span class="sxs-lookup"><span data-stu-id="4dfc3-125">DLL</span></span> | <span data-ttu-id="4dfc3-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4dfc3-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4dfc3-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4dfc3-127">See also</span></span>

[<span data-ttu-id="4dfc3-128">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="4dfc3-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4dfc3-129">**\_informazioni cronologia \_ console**</span><span class="sxs-lookup"><span data-stu-id="4dfc3-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="4dfc3-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="4dfc3-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)
