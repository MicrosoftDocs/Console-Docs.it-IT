---
title: WriteConsoleOutputCharacter (funzione)
description: Copia un numero di caratteri in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bc313abbcb28016968355cc405e0cc2de3d36cb0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060471"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="75ca6-104">WriteConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="75ca6-104">WriteConsoleOutputCharacter function</span></span>


<span data-ttu-id="75ca6-105">Copia un numero di caratteri in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="75ca6-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="75ca6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75ca6-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="75ca6-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="75ca6-107">Parameters</span></span>
----------

<span data-ttu-id="75ca6-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="75ca6-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="75ca6-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="75ca6-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="75ca6-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="75ca6-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="75ca6-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="75ca6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="75ca6-112">*lpCharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="75ca6-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="75ca6-113">Caratteri da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="75ca6-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="75ca6-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="75ca6-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="75ca6-115">Numero di caratteri da scrivere.</span><span class="sxs-lookup"><span data-stu-id="75ca6-115">The number of characters to be written.</span></span>

<span data-ttu-id="75ca6-116">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="75ca6-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="75ca6-117">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella nel buffer dello schermo della console in cui verranno scritti i caratteri.</span><span class="sxs-lookup"><span data-stu-id="75ca6-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="75ca6-118">*lpNumberOfCharsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="75ca6-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="75ca6-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="75ca6-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="75ca6-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="75ca6-120">Return value</span></span>
------------

<span data-ttu-id="75ca6-121">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="75ca6-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="75ca6-122">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="75ca6-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="75ca6-123">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="75ca6-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="75ca6-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="75ca6-124">Remarks</span></span>
-------

<span data-ttu-id="75ca6-125">Se il numero di caratteri da scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="75ca6-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="75ca6-126">Se il numero di caratteri da scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="75ca6-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="75ca6-127">I valori di attributo nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="75ca6-127">The attribute values at the positions written to are not changed.</span></span>

<span data-ttu-id="75ca6-128">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="75ca6-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="75ca6-129">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="75ca6-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="75ca6-130">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="75ca6-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="75ca6-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="75ca6-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="75ca6-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="75ca6-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="75ca6-133">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="75ca6-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="75ca6-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="75ca6-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="75ca6-135">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="75ca6-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="75ca6-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="75ca6-136">Header</span></span></p></td>
<td><span data-ttu-id="75ca6-137">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="75ca6-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="75ca6-138">Libreria</span><span class="sxs-lookup"><span data-stu-id="75ca6-138">Library</span></span></p></td>
<td><span data-ttu-id="75ca6-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="75ca6-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="75ca6-140">DLL</span><span class="sxs-lookup"><span data-stu-id="75ca6-140">DLL</span></span></p></td>
<td><span data-ttu-id="75ca6-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="75ca6-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="75ca6-142">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="75ca6-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="75ca6-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) e <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="75ca6-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) and <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="75ca6-144"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75ca6-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="75ca6-145">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="75ca6-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="75ca6-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="75ca6-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="75ca6-147">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="75ca6-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="75ca6-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="75ca6-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="75ca6-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="75ca6-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="75ca6-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="75ca6-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="75ca6-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="75ca6-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="75ca6-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="75ca6-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="75ca6-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="75ca6-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="75ca6-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="75ca6-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 




