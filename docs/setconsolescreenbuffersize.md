---
title: SetConsoleScreenBufferSize (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleScreenBufferSize, che modifica la dimensione del buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e2f3a3ea11f291e88837885c6fc3e555fd39e09
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060510"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="96d6d-104">SetConsoleScreenBufferSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="96d6d-104">SetConsoleScreenBufferSize function</span></span>


<span data-ttu-id="96d6d-105">Modifica la dimensione del buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="96d6d-105">Changes the size of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="96d6d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="96d6d-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

<a name="parameters"></a><span data-ttu-id="96d6d-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="96d6d-107">Parameters</span></span>
----------

<span data-ttu-id="96d6d-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="96d6d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="96d6d-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="96d6d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="96d6d-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="96d6d-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="96d6d-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="96d6d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="96d6d-112">*dwSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="96d6d-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="96d6d-113">Struttura [**Coord**](coord-str.md) che specifica la nuova dimensione del buffer dello schermo della console, in righe e colonne di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="96d6d-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="96d6d-114">La larghezza e l'altezza specificate non possono essere minori della larghezza e dell'altezza della finestra del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="96d6d-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="96d6d-115">Anche le dimensioni specificate non possono essere inferiori alle dimensioni minime consentite dal sistema.</span><span class="sxs-lookup"><span data-stu-id="96d6d-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="96d6d-116">Questo valore minimo dipende dalle dimensioni correnti del carattere per la console (selezionate dall'utente) e dai valori \*\* \_ CYMIN\*\* **SM \_ CXMIN** e SM restituiti dalla funzione [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="96d6d-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

<a name="return-value"></a><span data-ttu-id="96d6d-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="96d6d-117">Return value</span></span>
------------

<span data-ttu-id="96d6d-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="96d6d-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="96d6d-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="96d6d-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="96d6d-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="96d6d-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="96d6d-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="96d6d-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="96d6d-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="96d6d-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="96d6d-123">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="96d6d-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96d6d-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="96d6d-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="96d6d-125">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="96d6d-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96d6d-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="96d6d-126">Header</span></span></p></td>
<td><span data-ttu-id="96d6d-127">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="96d6d-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96d6d-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="96d6d-128">Library</span></span></p></td>
<td><span data-ttu-id="96d6d-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="96d6d-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96d6d-130">DLL</span><span class="sxs-lookup"><span data-stu-id="96d6d-130">DLL</span></span></p></td>
<td><span data-ttu-id="96d6d-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="96d6d-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="96d6d-132"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="96d6d-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="96d6d-133">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="96d6d-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="96d6d-134">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="96d6d-134">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="96d6d-135">**COORD**</span><span class="sxs-lookup"><span data-stu-id="96d6d-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="96d6d-136">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="96d6d-136">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="96d6d-137">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="96d6d-137">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

 

 




