---
title: FillConsoleOutputCharacter (funzione)
description: Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 95efbcc261943a2986fe6fbb1f3d54aaae1b2d2b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357511"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="88ba3-104">FillConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="88ba3-104">FillConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="88ba3-105">Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.</span><span class="sxs-lookup"><span data-stu-id="88ba3-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

## <a name="syntax"></a><span data-ttu-id="88ba3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="88ba3-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="88ba3-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="88ba3-107">Parameters</span></span>

<span data-ttu-id="88ba3-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="88ba3-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="88ba3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="88ba3-110">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="88ba3-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="88ba3-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="88ba3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="88ba3-112">*cCharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="88ba3-113">Carattere da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="88ba3-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="88ba3-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="88ba3-115">Numero di celle di caratteri in cui deve essere scritto il carattere.</span><span class="sxs-lookup"><span data-stu-id="88ba3-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="88ba3-116">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="88ba3-117">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella in cui deve essere scritto il carattere.</span><span class="sxs-lookup"><span data-stu-id="88ba3-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="88ba3-118">*lpNumberOfCharsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="88ba3-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="88ba3-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="88ba3-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="88ba3-120">Return value</span></span>

<span data-ttu-id="88ba3-121">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="88ba3-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="88ba3-122">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="88ba3-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="88ba3-123">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="88ba3-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="88ba3-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="88ba3-124">Remarks</span></span>

<span data-ttu-id="88ba3-125">Se il numero di caratteri in cui scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="88ba3-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="88ba3-126">Se il numero di caratteri in cui scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="88ba3-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="88ba3-127">I valori di attributo nelle posizioni scritte non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="88ba3-127">The attribute values at the positions written are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="88ba3-128">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** specifico.</span><span class="sxs-lookup"><span data-stu-id="88ba3-128">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="88ba3-129">Il riempimento dell'area esterna alla finestra visualizzabile non è supportato ed è riservato per lo spazio della cronologia del terminale.</span><span class="sxs-lookup"><span data-stu-id="88ba3-129">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="88ba3-130">Il riempimento di un'area visibile con nuovo testo o colore viene eseguito tramite **[lo scorrimento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)**, **[l'impostazione dei nuovi attributi](console-virtual-terminal-sequences.md#text-formatting)**, la scrittura del testo desiderato per l'area, la ripetizione dei caratteri, se necessario, per la durata dell'esecuzione del riempimento.</span><span class="sxs-lookup"><span data-stu-id="88ba3-130">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="88ba3-131">È possibile che venga richiesto lo spostamento del cursore aggiuntivo seguito dalla scrittura del testo desiderato per riempire un'area rettangolare.</span><span class="sxs-lookup"><span data-stu-id="88ba3-131">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="88ba3-132">Si prevede che l'applicazione client mantenga la propria memoria dello schermo e non sia in grado di eseguire query sullo stato remoto.</span><span class="sxs-lookup"><span data-stu-id="88ba3-132">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="88ba3-133">Altre informazioni sono reperibili nella documentazione della **[console classica rispetto al terminale virtuale](classic-vs-vt.md)** .</span><span class="sxs-lookup"><span data-stu-id="88ba3-133">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="88ba3-134">Requisiti</span><span class="sxs-lookup"><span data-stu-id="88ba3-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="88ba3-135">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="88ba3-135">Minimum supported client</span></span> | <span data-ttu-id="88ba3-136">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="88ba3-137">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="88ba3-137">Minimum supported server</span></span> | <span data-ttu-id="88ba3-138">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="88ba3-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="88ba3-139">Intestazione</span><span class="sxs-lookup"><span data-stu-id="88ba3-139">Header</span></span> | <span data-ttu-id="88ba3-140">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="88ba3-140">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="88ba3-141">Libreria</span><span class="sxs-lookup"><span data-stu-id="88ba3-141">Library</span></span> | <span data-ttu-id="88ba3-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="88ba3-142">Kernel32.lib</span></span> |
| <span data-ttu-id="88ba3-143">DLL</span><span class="sxs-lookup"><span data-stu-id="88ba3-143">DLL</span></span> | <span data-ttu-id="88ba3-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="88ba3-144">Kernel32.dll</span></span> |
| <span data-ttu-id="88ba3-145">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="88ba3-145">Unicode and ANSI names</span></span> | <span data-ttu-id="88ba3-146">**FillConsoleOutputCharacterW** (Unicode) e **FillConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="88ba3-146">**FillConsoleOutputCharacterW** (Unicode) and **FillConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="88ba3-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88ba3-147">See also</span></span>

[<span data-ttu-id="88ba3-148">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="88ba3-148">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="88ba3-149">**COORD**</span><span class="sxs-lookup"><span data-stu-id="88ba3-149">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="88ba3-150">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="88ba3-150">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="88ba3-151">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="88ba3-151">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="88ba3-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="88ba3-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="88ba3-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="88ba3-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="88ba3-154">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="88ba3-154">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)