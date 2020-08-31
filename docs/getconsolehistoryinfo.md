---
title: GetConsoleHistoryInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleHistoryInfo, che recupera le impostazioni della cronologia per la console del processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: 176cf5517f18f022f00824de02872adcb916f231
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059745"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="86954-104">GetConsoleHistoryInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="86954-104">GetConsoleHistoryInfo function</span></span>


<span data-ttu-id="86954-105">Recupera le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="86954-105">Retrieves the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="86954-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="86954-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="86954-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="86954-107">Parameters</span></span>
----------

<span data-ttu-id="86954-108">*lpConsoleHistoryInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="86954-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="86954-109">Puntatore a una struttura [**di \_ \_ informazioni della cronologia della console**](console-history-info.md) che riceve le impostazioni della cronologia per la console del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="86954-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="86954-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="86954-110">Return value</span></span>
------------

<span data-ttu-id="86954-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="86954-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="86954-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="86954-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="86954-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="86954-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="86954-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="86954-114">Remarks</span></span>
-------

<span data-ttu-id="86954-115">Se il processo chiamante non è un processo console, la funzione ha esito negativo e imposta l'ultimo errore su \*\* \_ accesso \_ negato\*\*.</span><span class="sxs-lookup"><span data-stu-id="86954-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="86954-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="86954-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="86954-117">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="86954-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="86954-118">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="86954-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="86954-119">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="86954-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="86954-120">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="86954-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="86954-121">Intestazione</span><span class="sxs-lookup"><span data-stu-id="86954-121">Header</span></span></p></td>
<td><span data-ttu-id="86954-122">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="86954-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="86954-123">Libreria</span><span class="sxs-lookup"><span data-stu-id="86954-123">Library</span></span></p></td>
<td><span data-ttu-id="86954-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="86954-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="86954-125">DLL</span><span class="sxs-lookup"><span data-stu-id="86954-125">DLL</span></span></p></td>
<td><span data-ttu-id="86954-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="86954-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="86954-127"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="86954-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="86954-128">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="86954-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="86954-129">**\_informazioni cronologia \_ console**</span><span class="sxs-lookup"><span data-stu-id="86954-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="86954-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="86954-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




