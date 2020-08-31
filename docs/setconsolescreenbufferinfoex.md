---
title: SetConsoleScreenBufferInfoEx (funzione)
description: Imposta le informazioni estese sul buffer dello schermo della console specificato sul buffer specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 403ce6c3625aacdcc8b2eb498e7df1715d1e6b94
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060495"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="0854b-104">SetConsoleScreenBufferInfoEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="0854b-104">SetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="0854b-105">Imposta le informazioni estese sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="0854b-105">Sets extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="0854b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0854b-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="0854b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="0854b-107">Parameters</span></span>
----------

<span data-ttu-id="0854b-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0854b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0854b-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="0854b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0854b-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="0854b-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="0854b-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0854b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0854b-112">*lpConsoleScreenBufferInfoEx* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0854b-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="0854b-113">Struttura [\*\* \_ \_ \_ INFOEX buffer dello schermo\*\*](console-screen-buffer-infoex.md) della console che contiene le informazioni sul buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="0854b-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="0854b-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0854b-114">Return value</span></span>
------------

<span data-ttu-id="0854b-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="0854b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0854b-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="0854b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0854b-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0854b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="0854b-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0854b-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0854b-119">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0854b-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0854b-120">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0854b-120">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0854b-121">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0854b-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0854b-122">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0854b-122">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0854b-123">Intestazione</span><span class="sxs-lookup"><span data-stu-id="0854b-123">Header</span></span></p></td>
<td><span data-ttu-id="0854b-124">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0854b-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0854b-125">Libreria</span><span class="sxs-lookup"><span data-stu-id="0854b-125">Library</span></span></p></td>
<td><span data-ttu-id="0854b-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0854b-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0854b-127">DLL</span><span class="sxs-lookup"><span data-stu-id="0854b-127">DLL</span></span></p></td>
<td><span data-ttu-id="0854b-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0854b-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0854b-129"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0854b-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0854b-130">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="0854b-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0854b-131">**\_INFOEX buffer dello schermo della console \_ \_**</span><span class="sxs-lookup"><span data-stu-id="0854b-131">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="0854b-132">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="0854b-132">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

 

 




