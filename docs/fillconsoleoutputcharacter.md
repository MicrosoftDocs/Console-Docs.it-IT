---
title: FillConsoleOutputCharacter (funzione)
description: Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059884"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="f1463-104">FillConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="f1463-104">FillConsoleOutputCharacter function</span></span>


<span data-ttu-id="f1463-105">Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.</span><span class="sxs-lookup"><span data-stu-id="f1463-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

<a name="syntax"></a><span data-ttu-id="f1463-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f1463-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="f1463-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="f1463-107">Parameters</span></span>
----------

<span data-ttu-id="f1463-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f1463-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f1463-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f1463-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f1463-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="f1463-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="f1463-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="f1463-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f1463-112">*cCharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f1463-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="f1463-113">Carattere da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f1463-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="f1463-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f1463-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="f1463-115">Numero di celle di caratteri in cui deve essere scritto il carattere.</span><span class="sxs-lookup"><span data-stu-id="f1463-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="f1463-116">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f1463-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="f1463-117">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella in cui deve essere scritto il carattere.</span><span class="sxs-lookup"><span data-stu-id="f1463-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="f1463-118">*lpNumberOfCharsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="f1463-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="f1463-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f1463-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="f1463-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f1463-120">Return value</span></span>
------------

<span data-ttu-id="f1463-121">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="f1463-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f1463-122">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="f1463-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f1463-123">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f1463-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f1463-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f1463-124">Remarks</span></span>
-------

<span data-ttu-id="f1463-125">Se il numero di caratteri in cui scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="f1463-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="f1463-126">Se il numero di caratteri in cui scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="f1463-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="f1463-127">I valori di attributo nelle posizioni scritte non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="f1463-127">The attribute values at the positions written are not changed.</span></span>

<span data-ttu-id="f1463-128">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="f1463-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="f1463-129">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="f1463-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="f1463-130">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="f1463-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="f1463-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f1463-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f1463-132">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f1463-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f1463-133">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f1463-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f1463-134">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="f1463-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f1463-135">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="f1463-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f1463-136">Intestazione</span><span class="sxs-lookup"><span data-stu-id="f1463-136">Header</span></span></p></td>
<td><span data-ttu-id="f1463-137">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f1463-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f1463-138">Libreria</span><span class="sxs-lookup"><span data-stu-id="f1463-138">Library</span></span></p></td>
<td><span data-ttu-id="f1463-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f1463-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f1463-140">DLL</span><span class="sxs-lookup"><span data-stu-id="f1463-140">DLL</span></span></p></td>
<td><span data-ttu-id="f1463-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f1463-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f1463-142">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="f1463-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="f1463-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) e <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="f1463-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f1463-144"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1463-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f1463-145">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="f1463-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f1463-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="f1463-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f1463-147">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f1463-147">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="f1463-148">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="f1463-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="f1463-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f1463-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f1463-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f1463-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f1463-151">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f1463-151">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




