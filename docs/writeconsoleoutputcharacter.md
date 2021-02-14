---
title: WriteConsoleOutputCharacter (funzione)
description: Copia un numero di caratteri in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 87d6e8768f55135536b1c0f752cc8f7827c643f1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359041"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="e785c-104">WriteConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="e785c-104">WriteConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e785c-105">Copia un numero di caratteri in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="e785c-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="e785c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e785c-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="e785c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="e785c-107">Parameters</span></span>

<span data-ttu-id="e785c-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e785c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e785c-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="e785c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="e785c-110">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="e785c-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="e785c-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e785c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e785c-112">*lpCharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e785c-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="e785c-113">Caratteri da scrivere nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="e785c-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="e785c-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e785c-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="e785c-115">Numero di caratteri da scrivere.</span><span class="sxs-lookup"><span data-stu-id="e785c-115">The number of characters to be written.</span></span>

<span data-ttu-id="e785c-116">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e785c-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="e785c-117">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella nel buffer dello schermo della console in cui verranno scritti i caratteri.</span><span class="sxs-lookup"><span data-stu-id="e785c-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="e785c-118">*lpNumberOfCharsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="e785c-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="e785c-119">Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="e785c-119">A pointer to a variable that receives the number of characters actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="e785c-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e785c-120">Return value</span></span>

<span data-ttu-id="e785c-121">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e785c-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e785c-122">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e785c-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e785c-123">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="e785c-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e785c-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e785c-124">Remarks</span></span>

<span data-ttu-id="e785c-125">Se il numero di caratteri da scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="e785c-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="e785c-126">Se il numero di caratteri da scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="e785c-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="e785c-127">I valori di attributo nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="e785c-127">The attribute values at the positions written to are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="e785c-128">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="e785c-128">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="e785c-129">Spostare il cursore nella posizione da inserire, applicare la formattazione desiderata e scrivere il testo da riempire.</span><span class="sxs-lookup"><span data-stu-id="e785c-129">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="e785c-130">Non esiste alcun equivalente per emettere testo in un'area senza applicare anche la formattazione dei colori attiva.</span><span class="sxs-lookup"><span data-stu-id="e785c-130">There is no equivalent to emit text to an area without also applying the active color formatting.</span></span> <span data-ttu-id="e785c-131">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi in cui è previsto che la singola applicazione client memorizzi il proprio stato disegnato per un'ulteriore manipolazione.</span><span class="sxs-lookup"><span data-stu-id="e785c-131">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="e785c-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e785c-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e785c-133">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e785c-133">Minimum supported client</span></span> | <span data-ttu-id="e785c-134">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="e785c-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e785c-135">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e785c-135">Minimum supported server</span></span> | <span data-ttu-id="e785c-136">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="e785c-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e785c-137">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e785c-137">Header</span></span> | <span data-ttu-id="e785c-138">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e785c-138">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e785c-139">Libreria</span><span class="sxs-lookup"><span data-stu-id="e785c-139">Library</span></span> | <span data-ttu-id="e785c-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e785c-140">Kernel32.lib</span></span> |
| <span data-ttu-id="e785c-141">DLL</span><span class="sxs-lookup"><span data-stu-id="e785c-141">DLL</span></span> | <span data-ttu-id="e785c-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e785c-142">Kernel32.dll</span></span> |
| <span data-ttu-id="e785c-143">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="e785c-143">Unicode and ANSI names</span></span> | <span data-ttu-id="e785c-144">**WriteConsoleOutputCharacterW** (Unicode) e **WriteConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e785c-144">**WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e785c-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e785c-145">See also</span></span>

[<span data-ttu-id="e785c-146">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="e785c-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e785c-147">**COORD**</span><span class="sxs-lookup"><span data-stu-id="e785c-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e785c-148">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="e785c-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="e785c-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="e785c-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="e785c-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="e785c-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="e785c-151">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="e785c-151">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="e785c-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="e785c-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="e785c-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e785c-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="e785c-154">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="e785c-154">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="e785c-155">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="e785c-155">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)