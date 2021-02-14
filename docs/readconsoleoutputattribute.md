---
title: ReadConsoleOutputAttribute (funzione)
description: Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bf140d9f6721196caa5f62a064ed434554067d62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358701"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="ceb79-104">ReadConsoleOutputAttribute (funzione)</span><span class="sxs-lookup"><span data-stu-id="ceb79-104">ReadConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ceb79-105">Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="ceb79-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="ceb79-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ceb79-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a><span data-ttu-id="ceb79-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ceb79-107">Parameters</span></span>

<span data-ttu-id="ceb79-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ceb79-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="ceb79-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ceb79-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="ceb79-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ceb79-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ceb79-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ceb79-112">*lpAttribute* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="ceb79-113">Puntatore a un buffer che riceve gli attributi utilizzati dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="ceb79-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="ceb79-114">Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="ceb79-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="ceb79-115">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="ceb79-116">Numero di celle di caratteri del buffer dello schermo da cui eseguire la lettura.</span><span class="sxs-lookup"><span data-stu-id="ceb79-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="ceb79-117">La dimensione del buffer a cui punta il parametro *lpAttribute* deve essere `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="ceb79-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="ceb79-118">*dwReadCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="ceb79-119">Coordinate della prima cella nel buffer dello schermo della console da cui leggere, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="ceb79-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="ceb79-120">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="ceb79-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="ceb79-121">*lpNumberOfAttrsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="ceb79-122">Puntatore a una variabile che riceve il numero di attributi effettivamente letti.</span><span class="sxs-lookup"><span data-stu-id="ceb79-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="ceb79-123">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ceb79-123">Return value</span></span>

<span data-ttu-id="ceb79-124">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="ceb79-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ceb79-125">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="ceb79-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ceb79-126">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="ceb79-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ceb79-127">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ceb79-127">Remarks</span></span>

<span data-ttu-id="ceb79-128">Se il numero di attributi da leggere da si estende oltre la fine della riga del buffer dello schermo specificata, gli attributi vengono letti dalla riga successiva.</span><span class="sxs-lookup"><span data-stu-id="ceb79-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="ceb79-129">Se il numero di attributi da leggere da si estende oltre la fine del buffer dello schermo della console, vengono letti gli attributi fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="ceb79-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ceb79-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ceb79-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ceb79-131">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ceb79-131">Minimum supported client</span></span> | <span data-ttu-id="ceb79-132">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ceb79-133">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ceb79-133">Minimum supported server</span></span> | <span data-ttu-id="ceb79-134">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="ceb79-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ceb79-135">Intestazione</span><span class="sxs-lookup"><span data-stu-id="ceb79-135">Header</span></span> | <span data-ttu-id="ceb79-136">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ceb79-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ceb79-137">Libreria</span><span class="sxs-lookup"><span data-stu-id="ceb79-137">Library</span></span> | <span data-ttu-id="ceb79-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ceb79-138">Kernel32.lib</span></span> |
| <span data-ttu-id="ceb79-139">DLL</span><span class="sxs-lookup"><span data-stu-id="ceb79-139">DLL</span></span> | <span data-ttu-id="ceb79-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ceb79-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ceb79-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ceb79-141">See also</span></span>

[<span data-ttu-id="ceb79-142">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="ceb79-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ceb79-143">**COORD**</span><span class="sxs-lookup"><span data-stu-id="ceb79-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ceb79-144">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="ceb79-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ceb79-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ceb79-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ceb79-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ceb79-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ceb79-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ceb79-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ceb79-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ceb79-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="ceb79-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ceb79-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)