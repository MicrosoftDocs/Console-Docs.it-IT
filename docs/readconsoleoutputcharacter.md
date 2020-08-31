---
title: ReadConsoleOutputCharacter (funzione)
description: Copia un numero di caratteri dalle celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8f761d10951e6df77a54fd075c29379657204a99
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060364"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="8bddf-104">ReadConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="8bddf-104">ReadConsoleOutputCharacter function</span></span>


<span data-ttu-id="8bddf-105">Copia un numero di caratteri dalle celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="8bddf-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="8bddf-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8bddf-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

<a name="parameters"></a><span data-ttu-id="8bddf-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8bddf-107">Parameters</span></span>
----------

<span data-ttu-id="8bddf-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8bddf-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8bddf-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8bddf-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="8bddf-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="8bddf-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="8bddf-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="8bddf-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8bddf-112">*lpCharacter* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8bddf-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="8bddf-113">Puntatore a un buffer che riceve i caratteri letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8bddf-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="8bddf-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8bddf-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="8bddf-115">Numero di celle di caratteri del buffer dello schermo da cui eseguire la lettura.</span><span class="sxs-lookup"><span data-stu-id="8bddf-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="8bddf-116">La dimensione del buffer a cui punta il parametro *lpCharacter* deve essere `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="8bddf-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="8bddf-117">*dwReadCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="8bddf-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="8bddf-118">Coordinate della prima cella nel buffer dello schermo della console da cui leggere, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="8bddf-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="8bddf-119">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="8bddf-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="8bddf-120">*lpNumberOfCharsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="8bddf-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="8bddf-121">Puntatore a una variabile che riceve il numero di caratteri effettivamente letti.</span><span class="sxs-lookup"><span data-stu-id="8bddf-121">A pointer to a variable that receives the number of characters actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="8bddf-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8bddf-122">Return value</span></span>
------------

<span data-ttu-id="8bddf-123">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="8bddf-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8bddf-124">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="8bddf-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8bddf-125">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="8bddf-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="8bddf-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8bddf-126">Remarks</span></span>
-------

<span data-ttu-id="8bddf-127">Se il numero di caratteri da leggere da si estende oltre la fine della riga del buffer dello schermo specificata, i caratteri vengono letti dalla riga successiva.</span><span class="sxs-lookup"><span data-stu-id="8bddf-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="8bddf-128">Se il numero di caratteri da leggere da si estende oltre la fine del buffer dello schermo della console, vengono letti i caratteri fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="8bddf-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

<span data-ttu-id="8bddf-129">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="8bddf-129">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="8bddf-130">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="8bddf-130">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="8bddf-131">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="8bddf-131">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="8bddf-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8bddf-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8bddf-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8bddf-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8bddf-134">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8bddf-134">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8bddf-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="8bddf-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8bddf-136">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="8bddf-136">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8bddf-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="8bddf-137">Header</span></span></p></td>
<td><span data-ttu-id="8bddf-138">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8bddf-138">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8bddf-139">Libreria</span><span class="sxs-lookup"><span data-stu-id="8bddf-139">Library</span></span></p></td>
<td><span data-ttu-id="8bddf-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8bddf-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8bddf-141">DLL</span><span class="sxs-lookup"><span data-stu-id="8bddf-141">DLL</span></span></p></td>
<td><span data-ttu-id="8bddf-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8bddf-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8bddf-143">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="8bddf-143">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="8bddf-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) e <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="8bddf-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) and <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8bddf-145"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8bddf-145"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8bddf-146">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="8bddf-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8bddf-147">**COORD**</span><span class="sxs-lookup"><span data-stu-id="8bddf-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="8bddf-148">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="8bddf-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="8bddf-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8bddf-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="8bddf-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="8bddf-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="8bddf-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="8bddf-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="8bddf-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="8bddf-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="8bddf-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="8bddf-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="8bddf-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="8bddf-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="8bddf-155">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="8bddf-155">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




