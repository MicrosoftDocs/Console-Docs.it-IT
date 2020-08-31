---
title: WriteConsoleOutputAttribute (funzione)
description: Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060477"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="2acbc-104">WriteConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="2acbc-104">WriteConsoleOutputAttribute function</span></span>


<span data-ttu-id="2acbc-105">Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="2acbc-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="2acbc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2acbc-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="2acbc-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="2acbc-107">Parameters</span></span>
----------

<span data-ttu-id="2acbc-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2acbc-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2acbc-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2acbc-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2acbc-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="2acbc-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="2acbc-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2acbc-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2acbc-112">*lpAttribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2acbc-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="2acbc-113">Attributi da utilizzare durante la scrittura nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2acbc-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="2acbc-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="2acbc-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="2acbc-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2acbc-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="2acbc-116">Numero di celle di caratteri del buffer dello schermo in cui verranno copiati gli attributi.</span><span class="sxs-lookup"><span data-stu-id="2acbc-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="2acbc-117">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2acbc-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="2acbc-118">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella nel buffer dello schermo della console in cui verranno scritti gli attributi.</span><span class="sxs-lookup"><span data-stu-id="2acbc-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="2acbc-119">*lpNumberOfAttrsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="2acbc-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="2acbc-120">Puntatore a una variabile che riceve il numero di attributi effettivamente scritti nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2acbc-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="2acbc-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2acbc-121">Return value</span></span>
------------

<span data-ttu-id="2acbc-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2acbc-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2acbc-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2acbc-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2acbc-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2acbc-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2acbc-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2acbc-125">Remarks</span></span>
-------

<span data-ttu-id="2acbc-126">Se il numero di attributi da scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, gli attributi vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="2acbc-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="2acbc-127">Se il numero di attributi da scrivere si estende oltre la fine del buffer dello schermo della console, gli attributi vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2acbc-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="2acbc-128">I valori di carattere nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="2acbc-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="2acbc-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2acbc-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2acbc-130">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2acbc-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2acbc-131">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2acbc-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2acbc-132">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2acbc-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2acbc-133">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2acbc-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2acbc-134">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2acbc-134">Header</span></span></p></td>
<td><span data-ttu-id="2acbc-135">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2acbc-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2acbc-136">Libreria</span><span class="sxs-lookup"><span data-stu-id="2acbc-136">Library</span></span></p></td>
<td><span data-ttu-id="2acbc-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2acbc-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2acbc-138">DLL</span><span class="sxs-lookup"><span data-stu-id="2acbc-138">DLL</span></span></p></td>
<td><span data-ttu-id="2acbc-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2acbc-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2acbc-140"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2acbc-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2acbc-141">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="2acbc-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2acbc-142">**COORD**</span><span class="sxs-lookup"><span data-stu-id="2acbc-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2acbc-143">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="2acbc-143">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="2acbc-144">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2acbc-144">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="2acbc-145">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="2acbc-145">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="2acbc-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="2acbc-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="2acbc-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="2acbc-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="2acbc-148">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="2acbc-148">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




