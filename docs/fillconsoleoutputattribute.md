---
title: FillConsoleOutputAttribute (funzione)
description: Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039069"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="9ef5c-104">FillConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="9ef5c-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9ef5c-105">Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ef5c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9ef5c-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="9ef5c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="9ef5c-107">Parameters</span></span>

<span data-ttu-id="9ef5c-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9ef5c-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9ef5c-110">L'handle deve avere il diritto di accesso in **\_ scrittura generico** .</span><span class="sxs-lookup"><span data-stu-id="9ef5c-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="9ef5c-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="9ef5c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9ef5c-112">*wAttribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="9ef5c-113">Attributi da utilizzare durante la scrittura nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="9ef5c-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="9ef5c-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="9ef5c-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="9ef5c-116">Numero di celle di tipo carattere da impostare sugli attributi di colore specificati.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="9ef5c-117">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="9ef5c-118">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella i cui attributi devono essere impostati.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="9ef5c-119">*lpNumberOfAttrsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="9ef5c-120">Puntatore a una variabile che riceve il numero di celle di tipo carattere i cui attributi sono stati effettivamente impostati.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ef5c-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9ef5c-121">Return value</span></span>

<span data-ttu-id="9ef5c-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9ef5c-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9ef5c-124">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9ef5c-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9ef5c-125">Commenti</span><span class="sxs-lookup"><span data-stu-id="9ef5c-125">Remarks</span></span>

<span data-ttu-id="9ef5c-126">Se il numero di celle di tipo carattere i cui attributi devono essere impostati si estende oltre la fine della riga specificata nel buffer dello schermo della console, vengono impostate le celle della riga successiva.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="9ef5c-127">Se il numero di celle in cui scrivere si estende oltre la fine del buffer dello schermo della console, le celle vengono scritte fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="9ef5c-128">I valori di carattere nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="9ef5c-129">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** specifico.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="9ef5c-130">Il riempimento dell'area esterna alla finestra visualizzabile non è supportato ed è riservato per lo spazio della cronologia del terminale.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="9ef5c-131">Il riempimento di un'area visibile con nuovo testo o colore viene eseguito tramite **[lo scorrimento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)** , **[l'impostazione dei nuovi attributi](console-virtual-terminal-sequences.md#text-formatting)** , la scrittura del testo desiderato per l'area, la ripetizione dei caratteri, se necessario, per la durata dell'esecuzione del riempimento.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="9ef5c-132">È possibile che venga richiesto lo spostamento del cursore aggiuntivo seguito dalla scrittura del testo desiderato per riempire un'area rettangolare.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="9ef5c-133">Si prevede che l'applicazione client mantenga la propria memoria dello schermo e non sia in grado di eseguire query sullo stato remoto.</span><span class="sxs-lookup"><span data-stu-id="9ef5c-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="9ef5c-134">Altre informazioni sono reperibili nella documentazione della **[console classica rispetto al terminale virtuale](classic-vs-vt.md)** .</span><span class="sxs-lookup"><span data-stu-id="9ef5c-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ef5c-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9ef5c-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9ef5c-136">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9ef5c-136">Minimum supported client</span></span> | <span data-ttu-id="9ef5c-137">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ef5c-138">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="9ef5c-138">Minimum supported server</span></span> | <span data-ttu-id="9ef5c-139">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="9ef5c-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ef5c-140">Intestazione</span><span class="sxs-lookup"><span data-stu-id="9ef5c-140">Header</span></span> | <span data-ttu-id="9ef5c-141">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9ef5c-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9ef5c-142">Libreria</span><span class="sxs-lookup"><span data-stu-id="9ef5c-142">Library</span></span> | <span data-ttu-id="9ef5c-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9ef5c-143">Kernel32.lib</span></span> |
| <span data-ttu-id="9ef5c-144">DLL</span><span class="sxs-lookup"><span data-stu-id="9ef5c-144">DLL</span></span> | <span data-ttu-id="9ef5c-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9ef5c-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9ef5c-146">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9ef5c-146">See also</span></span>

[<span data-ttu-id="9ef5c-147">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="9ef5c-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9ef5c-148">**COORD**</span><span class="sxs-lookup"><span data-stu-id="9ef5c-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9ef5c-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="9ef5c-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="9ef5c-150">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="9ef5c-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="9ef5c-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="9ef5c-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="9ef5c-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="9ef5c-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
