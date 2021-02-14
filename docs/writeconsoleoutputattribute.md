---
title: WriteConsoleOutputAttribute (funzione)
description: Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4c940243b8367e2f66923c14ffa90de7c9a384b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357761"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="12e73-104">WriteConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="12e73-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="12e73-105">Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="12e73-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="12e73-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="12e73-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="12e73-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="12e73-107">Parameters</span></span>

<span data-ttu-id="12e73-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="12e73-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="12e73-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="12e73-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="12e73-110">L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="12e73-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="12e73-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="12e73-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="12e73-112">*lpAttribute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="12e73-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="12e73-113">Attributi da utilizzare durante la scrittura nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="12e73-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="12e73-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="12e73-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="12e73-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="12e73-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="12e73-116">Numero di celle di caratteri del buffer dello schermo in cui verranno copiati gli attributi.</span><span class="sxs-lookup"><span data-stu-id="12e73-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="12e73-117">*dwWriteCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="12e73-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="12e73-118">Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella nel buffer dello schermo della console in cui verranno scritti gli attributi.</span><span class="sxs-lookup"><span data-stu-id="12e73-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="12e73-119">*lpNumberOfAttrsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="12e73-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="12e73-120">Puntatore a una variabile che riceve il numero di attributi effettivamente scritti nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="12e73-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="12e73-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="12e73-121">Return value</span></span>

<span data-ttu-id="12e73-122">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="12e73-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="12e73-123">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="12e73-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="12e73-124">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="12e73-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="12e73-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="12e73-125">Remarks</span></span>

<span data-ttu-id="12e73-126">Se il numero di attributi da scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, gli attributi vengono scritti nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="12e73-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="12e73-127">Se il numero di attributi da scrivere si estende oltre la fine del buffer dello schermo della console, gli attributi vengono scritti fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="12e73-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="12e73-128">I valori di carattere nelle posizioni scritte in non vengono modificati.</span><span class="sxs-lookup"><span data-stu-id="12e73-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="12e73-129">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="12e73-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="12e73-130">Spostare il cursore nella posizione da inserire, applicare la formattazione desiderata e scrivere il testo da riempire.</span><span class="sxs-lookup"><span data-stu-id="12e73-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="12e73-131">Non esiste alcun equivalente per applicare il colore a un'area senza emettere anche testo.</span><span class="sxs-lookup"><span data-stu-id="12e73-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="12e73-132">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi in cui è previsto che la singola applicazione client memorizzi il proprio stato disegnato per un'ulteriore manipolazione.</span><span class="sxs-lookup"><span data-stu-id="12e73-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="12e73-133">Requisiti</span><span class="sxs-lookup"><span data-stu-id="12e73-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="12e73-134">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="12e73-134">Minimum supported client</span></span> | <span data-ttu-id="12e73-135">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="12e73-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="12e73-136">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="12e73-136">Minimum supported server</span></span> | <span data-ttu-id="12e73-137">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="12e73-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="12e73-138">Intestazione</span><span class="sxs-lookup"><span data-stu-id="12e73-138">Header</span></span> | <span data-ttu-id="12e73-139">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="12e73-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="12e73-140">Libreria</span><span class="sxs-lookup"><span data-stu-id="12e73-140">Library</span></span> | <span data-ttu-id="12e73-141">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="12e73-141">Kernel32.lib</span></span> |
| <span data-ttu-id="12e73-142">DLL</span><span class="sxs-lookup"><span data-stu-id="12e73-142">DLL</span></span> | <span data-ttu-id="12e73-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="12e73-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="12e73-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12e73-144">See also</span></span>

[<span data-ttu-id="12e73-145">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="12e73-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="12e73-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="12e73-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="12e73-147">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="12e73-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="12e73-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="12e73-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="12e73-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="12e73-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="12e73-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="12e73-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="12e73-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="12e73-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="12e73-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="12e73-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)