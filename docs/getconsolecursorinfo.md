---
title: GetConsoleCursorInfo (funzione)
description: Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d87fe0828451615e837c1c6c809a0160f15cf018
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059793"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="fbc0e-104">GetConsoleCursorInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="fbc0e-104">GetConsoleCursorInfo function</span></span>


<span data-ttu-id="fbc0e-105">Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="fbc0e-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="fbc0e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fbc0e-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="fbc0e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="fbc0e-107">Parameters</span></span>
----------

<span data-ttu-id="fbc0e-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="fbc0e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="fbc0e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="fbc0e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="fbc0e-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="fbc0e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="fbc0e-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="fbc0e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="fbc0e-112">*lpConsoleCursorInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="fbc0e-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="fbc0e-113">Puntatore a una struttura [**di \_ \_ informazioni del cursore della console**](console-cursor-info-str.md) che riceve informazioni sul cursore della console.</span><span class="sxs-lookup"><span data-stu-id="fbc0e-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="fbc0e-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="fbc0e-114">Return value</span></span>
------------

<span data-ttu-id="fbc0e-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="fbc0e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fbc0e-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="fbc0e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fbc0e-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fbc0e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="fbc0e-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fbc0e-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="fbc0e-119">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fbc0e-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="fbc0e-120">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="fbc0e-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fbc0e-121">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="fbc0e-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="fbc0e-122">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="fbc0e-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fbc0e-123">Intestazione</span><span class="sxs-lookup"><span data-stu-id="fbc0e-123">Header</span></span></p></td>
<td><span data-ttu-id="fbc0e-124">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fbc0e-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fbc0e-125">Libreria</span><span class="sxs-lookup"><span data-stu-id="fbc0e-125">Library</span></span></p></td>
<td><span data-ttu-id="fbc0e-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fbc0e-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fbc0e-127">DLL</span><span class="sxs-lookup"><span data-stu-id="fbc0e-127">DLL</span></span></p></td>
<td><span data-ttu-id="fbc0e-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fbc0e-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="fbc0e-129"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fbc0e-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="fbc0e-130">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="fbc0e-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fbc0e-131">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="fbc0e-131">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="fbc0e-132">**\_informazioni cursore \_ console**</span><span class="sxs-lookup"><span data-stu-id="fbc0e-132">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="fbc0e-133">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="fbc0e-133">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




