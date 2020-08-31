---
title: WriteConsoleOutput (funzione)
description: Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059564"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="24aa1-104">WriteConsoleOutput (funzione)</span><span class="sxs-lookup"><span data-stu-id="24aa1-104">WriteConsoleOutput function</span></span>


<span data-ttu-id="24aa1-105">Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="24aa1-106">I dati da scrivere vengono ricavati da un blocco rettangolare di dimensioni corrispondenti in una posizione specificata nel buffer di origine.</span><span class="sxs-lookup"><span data-stu-id="24aa1-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="24aa1-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24aa1-107">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a><span data-ttu-id="24aa1-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="24aa1-108">Parameters</span></span>
----------

<span data-ttu-id="24aa1-109">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="24aa1-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="24aa1-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="24aa1-111">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="24aa1-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="24aa1-112">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="24aa1-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="24aa1-113">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="24aa1-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="24aa1-114">Dati da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="24aa1-115">Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [\*\* \_ informazioni char\*\*](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="24aa1-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="24aa1-116">*dwBufferSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="24aa1-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="24aa1-117">Dimensioni del buffer a cui punta il parametro *lpBuffer* , in celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="24aa1-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="24aa1-118">Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.</span><span class="sxs-lookup"><span data-stu-id="24aa1-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="24aa1-119">*dwBufferCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="24aa1-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="24aa1-120">Coordinate della cella superiore sinistra nel buffer a cui punta il parametro *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="24aa1-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="24aa1-121">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="24aa1-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="24aa1-122">*lpWriteRegion* \[ in uscita\]</span><span class="sxs-lookup"><span data-stu-id="24aa1-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="24aa1-123">Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="24aa1-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="24aa1-124">In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console in cui scrivere.</span><span class="sxs-lookup"><span data-stu-id="24aa1-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="24aa1-125">Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.</span><span class="sxs-lookup"><span data-stu-id="24aa1-125">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="24aa1-126">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="24aa1-126">Return value</span></span>
------------

<span data-ttu-id="24aa1-127">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="24aa1-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="24aa1-128">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="24aa1-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="24aa1-129">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="24aa1-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="24aa1-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="24aa1-130">Remarks</span></span>
-------

<span data-ttu-id="24aa1-131">**WriteConsoleOutput** considera il buffer di origine e il buffer dello schermo di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere).</span><span class="sxs-lookup"><span data-stu-id="24aa1-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="24aa1-132">Il rettangolo a cui punta il parametro *lpWriteRegion* specifica le dimensioni e la posizione del blocco in cui scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="24aa1-133">Un rettangolo con le stesse dimensioni si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="24aa1-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="24aa1-134">I dati delle celle presenti nell'intersezione tra il rettangolo e il rettangolo del buffer di origine (le cui dimensioni sono specificate dal parametro *dwBufferSize* ) vengono scritti nel rettangolo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="24aa1-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="24aa1-135">Le celle nel rettangolo di destinazione il cui percorso di origine corrispondente si trova al di fuori dei limiti del rettangolo del buffer di origine non vengono influenzate dall'operazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="24aa1-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="24aa1-136">In altre parole, queste sono le celle per le quali non sono disponibili dati da scrivere.</span><span class="sxs-lookup"><span data-stu-id="24aa1-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="24aa1-137">Prima della restituzione di **WriteConsoleOutput** , imposta i membri di *lpWriteRegion* sul rettangolo del buffer dello schermo effettivo interessato dall'operazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="24aa1-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="24aa1-138">Questo rettangolo riflette le celle del rettangolo di destinazione per cui esiste una cella corrispondente nel buffer di origine, perché **WriteConsoleOutput** Ritaglia le dimensioni del rettangolo di destinazione ai limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="24aa1-139">Se il rettangolo specificato da *lpWriteRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di origine, non viene scritto alcun dato.</span><span class="sxs-lookup"><span data-stu-id="24aa1-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="24aa1-140">In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpWriteRegion* , in modo tale che il membro **destro** sia minore della **sinistra**o che il membro **inferiore** sia minore della **parte superiore**.</span><span class="sxs-lookup"><span data-stu-id="24aa1-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="24aa1-141">Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="24aa1-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="24aa1-142">**WriteConsoleOutput** non ha alcun effetto sulla posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="24aa1-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

<span data-ttu-id="24aa1-143">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="24aa1-143">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="24aa1-144">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="24aa1-144">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="24aa1-145">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="24aa1-145">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="24aa1-146">Esempi</span><span class="sxs-lookup"><span data-stu-id="24aa1-146">Examples</span></span>
--------

<span data-ttu-id="24aa1-147">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="24aa1-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="24aa1-148">Requisiti</span><span class="sxs-lookup"><span data-stu-id="24aa1-148">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="24aa1-149">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="24aa1-149">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="24aa1-150">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="24aa1-150">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="24aa1-151">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="24aa1-151">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="24aa1-152">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="24aa1-152">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="24aa1-153">Intestazione</span><span class="sxs-lookup"><span data-stu-id="24aa1-153">Header</span></span></p></td>
<td><span data-ttu-id="24aa1-154">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="24aa1-154">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="24aa1-155">Libreria</span><span class="sxs-lookup"><span data-stu-id="24aa1-155">Library</span></span></p></td>
<td><span data-ttu-id="24aa1-156">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="24aa1-156">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="24aa1-157">DLL</span><span class="sxs-lookup"><span data-stu-id="24aa1-157">DLL</span></span></p></td>
<td><span data-ttu-id="24aa1-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="24aa1-158">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="24aa1-159">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="24aa1-159">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="24aa1-160"><strong>WriteConsoleOutputW</strong> (Unicode) e <strong>WriteConsoleOutputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="24aa1-160"><strong>WriteConsoleOutputW</strong> (Unicode) and <strong>WriteConsoleOutputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="24aa1-161"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24aa1-161"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="24aa1-162">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="24aa1-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="24aa1-163">**\_informazioni char**</span><span class="sxs-lookup"><span data-stu-id="24aa1-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="24aa1-164">**COORD**</span><span class="sxs-lookup"><span data-stu-id="24aa1-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="24aa1-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="24aa1-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="24aa1-166">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="24aa1-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="24aa1-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="24aa1-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="24aa1-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="24aa1-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="24aa1-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="24aa1-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="24aa1-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="24aa1-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="24aa1-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="24aa1-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="24aa1-172">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="24aa1-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="24aa1-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="24aa1-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="24aa1-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="24aa1-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




