---
title: WriteConsoleOutput (funzione)
description: Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 1f10285cfc5c671ac5d31b8a575e84b1fd0f6a14
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359031"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="b1a96-104">WriteConsoleOutput (funzione)</span><span class="sxs-lookup"><span data-stu-id="b1a96-104">WriteConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b1a96-105">Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b1a96-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="b1a96-106">I dati da scrivere vengono ricavati da un blocco rettangolare di dimensioni corrispondenti in una posizione specificata nel buffer di origine.</span><span class="sxs-lookup"><span data-stu-id="b1a96-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1a96-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b1a96-107">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a><span data-ttu-id="b1a96-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="b1a96-108">Parameters</span></span>

<span data-ttu-id="b1a96-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b1a96-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b1a96-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="b1a96-111">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="b1a96-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="b1a96-112">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b1a96-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b1a96-113">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="b1a96-114">Dati da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b1a96-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="b1a96-115">Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [**\_ informazioni char**](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="b1a96-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="b1a96-116">*dwBufferSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="b1a96-117">Dimensioni del buffer a cui punta il parametro *lpBuffer* , in celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="b1a96-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="b1a96-118">Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.</span><span class="sxs-lookup"><span data-stu-id="b1a96-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="b1a96-119">*dwBufferCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="b1a96-120">Coordinate della cella superiore sinistra nel buffer a cui punta il parametro *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="b1a96-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="b1a96-121">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="b1a96-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="b1a96-122">*lpWriteRegion* \[ in uscita\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="b1a96-123">Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="b1a96-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="b1a96-124">In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console in cui scrivere.</span><span class="sxs-lookup"><span data-stu-id="b1a96-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="b1a96-125">Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.</span><span class="sxs-lookup"><span data-stu-id="b1a96-125">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1a96-126">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b1a96-126">Return value</span></span>

<span data-ttu-id="b1a96-127">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="b1a96-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b1a96-128">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="b1a96-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b1a96-129">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="b1a96-129">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b1a96-130">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b1a96-130">Remarks</span></span>

<span data-ttu-id="b1a96-131">**WriteConsoleOutput** considera il buffer di origine e il buffer dello schermo di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere).</span><span class="sxs-lookup"><span data-stu-id="b1a96-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="b1a96-132">Il rettangolo a cui punta il parametro *lpWriteRegion* specifica le dimensioni e la posizione del blocco in cui scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b1a96-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="b1a96-133">Un rettangolo con le stesse dimensioni si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="b1a96-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="b1a96-134">I dati delle celle presenti nell'intersezione tra il rettangolo e il rettangolo del buffer di origine (le cui dimensioni sono specificate dal parametro *dwBufferSize* ) vengono scritti nel rettangolo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b1a96-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="b1a96-135">Le celle nel rettangolo di destinazione il cui percorso di origine corrispondente si trova al di fuori dei limiti del rettangolo del buffer di origine non vengono influenzate dall'operazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="b1a96-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="b1a96-136">In altre parole, queste sono le celle per le quali non sono disponibili dati da scrivere.</span><span class="sxs-lookup"><span data-stu-id="b1a96-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="b1a96-137">Prima della restituzione di **WriteConsoleOutput** , imposta i membri di *lpWriteRegion* sul rettangolo del buffer dello schermo effettivo interessato dall'operazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="b1a96-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="b1a96-138">Questo rettangolo riflette le celle del rettangolo di destinazione per cui esiste una cella corrispondente nel buffer di origine, perché **WriteConsoleOutput** Ritaglia le dimensioni del rettangolo di destinazione ai limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b1a96-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="b1a96-139">Se il rettangolo specificato da *lpWriteRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di origine, non viene scritto alcun dato.</span><span class="sxs-lookup"><span data-stu-id="b1a96-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="b1a96-140">In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpWriteRegion* , in modo tale che il membro **destro** sia minore della **sinistra** o che il membro **inferiore** sia minore della **parte superiore**.</span><span class="sxs-lookup"><span data-stu-id="b1a96-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="b1a96-141">Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="b1a96-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="b1a96-142">**WriteConsoleOutput** non ha alcun effetto sulla posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="b1a96-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="b1a96-143">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="b1a96-143">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="b1a96-144">Spostare il cursore sul percorso da inserire, applicare la formattazione desiderata e scrivere il testo.</span><span class="sxs-lookup"><span data-stu-id="b1a96-144">Move the cursor to the location to insert, apply the formatting desired, and write out the text.</span></span> <span data-ttu-id="b1a96-145">Le _sequenze di terminali virtuali_ sono consigliate per lo sviluppo nuovo e continuo.</span><span class="sxs-lookup"><span data-stu-id="b1a96-145">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="b1a96-146">Esempio</span><span class="sxs-lookup"><span data-stu-id="b1a96-146">Examples</span></span>

<span data-ttu-id="b1a96-147">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b1a96-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b1a96-148">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b1a96-148">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b1a96-149">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b1a96-149">Minimum supported client</span></span> | <span data-ttu-id="b1a96-150">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-150">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b1a96-151">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b1a96-151">Minimum supported server</span></span> | <span data-ttu-id="b1a96-152">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="b1a96-152">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b1a96-153">Intestazione</span><span class="sxs-lookup"><span data-stu-id="b1a96-153">Header</span></span> | <span data-ttu-id="b1a96-154">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b1a96-154">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b1a96-155">Libreria</span><span class="sxs-lookup"><span data-stu-id="b1a96-155">Library</span></span> | <span data-ttu-id="b1a96-156">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b1a96-156">Kernel32.lib</span></span> |
| <span data-ttu-id="b1a96-157">DLL</span><span class="sxs-lookup"><span data-stu-id="b1a96-157">DLL</span></span> | <span data-ttu-id="b1a96-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b1a96-158">Kernel32.dll</span></span> |
| <span data-ttu-id="b1a96-159">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="b1a96-159">Unicode and ANSI names</span></span> | <span data-ttu-id="b1a96-160">**WriteConsoleOutputW** (Unicode) e **WriteConsoleOutputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b1a96-160">**WriteConsoleOutputW** (Unicode) and **WriteConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b1a96-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b1a96-161">See also</span></span>

[<span data-ttu-id="b1a96-162">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="b1a96-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b1a96-163">**\_informazioni char**</span><span class="sxs-lookup"><span data-stu-id="b1a96-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="b1a96-164">**COORD**</span><span class="sxs-lookup"><span data-stu-id="b1a96-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="b1a96-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="b1a96-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="b1a96-166">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="b1a96-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="b1a96-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="b1a96-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="b1a96-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="b1a96-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="b1a96-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="b1a96-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="b1a96-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b1a96-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b1a96-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b1a96-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b1a96-172">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="b1a96-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="b1a96-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="b1a96-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="b1a96-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="b1a96-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)