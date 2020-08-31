---
title: GetConsoleFontSize (funzione)
description: Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059796"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="1c398-104">GetConsoleFontSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="1c398-104">GetConsoleFontSize function</span></span>


<span data-ttu-id="1c398-105">Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="1c398-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="1c398-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1c398-106">Syntax</span></span>
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a><span data-ttu-id="1c398-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="1c398-107">Parameters</span></span>
----------

<span data-ttu-id="1c398-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1c398-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1c398-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="1c398-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1c398-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="1c398-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1c398-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1c398-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1c398-112">*nFont* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1c398-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="1c398-113">Indice del tipo di carattere di cui è necessario recuperare le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="1c398-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="1c398-114">Questo indice viene ottenuto chiamando la funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="1c398-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

<a name="return-value"></a><span data-ttu-id="1c398-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1c398-115">Return value</span></span>
------------

<span data-ttu-id="1c398-116">Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="1c398-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="1c398-117">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="1c398-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="1c398-118">Se la funzione ha esito negativo, la larghezza e l'altezza sono pari a zero.</span><span class="sxs-lookup"><span data-stu-id="1c398-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="1c398-119">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1c398-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="1c398-120">Per compilare un'applicazione che usa questa funzione, definire \*\* \_ Win32 \_ WinNT\*\* come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="1c398-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="1c398-121">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1c398-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="1c398-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1c398-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1c398-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1c398-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1c398-124">Windows XP [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="1c398-124">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1c398-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="1c398-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1c398-126">Windows Server 2003 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="1c398-126">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1c398-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="1c398-127">Header</span></span></p></td>
<td><span data-ttu-id="1c398-128">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1c398-128">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1c398-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="1c398-129">Library</span></span></p></td>
<td><span data-ttu-id="1c398-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1c398-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1c398-131">DLL</span><span class="sxs-lookup"><span data-stu-id="1c398-131">DLL</span></span></p></td>
<td><span data-ttu-id="1c398-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1c398-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1c398-133"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c398-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1c398-134">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="1c398-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1c398-135">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="1c398-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="1c398-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="1c398-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1c398-137">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="1c398-137">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




