---
title: ReadConsoleOutput (funzione)
description: Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e scrive i dati nel buffer di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 382ed9cd06586ab86097c6efd2f6b8ea92f03eaf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060409"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="00887-104">ReadConsoleOutput (funzione)</span><span class="sxs-lookup"><span data-stu-id="00887-104">ReadConsoleOutput function</span></span>


<span data-ttu-id="00887-105">Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e la funzione scrive i dati in un blocco rettangolare in una posizione specificata nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="00887-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="00887-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="00887-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

<a name="parameters"></a><span data-ttu-id="00887-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="00887-107">Parameters</span></span>
----------

<span data-ttu-id="00887-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="00887-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="00887-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="00887-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="00887-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="00887-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="00887-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="00887-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="00887-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="00887-113">Puntatore a un buffer di destinazione che riceve i dati letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="00887-114">Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [\*\* \_ informazioni char\*\*](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="00887-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="00887-115">*dwBufferSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="00887-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="00887-116">Dimensioni del parametro *lpBuffer* , in celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="00887-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="00887-117">Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.</span><span class="sxs-lookup"><span data-stu-id="00887-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="00887-118">*dwBufferCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="00887-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="00887-119">Coordinate della cella superiore sinistra nel parametro *lpBuffer* che riceve i dati letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="00887-120">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="00887-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="00887-121">*lpReadRegion* \[ in uscita\]</span><span class="sxs-lookup"><span data-stu-id="00887-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="00887-122">Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="00887-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="00887-123">In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console da cui la funzione deve essere letta.</span><span class="sxs-lookup"><span data-stu-id="00887-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="00887-124">Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.</span><span class="sxs-lookup"><span data-stu-id="00887-124">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="00887-125">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="00887-125">Return value</span></span>
------------

<span data-ttu-id="00887-126">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="00887-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="00887-127">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="00887-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="00887-128">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="00887-128">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="00887-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="00887-129">Remarks</span></span>
-------

<span data-ttu-id="00887-130">**ReadConsoleOutput** considera il buffer dello schermo della console e il buffer di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere).</span><span class="sxs-lookup"><span data-stu-id="00887-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="00887-131">Il rettangolo a cui punta il parametro *lpReadRegion* specifica le dimensioni e la posizione del blocco da leggere dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="00887-132">Un rettangolo di destinazione della stessa dimensione si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="00887-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="00887-133">I dati letti dalle celle del rettangolo di origine buffer dello schermo della console vengono copiati nelle celle corrispondenti nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="00887-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="00887-134">Se la cella corrispondente non rientra nei limiti del rettangolo del buffer di destinazione (le cui dimensioni sono specificate dal parametro *dwBufferSize* ), i dati non vengono copiati.</span><span class="sxs-lookup"><span data-stu-id="00887-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="00887-135">Le celle del buffer di destinazione corrispondenti alle coordinate che non rientrano nei limiti del buffer dello schermo della console rimangono invariate.</span><span class="sxs-lookup"><span data-stu-id="00887-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="00887-136">In altre parole, queste sono le celle per le quali non sono disponibili dati del buffer dello schermo da leggere.</span><span class="sxs-lookup"><span data-stu-id="00887-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="00887-137">Prima della restituzione di **ReadConsoleOutput** , imposta i membri della struttura a cui punta il parametro *lpReadRegion* sul rettangolo del buffer dello schermo effettivo le cui celle sono state copiate nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="00887-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="00887-138">Questo rettangolo riflette le celle del rettangolo di origine per cui esiste una cella corrispondente nel buffer di destinazione, perché **ReadConsoleOutput** Ritaglia le dimensioni del rettangolo di origine per adattarsi ai limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="00887-139">Se il rettangolo specificato da *lpReadRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di destinazione, non vengono copiati dati.</span><span class="sxs-lookup"><span data-stu-id="00887-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="00887-140">In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpReadRegion* , in modo tale che il membro **destro** sia minore della **sinistra**o che il membro **inferiore** sia minore della **parte superiore**.</span><span class="sxs-lookup"><span data-stu-id="00887-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="00887-141">Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="00887-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="00887-142">La funzione **ReadConsoleOutput** non ha alcun effetto sulla posizione del cursore del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="00887-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="00887-143">Il contenuto del buffer dello schermo della console non viene modificato dalla funzione.</span><span class="sxs-lookup"><span data-stu-id="00887-143">The contents of the console screen buffer are not changed by the function.</span></span>

<span data-ttu-id="00887-144">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="00887-144">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="00887-145">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="00887-145">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="00887-146">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="00887-146">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="00887-147">Esempi</span><span class="sxs-lookup"><span data-stu-id="00887-147">Examples</span></span>
--------

<span data-ttu-id="00887-148">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="00887-148">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="00887-149">Requisiti</span><span class="sxs-lookup"><span data-stu-id="00887-149">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="00887-150">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="00887-150">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="00887-151">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="00887-151">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="00887-152">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="00887-152">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="00887-153">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="00887-153">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="00887-154">Intestazione</span><span class="sxs-lookup"><span data-stu-id="00887-154">Header</span></span></p></td>
<td><span data-ttu-id="00887-155">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="00887-155">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="00887-156">Libreria</span><span class="sxs-lookup"><span data-stu-id="00887-156">Library</span></span></p></td>
<td><span data-ttu-id="00887-157">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="00887-157">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="00887-158">DLL</span><span class="sxs-lookup"><span data-stu-id="00887-158">DLL</span></span></p></td>
<td><span data-ttu-id="00887-159">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="00887-159">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="00887-160">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="00887-160">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="00887-161"><strong>ReadConsoleOutputW</strong> (Unicode) e <strong>ReadConsoleOutputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="00887-161"><strong>ReadConsoleOutputW</strong> (Unicode) and <strong>ReadConsoleOutputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="00887-162"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="00887-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="00887-163">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="00887-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="00887-164">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="00887-164">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="00887-165">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="00887-165">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="00887-166">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="00887-166">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="00887-167">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="00887-167">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="00887-168">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="00887-168">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="00887-169">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="00887-169">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="00887-170">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="00887-170">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="00887-171">**\_informazioni char**</span><span class="sxs-lookup"><span data-stu-id="00887-171">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="00887-172">**COORD**</span><span class="sxs-lookup"><span data-stu-id="00887-172">**COORD**</span></span>](coord-str.md)

 

 




