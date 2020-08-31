---
title: GetConsoleScreenBufferInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleScreenBufferInfo, che recupera le informazioni sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059716"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="69ad1-104">GetConsoleScreenBufferInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="69ad1-104">GetConsoleScreenBufferInfo function</span></span>


<span data-ttu-id="69ad1-105">Recupera le informazioni sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="69ad1-105">Retrieves information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="69ad1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69ad1-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a><span data-ttu-id="69ad1-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="69ad1-107">Parameters</span></span>
----------

<span data-ttu-id="69ad1-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="69ad1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="69ad1-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="69ad1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="69ad1-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="69ad1-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="69ad1-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="69ad1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="69ad1-112">*lpConsoleScreenBufferInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="69ad1-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="69ad1-113">Puntatore a una struttura [**di \_ \_ \_ informazioni sul buffer dello schermo della console**](console-screen-buffer-info-str.md) che riceve le informazioni sul buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="69ad1-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="69ad1-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="69ad1-114">Return value</span></span>
------------

<span data-ttu-id="69ad1-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="69ad1-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="69ad1-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="69ad1-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="69ad1-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="69ad1-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="69ad1-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="69ad1-118">Remarks</span></span>
-------

<span data-ttu-id="69ad1-119">Il rettangolo restituito nel membro **srWindow** della struttura di [\*\* \_ informazioni sul \_ buffer \_ dello schermo della console\*\*](console-screen-buffer-info-str.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.</span><span class="sxs-lookup"><span data-stu-id="69ad1-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="69ad1-120">Tutte le coordinate restituite nella struttura delle [\*\* \_ \_ \_ informazioni del buffer dello schermo della console\*\*](console-screen-buffer-info-str.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="69ad1-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="69ad1-121">Esempi</span><span class="sxs-lookup"><span data-stu-id="69ad1-121">Examples</span></span>
--------

<span data-ttu-id="69ad1-122">Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="69ad1-122">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="69ad1-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="69ad1-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="69ad1-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="69ad1-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="69ad1-125">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="69ad1-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ad1-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="69ad1-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="69ad1-127">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="69ad1-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ad1-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="69ad1-128">Header</span></span></p></td>
<td><span data-ttu-id="69ad1-129">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="69ad1-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ad1-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="69ad1-130">Library</span></span></p></td>
<td><span data-ttu-id="69ad1-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="69ad1-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ad1-132">DLL</span><span class="sxs-lookup"><span data-stu-id="69ad1-132">DLL</span></span></p></td>
<td><span data-ttu-id="69ad1-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="69ad1-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="69ad1-134"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69ad1-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="69ad1-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="69ad1-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="69ad1-136">**\_informazioni sul \_ buffer dello schermo della console \_**</span><span class="sxs-lookup"><span data-stu-id="69ad1-136">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="69ad1-137">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="69ad1-137">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="69ad1-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="69ad1-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="69ad1-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="69ad1-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="69ad1-140">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="69ad1-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="69ad1-141">Dimensioni del buffer della finestra e dello schermo</span><span class="sxs-lookup"><span data-stu-id="69ad1-141">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




