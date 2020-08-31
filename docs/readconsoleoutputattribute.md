---
title: ReadConsoleOutputAttribute (funzione)
description: Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4cf3ac9b85c3eab73c3530c1fd9991a7fbbf5a5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060393"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="8b483-104">ReadConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="8b483-104">ReadConsoleOutputAttribute function</span></span>


<span data-ttu-id="8b483-105">Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="8b483-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="8b483-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8b483-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

<a name="parameters"></a><span data-ttu-id="8b483-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8b483-107">Parameters</span></span>
----------

<span data-ttu-id="8b483-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8b483-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8b483-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8b483-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="8b483-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="8b483-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="8b483-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="8b483-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8b483-112">*lpAttribute* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8b483-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="8b483-113">Puntatore a un buffer che riceve gli attributi utilizzati dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8b483-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="8b483-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="8b483-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="8b483-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8b483-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="8b483-116">Numero di celle di caratteri del buffer dello schermo da cui eseguire la lettura.</span><span class="sxs-lookup"><span data-stu-id="8b483-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="8b483-117">La dimensione del buffer a cui punta il parametro *lpAttribute* deve essere `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="8b483-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="8b483-118">*dwReadCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8b483-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="8b483-119">Coordinate della prima cella nel buffer dello schermo della console da cui leggere, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="8b483-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="8b483-120">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="8b483-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="8b483-121">*lpNumberOfAttrsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8b483-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="8b483-122">Puntatore a una variabile che riceve il numero di attributi effettivamente letti.</span><span class="sxs-lookup"><span data-stu-id="8b483-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="8b483-123">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8b483-123">Return value</span></span>
------------

<span data-ttu-id="8b483-124">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="8b483-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8b483-125">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="8b483-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8b483-126">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="8b483-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="8b483-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8b483-127">Remarks</span></span>
-------

<span data-ttu-id="8b483-128">Se il numero di attributi da leggere da si estende oltre la fine della riga del buffer dello schermo specificata, gli attributi vengono letti dalla riga successiva.</span><span class="sxs-lookup"><span data-stu-id="8b483-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="8b483-129">Se il numero di attributi da leggere da si estende oltre la fine del buffer dello schermo della console, vengono letti gli attributi fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8b483-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

<a name="requirements"></a><span data-ttu-id="8b483-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8b483-130">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8b483-131">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8b483-131">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8b483-132">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8b483-132">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8b483-133">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8b483-133">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8b483-134">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8b483-134">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8b483-135">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8b483-135">Header</span></span></p></td>
<td><span data-ttu-id="8b483-136">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8b483-136">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8b483-137">Libreria</span><span class="sxs-lookup"><span data-stu-id="8b483-137">Library</span></span></p></td>
<td><span data-ttu-id="8b483-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8b483-138">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8b483-139">DLL</span><span class="sxs-lookup"><span data-stu-id="8b483-139">DLL</span></span></p></td>
<td><span data-ttu-id="8b483-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8b483-140">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8b483-141"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8b483-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8b483-142">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="8b483-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8b483-143">**COORD**</span><span class="sxs-lookup"><span data-stu-id="8b483-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="8b483-144">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="8b483-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="8b483-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8b483-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="8b483-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="8b483-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="8b483-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8b483-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="8b483-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="8b483-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="8b483-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="8b483-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




