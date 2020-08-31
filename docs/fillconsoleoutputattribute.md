---
title: FillConsoleOutputAttribute (funzione)
description: Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059881"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="65d1e-104">FillConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="65d1e-104">FillConsoleOutputAttribute function</span></span>


<span data-ttu-id="65d1e-105">Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="65d1e-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="65d1e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="65d1e-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="65d1e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="65d1e-107">Parameters</span></span>
----------

<span data-ttu-id="65d1e-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65d1e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="65d1e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="65d1e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="65d1e-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="65d1e-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="65d1e-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="65d1e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="65d1e-112">*wAttribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65d1e-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="65d1e-113">Attributi da utilizzare durante la scrittura nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="65d1e-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="65d1e-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="65d1e-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="65d1e-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65d1e-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="65d1e-116">Numero di celle di tipo carattere da impostare sugli attributi di colore specificati.</span><span class="sxs-lookup"><span data-stu-id="65d1e-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="65d1e-117">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65d1e-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="65d1e-118">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella i cui attributi devono essere impostati.</span><span class="sxs-lookup"><span data-stu-id="65d1e-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="65d1e-119">*lpNumberOfAttrsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="65d1e-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="65d1e-120">Puntatore a una variabile che riceve il numero di celle di tipo carattere i cui attributi sono stati effettivamente impostati.</span><span class="sxs-lookup"><span data-stu-id="65d1e-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

<a name="return-value"></a><span data-ttu-id="65d1e-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="65d1e-121">Return value</span></span>
------------

<span data-ttu-id="65d1e-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="65d1e-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="65d1e-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="65d1e-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="65d1e-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="65d1e-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="65d1e-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="65d1e-125">Remarks</span></span>
-------

<span data-ttu-id="65d1e-126">Se il numero di celle di tipo carattere i cui attributi devono essere impostati si estende oltre la fine della riga specificata nel buffer dello schermo della console, vengono impostate le celle della riga successiva.</span><span class="sxs-lookup"><span data-stu-id="65d1e-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="65d1e-127">Se il numero di celle in cui scrivere si estende oltre la fine del buffer dello schermo della console, le celle vengono scritte fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="65d1e-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="65d1e-128">I valori di carattere nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="65d1e-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="65d1e-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="65d1e-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="65d1e-130">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="65d1e-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="65d1e-131">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="65d1e-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="65d1e-132">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="65d1e-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="65d1e-133">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="65d1e-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="65d1e-134">Intestazione</span><span class="sxs-lookup"><span data-stu-id="65d1e-134">Header</span></span></p></td>
<td><span data-ttu-id="65d1e-135">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="65d1e-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="65d1e-136">Libreria</span><span class="sxs-lookup"><span data-stu-id="65d1e-136">Library</span></span></p></td>
<td><span data-ttu-id="65d1e-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="65d1e-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="65d1e-138">DLL</span><span class="sxs-lookup"><span data-stu-id="65d1e-138">DLL</span></span></p></td>
<td><span data-ttu-id="65d1e-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="65d1e-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="65d1e-140"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="65d1e-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="65d1e-141">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="65d1e-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="65d1e-142">**COORD**</span><span class="sxs-lookup"><span data-stu-id="65d1e-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="65d1e-143">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="65d1e-143">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="65d1e-144">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="65d1e-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="65d1e-145">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="65d1e-145">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="65d1e-146">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="65d1e-146">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




