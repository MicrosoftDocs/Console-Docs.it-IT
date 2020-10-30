---
title: ReadConsoleOutput (funzione)
description: Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e scrive i dati nel buffer di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 0ce2a5a62ee7719d0184247c9ef3327850e12c1b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037759"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="b0f6a-104">ReadConsoleOutput (funzione)</span><span class="sxs-lookup"><span data-stu-id="b0f6a-104">ReadConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b0f6a-105">Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e la funzione scrive i dati in un blocco rettangolare in una posizione specificata nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0f6a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b0f6a-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a><span data-ttu-id="b0f6a-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="b0f6a-107">Parameters</span></span>

<span data-ttu-id="b0f6a-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b0f6a-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="b0f6a-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b0f6a-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b0f6a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b0f6a-112">*lpBuffer* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="b0f6a-113">Puntatore a un buffer di destinazione che riceve i dati letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="b0f6a-114">Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [**\_ informazioni char**](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="b0f6a-115">*dwBufferSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="b0f6a-116">Dimensioni del parametro *lpBuffer* , in celle di tipo carattere.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="b0f6a-117">Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="b0f6a-118">*dwBufferCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="b0f6a-119">Coordinate della cella superiore sinistra nel parametro *lpBuffer* che riceve i dati letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="b0f6a-120">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="b0f6a-121">*lpReadRegion* \[ in uscita\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="b0f6a-122">Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="b0f6a-123">In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console da cui la funzione deve essere letta.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="b0f6a-124">Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-124">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0f6a-125">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b0f6a-125">Return value</span></span>

<span data-ttu-id="b0f6a-126">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b0f6a-127">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b0f6a-128">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b0f6a-128">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b0f6a-129">Commenti</span><span class="sxs-lookup"><span data-stu-id="b0f6a-129">Remarks</span></span>

<span data-ttu-id="b0f6a-130">**ReadConsoleOutput** considera il buffer dello schermo della console e il buffer di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere).</span><span class="sxs-lookup"><span data-stu-id="b0f6a-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="b0f6a-131">Il rettangolo a cui punta il parametro *lpReadRegion* specifica le dimensioni e la posizione del blocco da leggere dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="b0f6a-132">Un rettangolo di destinazione della stessa dimensione si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="b0f6a-133">I dati letti dalle celle del rettangolo di origine buffer dello schermo della console vengono copiati nelle celle corrispondenti nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="b0f6a-134">Se la cella corrispondente non rientra nei limiti del rettangolo del buffer di destinazione (le cui dimensioni sono specificate dal parametro *dwBufferSize* ), i dati non vengono copiati.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="b0f6a-135">Le celle del buffer di destinazione corrispondenti alle coordinate che non rientrano nei limiti del buffer dello schermo della console rimangono invariate.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="b0f6a-136">In altre parole, queste sono le celle per le quali non sono disponibili dati del buffer dello schermo da leggere.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="b0f6a-137">Prima della restituzione di **ReadConsoleOutput** , imposta i membri della struttura a cui punta il parametro *lpReadRegion* sul rettangolo del buffer dello schermo effettivo le cui celle sono state copiate nel buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="b0f6a-138">Questo rettangolo riflette le celle del rettangolo di origine per cui esiste una cella corrispondente nel buffer di destinazione, perché **ReadConsoleOutput** Ritaglia le dimensioni del rettangolo di origine per adattarsi ai limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="b0f6a-139">Se il rettangolo specificato da *lpReadRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di destinazione, non vengono copiati dati.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="b0f6a-140">In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpReadRegion* , in modo tale che il membro **destro** sia minore della **sinistra** o che il membro **inferiore** sia minore della **parte superiore** .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left** , or the **Bottom** member is less than the **Top** .</span></span> <span data-ttu-id="b0f6a-141">Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="b0f6a-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="b0f6a-142">La funzione **ReadConsoleOutput** non ha alcun effetto sulla posizione del cursore del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="b0f6a-143">Il contenuto del buffer dello schermo della console non viene modificato dalla funzione.</span><span class="sxs-lookup"><span data-stu-id="b0f6a-143">The contents of the console screen buffer are not changed by the function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="examples"></a><span data-ttu-id="b0f6a-144">Esempio</span><span class="sxs-lookup"><span data-stu-id="b0f6a-144">Examples</span></span>

<span data-ttu-id="b0f6a-145">Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b0f6a-145">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b0f6a-146">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b0f6a-146">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b0f6a-147">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b0f6a-147">Minimum supported client</span></span> | <span data-ttu-id="b0f6a-148">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-148">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0f6a-149">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b0f6a-149">Minimum supported server</span></span> | <span data-ttu-id="b0f6a-150">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="b0f6a-150">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0f6a-151">Intestazione</span><span class="sxs-lookup"><span data-stu-id="b0f6a-151">Header</span></span> | <span data-ttu-id="b0f6a-152">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b0f6a-152">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b0f6a-153">Libreria</span><span class="sxs-lookup"><span data-stu-id="b0f6a-153">Library</span></span> | <span data-ttu-id="b0f6a-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b0f6a-154">Kernel32.lib</span></span> |
| <span data-ttu-id="b0f6a-155">DLL</span><span class="sxs-lookup"><span data-stu-id="b0f6a-155">DLL</span></span> | <span data-ttu-id="b0f6a-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b0f6a-156">Kernel32.dll</span></span> |
| <span data-ttu-id="b0f6a-157">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="b0f6a-157">Unicode and ANSI names</span></span> | <span data-ttu-id="b0f6a-158">**ReadConsoleOutputW** (Unicode) e **ReadConsoleOutputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b0f6a-158">**ReadConsoleOutputW** (Unicode) and **ReadConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b0f6a-159">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b0f6a-159">See also</span></span>

[<span data-ttu-id="b0f6a-160">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="b0f6a-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b0f6a-161">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="b0f6a-161">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="b0f6a-162">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-162">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="b0f6a-163">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-163">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="b0f6a-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b0f6a-165">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-165">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b0f6a-166">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-166">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="b0f6a-167">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-167">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="b0f6a-168">**\_informazioni char**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-168">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="b0f6a-169">**COORD**</span><span class="sxs-lookup"><span data-stu-id="b0f6a-169">**COORD**</span></span>](coord-str.md)
