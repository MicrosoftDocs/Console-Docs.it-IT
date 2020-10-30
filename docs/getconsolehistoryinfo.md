---
title: GetConsoleHistoryInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleHistoryInfo, che recupera le impostazioni della cronologia per la console del processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038029"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="e3278-104">GetConsoleHistoryInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="e3278-104">GetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e3278-105">Recupera le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="e3278-105">Retrieves the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3278-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e3278-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="e3278-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="e3278-107">Parameters</span></span>

<span data-ttu-id="e3278-108">*lpConsoleHistoryInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="e3278-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="e3278-109">Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che riceve le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="e3278-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3278-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e3278-110">Return value</span></span>

<span data-ttu-id="e3278-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e3278-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="e3278-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e3278-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e3278-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e3278-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e3278-114">Commenti</span><span class="sxs-lookup"><span data-stu-id="e3278-114">Remarks</span></span>

<span data-ttu-id="e3278-115">Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo errore su **\_ accesso \_ negato** .</span><span class="sxs-lookup"><span data-stu-id="e3278-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED** .</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="e3278-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e3278-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e3278-117">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e3278-117">Minimum supported client</span></span> | <span data-ttu-id="e3278-118">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="e3278-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3278-119">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e3278-119">Minimum supported server</span></span> | <span data-ttu-id="e3278-120">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="e3278-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3278-121">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e3278-121">Header</span></span> | <span data-ttu-id="e3278-122">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e3278-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e3278-123">Libreria</span><span class="sxs-lookup"><span data-stu-id="e3278-123">Library</span></span> | <span data-ttu-id="e3278-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e3278-124">Kernel32.lib</span></span> |
| <span data-ttu-id="e3278-125">DLL</span><span class="sxs-lookup"><span data-stu-id="e3278-125">DLL</span></span> | <span data-ttu-id="e3278-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e3278-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3278-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e3278-127">See also</span></span>

[<span data-ttu-id="e3278-128">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="e3278-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e3278-129">**\_informazioni cronologia \_ console**</span><span class="sxs-lookup"><span data-stu-id="e3278-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="e3278-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="e3278-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
