---
title: ScrollConsoleScreenBuffer (funzione)
description: Vedere informazioni di riferimento sulla funzione ScrollConsoleScreenBuffer, che consente di spostare un blocco di dati in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060337"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="0b8a8-104">ScrollConsoleScreenBuffer (funzione)</span><span class="sxs-lookup"><span data-stu-id="0b8a8-104">ScrollConsoleScreenBuffer function</span></span>


<span data-ttu-id="0b8a8-105">Sposta un blocco di dati in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="0b8a8-106">Gli effetti dello spostamento possono essere limitati specificando un rettangolo di ritaglio, in modo che il contenuto del buffer dello schermo della console all'esterno del rettangolo di ritaglio non sia modificato.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

<a name="syntax"></a><span data-ttu-id="0b8a8-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0b8a8-107">Syntax</span></span>
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a><span data-ttu-id="0b8a8-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="0b8a8-108">Parameters</span></span>
----------

<span data-ttu-id="0b8a8-109">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0b8a8-110">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="0b8a8-111">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="0b8a8-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0b8a8-112">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0b8a8-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0b8a8-113">*lpScrollRectangle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="0b8a8-114">Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console da spostare.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="0b8a8-115">*lpClipRectangle* \[ in, facoltativo\]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="0b8a8-116">Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console interessato dallo scorrimento.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="0b8a8-117">Questo puntatore può essere **null**.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="0b8a8-118">*dwDestinationOrigin* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="0b8a8-119">Struttura [**Coord**](coord-str.md) che specifica l'angolo superiore sinistro della nuova posizione del contenuto di *lpScrollRectangle* , in caratteri.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="0b8a8-120">*lpFill* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="0b8a8-121">Puntatore a una struttura [**di \_ informazioni char**](char-info-str.md) che specifica gli attributi di caratteri e colori da utilizzare per riempire le celle all'interno dell'intersezione tra *lpScrollRectangle* e *lpClipRectangle* che sono stati lasciati vuoti come risultato dello spostamento.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

<a name="return-value"></a><span data-ttu-id="0b8a8-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0b8a8-122">Return value</span></span>
------------

<span data-ttu-id="0b8a8-123">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0b8a8-124">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0b8a8-125">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0b8a8-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0b8a8-126">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0b8a8-126">Remarks</span></span>
-------

<span data-ttu-id="0b8a8-127">**ScrollConsoleScreenBuffer** copia il contenuto di un'area rettangolare di un buffer dello schermo, specificato dal parametro *lpScrollRectangle* , in un'altra area del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="0b8a8-128">Il rettangolo di destinazione ha le stesse dimensioni del rettangolo *lpScrollRectangle* con l'angolo superiore sinistro in corrispondenza delle coordinate specificate dal parametro *dwDestinationOrigin* .</span><span class="sxs-lookup"><span data-stu-id="0b8a8-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="0b8a8-129">Le parti di *lpScrollRectangle* che non si sovrappongono al rettangolo di destinazione vengono compilate con gli attributi di carattere e colore specificati dal parametro *lpFill* .</span><span class="sxs-lookup"><span data-stu-id="0b8a8-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="0b8a8-130">Il rettangolo di ritaglio si applica alle modifiche apportate sia nel rettangolo *lpScrollRectangle* che nel rettangolo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="0b8a8-131">Se, ad esempio, il rettangolo di ridimensionamento non include un'area che verrebbe compilata con il contenuto di *lpFill*, il contenuto originale dell'area viene lasciato invariato.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="0b8a8-132">Se le aree di scorrimento o di destinazione si estendono oltre le dimensioni del buffer dello schermo della console, vengono ritagliate.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="0b8a8-133">Ad esempio, se *lpScrollRectangle* è l'area contenuta da (0,0) e (19, 19) e *dwDestinationOrigin* è (10, 15), il rettangolo di destinazione è l'area contenuta da (10, 15) e (29, 34).</span><span class="sxs-lookup"><span data-stu-id="0b8a8-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="0b8a8-134">Tuttavia, se il buffer dello schermo della console ha una larghezza di 50 caratteri e 30 caratteri di altezza, il rettangolo di destinazione viene ritagliato in (10, 15) e (29, 29).</span><span class="sxs-lookup"><span data-stu-id="0b8a8-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="0b8a8-135">Anche le modifiche apportate al buffer dello schermo della console vengono ritagliate in base a *lpClipRectangle*, se il parametro specifica una struttura [\*\* \_ Rect di piccole dimensioni\*\*](small-rect-str.md) .</span><span class="sxs-lookup"><span data-stu-id="0b8a8-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="0b8a8-136">Se il rettangolo di ritaglio viene specificato come (0, 0) e (49, 19), vengono effettuate solo le modifiche che si verificano in tale area del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

<span data-ttu-id="0b8a8-137">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-137">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="0b8a8-138">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="0b8a8-138">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="0b8a8-139">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="0b8a8-139">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="0b8a8-140">Esempi</span><span class="sxs-lookup"><span data-stu-id="0b8a8-140">Examples</span></span>
--------

<span data-ttu-id="0b8a8-141">Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0b8a8-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0b8a8-142">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0b8a8-142">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0b8a8-143">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0b8a8-143">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0b8a8-144">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-144">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b8a8-145">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0b8a8-145">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0b8a8-146">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0b8a8-146">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0b8a8-147">Intestazione</span><span class="sxs-lookup"><span data-stu-id="0b8a8-147">Header</span></span></p></td>
<td><span data-ttu-id="0b8a8-148">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0b8a8-148">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b8a8-149">Libreria</span><span class="sxs-lookup"><span data-stu-id="0b8a8-149">Library</span></span></p></td>
<td><span data-ttu-id="0b8a8-150">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0b8a8-150">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0b8a8-151">DLL</span><span class="sxs-lookup"><span data-stu-id="0b8a8-151">DLL</span></span></p></td>
<td><span data-ttu-id="0b8a8-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0b8a8-152">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0b8a8-153">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="0b8a8-153">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="0b8a8-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) e <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="0b8a8-154"><strong>ScrollConsoleScreenBufferW</strong> (Unicode) and <strong>ScrollConsoleScreenBufferA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0b8a8-155"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0b8a8-155"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0b8a8-156">**\_informazioni char**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="0b8a8-157">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="0b8a8-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0b8a8-158">**COORD**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="0b8a8-159">Scorrimento del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="0b8a8-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="0b8a8-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0b8a8-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0b8a8-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="0b8a8-163">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="0b8a8-163">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




