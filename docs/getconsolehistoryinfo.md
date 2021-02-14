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
ms.openlocfilehash: a26dbeb2a873bd780f91c240bf2658cde11b45ec
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359021"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="32219-104">GetConsoleHistoryInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="32219-104">GetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="32219-105">Recupera le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="32219-105">Retrieves the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="32219-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="32219-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="32219-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="32219-107">Parameters</span></span>

<span data-ttu-id="32219-108">*lpConsoleHistoryInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="32219-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="32219-109">Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che riceve le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="32219-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="32219-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="32219-110">Return value</span></span>

<span data-ttu-id="32219-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="32219-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="32219-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="32219-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="32219-113">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="32219-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="32219-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="32219-114">Remarks</span></span>

<span data-ttu-id="32219-115">Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo errore su **\_ accesso \_ negato**.</span><span class="sxs-lookup"><span data-stu-id="32219-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="32219-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="32219-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="32219-117">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="32219-117">Minimum supported client</span></span> | <span data-ttu-id="32219-118">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="32219-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="32219-119">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="32219-119">Minimum supported server</span></span> | <span data-ttu-id="32219-120">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="32219-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="32219-121">Intestazione</span><span class="sxs-lookup"><span data-stu-id="32219-121">Header</span></span> | <span data-ttu-id="32219-122">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="32219-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="32219-123">Libreria</span><span class="sxs-lookup"><span data-stu-id="32219-123">Library</span></span> | <span data-ttu-id="32219-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="32219-124">Kernel32.lib</span></span> |
| <span data-ttu-id="32219-125">DLL</span><span class="sxs-lookup"><span data-stu-id="32219-125">DLL</span></span> | <span data-ttu-id="32219-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="32219-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="32219-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="32219-127">See also</span></span>

[<span data-ttu-id="32219-128">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="32219-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="32219-129">**\_informazioni cronologia \_ console**</span><span class="sxs-lookup"><span data-stu-id="32219-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="32219-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="32219-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)