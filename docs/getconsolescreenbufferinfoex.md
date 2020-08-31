---
title: GetConsoleScreenBufferInfoEx (funzione)
description: Recupera le informazioni estese sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059748"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="8db3e-104">GetConsoleScreenBufferInfoEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="8db3e-104">GetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="8db3e-105">Recupera le informazioni estese sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="8db3e-105">Retrieves extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="8db3e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8db3e-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="8db3e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8db3e-107">Parameters</span></span>
----------

<span data-ttu-id="8db3e-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8db3e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8db3e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8db3e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="8db3e-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="8db3e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="8db3e-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="8db3e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8db3e-112">*lpConsoleScreenBufferInfoEx* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8db3e-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="8db3e-113">Struttura [\*\* \_ INFOEX del \_ buffer \_ dello schermo della console\*\*](console-screen-buffer-infoex.md) che riceve le informazioni sul buffer dello schermo della console richieste.</span><span class="sxs-lookup"><span data-stu-id="8db3e-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="8db3e-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8db3e-114">Return value</span></span>
------------

<span data-ttu-id="8db3e-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="8db3e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8db3e-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="8db3e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8db3e-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="8db3e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="8db3e-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8db3e-118">Remarks</span></span>
-------

<span data-ttu-id="8db3e-119">Il rettangolo restituito nel membro **srWindow** della struttura [**INFOEX del \_ \_ buffer dello \_ schermo della console**](console-screen-buffer-infoex.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.</span><span class="sxs-lookup"><span data-stu-id="8db3e-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="8db3e-120">Tutte le coordinate restituite nella struttura [\*\* \_ \_ \_ INFOEX buffer dello schermo della console\*\*](console-screen-buffer-infoex.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8db3e-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="requirements"></a><span data-ttu-id="8db3e-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8db3e-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8db3e-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8db3e-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8db3e-123">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8db3e-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8db3e-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8db3e-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8db3e-125">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8db3e-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8db3e-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8db3e-126">Header</span></span></p></td>
<td><span data-ttu-id="8db3e-127">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8db3e-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8db3e-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="8db3e-128">Library</span></span></p></td>
<td><span data-ttu-id="8db3e-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8db3e-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8db3e-130">DLL</span><span class="sxs-lookup"><span data-stu-id="8db3e-130">DLL</span></span></p></td>
<td><span data-ttu-id="8db3e-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8db3e-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8db3e-132"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8db3e-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8db3e-133">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="8db3e-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8db3e-134">**\_INFOEX buffer dello schermo della console \_ \_**</span><span class="sxs-lookup"><span data-stu-id="8db3e-134">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="8db3e-135">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="8db3e-135">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

 

 




