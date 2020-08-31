---
title: GetCurrentConsoleFont (funzione)
description: Recupera le informazioni sul tipo di carattere della console corrente per un buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059681"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="e341c-104">GetCurrentConsoleFont (funzione)</span><span class="sxs-lookup"><span data-stu-id="e341c-104">GetCurrentConsoleFont function</span></span>


<span data-ttu-id="e341c-105">Recupera le informazioni sul tipo di carattere della console corrente.</span><span class="sxs-lookup"><span data-stu-id="e341c-105">Retrieves information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="e341c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e341c-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a><span data-ttu-id="e341c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="e341c-107">Parameters</span></span>
----------

<span data-ttu-id="e341c-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e341c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e341c-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="e341c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="e341c-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="e341c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e341c-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e341c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e341c-112">*bMaximumWindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e341c-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="e341c-113">Se questo parametro è **true**, vengono recuperate le informazioni relative al tipo di carattere per la dimensione massima della finestra.</span><span class="sxs-lookup"><span data-stu-id="e341c-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="e341c-114">Se questo parametro è **false**, vengono recuperate le informazioni relative al tipo di carattere per le dimensioni correnti della finestra.</span><span class="sxs-lookup"><span data-stu-id="e341c-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="e341c-115">*lpConsoleCurrentFont* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="e341c-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="e341c-116">Puntatore a una struttura [**di \_ \_ informazioni sul tipo di carattere della console**](console-font-info-str.md) che riceve le informazioni sul tipo di carattere richieste.</span><span class="sxs-lookup"><span data-stu-id="e341c-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="e341c-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e341c-117">Return value</span></span>
------------

<span data-ttu-id="e341c-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e341c-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e341c-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e341c-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e341c-120">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e341c-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e341c-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e341c-121">Remarks</span></span>
-------

<span data-ttu-id="e341c-122">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="e341c-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="e341c-123">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="e341c-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="e341c-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e341c-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e341c-125">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e341c-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e341c-126">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e341c-126">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e341c-127">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e341c-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e341c-128">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e341c-128">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e341c-129">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e341c-129">Header</span></span></p></td>
<td><span data-ttu-id="e341c-130">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e341c-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e341c-131">Libreria</span><span class="sxs-lookup"><span data-stu-id="e341c-131">Library</span></span></p></td>
<td><span data-ttu-id="e341c-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e341c-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e341c-133">DLL</span><span class="sxs-lookup"><span data-stu-id="e341c-133">DLL</span></span></p></td>
<td><span data-ttu-id="e341c-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e341c-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e341c-135"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e341c-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e341c-136">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="e341c-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e341c-137">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="e341c-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="e341c-138">**informazioni sul tipo di carattere della CONSOLE \_ \_**</span><span class="sxs-lookup"><span data-stu-id="e341c-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="e341c-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="e341c-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

 

 




