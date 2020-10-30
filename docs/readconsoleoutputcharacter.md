---
title: ReadConsoleOutputCharacter (funzione)
description: Copia un numero di caratteri dalle celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037724"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="08f0d-104">ReadConsoleOutputCharacter (funzione)</span><span class="sxs-lookup"><span data-stu-id="08f0d-104">ReadConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="08f0d-105">Copia un numero di caratteri dalle celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="08f0d-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="08f0d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="08f0d-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a><span data-ttu-id="08f0d-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="08f0d-107">Parameters</span></span>

<span data-ttu-id="08f0d-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="08f0d-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="08f0d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="08f0d-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="08f0d-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="08f0d-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="08f0d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="08f0d-112">*lpCharacter* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="08f0d-113">Puntatore a un buffer che riceve i caratteri letti dal buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="08f0d-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="08f0d-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="08f0d-115">Numero di celle di caratteri del buffer dello schermo da cui eseguire la lettura.</span><span class="sxs-lookup"><span data-stu-id="08f0d-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="08f0d-116">La dimensione del buffer a cui punta il parametro *lpCharacter* deve essere `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="08f0d-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="08f0d-117">*dwReadCoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="08f0d-118">Coordinate della prima cella nel buffer dello schermo della console da cui leggere, in caratteri.</span><span class="sxs-lookup"><span data-stu-id="08f0d-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="08f0d-119">Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.</span><span class="sxs-lookup"><span data-stu-id="08f0d-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="08f0d-120">*lpNumberOfCharsRead* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="08f0d-121">Puntatore a una variabile che riceve il numero di caratteri effettivamente letti.</span><span class="sxs-lookup"><span data-stu-id="08f0d-121">A pointer to a variable that receives the number of characters actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="08f0d-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="08f0d-122">Return value</span></span>

<span data-ttu-id="08f0d-123">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="08f0d-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="08f0d-124">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="08f0d-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="08f0d-125">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="08f0d-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="08f0d-126">Commenti</span><span class="sxs-lookup"><span data-stu-id="08f0d-126">Remarks</span></span>

<span data-ttu-id="08f0d-127">Se il numero di caratteri da leggere da si estende oltre la fine della riga del buffer dello schermo specificata, i caratteri vengono letti dalla riga successiva.</span><span class="sxs-lookup"><span data-stu-id="08f0d-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="08f0d-128">Se il numero di caratteri da leggere da si estende oltre la fine del buffer dello schermo della console, vengono letti i caratteri fino alla fine del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="08f0d-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="08f0d-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="08f0d-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="08f0d-130">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="08f0d-130">Minimum supported client</span></span> | <span data-ttu-id="08f0d-131">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="08f0d-132">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="08f0d-132">Minimum supported server</span></span> | <span data-ttu-id="08f0d-133">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="08f0d-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="08f0d-134">Intestazione</span><span class="sxs-lookup"><span data-stu-id="08f0d-134">Header</span></span> | <span data-ttu-id="08f0d-135">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="08f0d-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="08f0d-136">Libreria</span><span class="sxs-lookup"><span data-stu-id="08f0d-136">Library</span></span> | <span data-ttu-id="08f0d-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="08f0d-137">Kernel32.lib</span></span> |
| <span data-ttu-id="08f0d-138">DLL</span><span class="sxs-lookup"><span data-stu-id="08f0d-138">DLL</span></span> | <span data-ttu-id="08f0d-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="08f0d-139">Kernel32.dll</span></span> |
| <span data-ttu-id="08f0d-140">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="08f0d-140">Unicode and ANSI names</span></span> | <span data-ttu-id="08f0d-141">**ReadConsoleOutputCharacterW** (Unicode) e **ReadConsoleOutputCharacterA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="08f0d-141">**ReadConsoleOutputCharacterW** (Unicode) and **ReadConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="08f0d-142">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="08f0d-142">See also</span></span>

[<span data-ttu-id="08f0d-143">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="08f0d-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="08f0d-144">**COORD**</span><span class="sxs-lookup"><span data-stu-id="08f0d-144">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="08f0d-145">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="08f0d-145">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="08f0d-146">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="08f0d-146">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="08f0d-147">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="08f0d-147">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="08f0d-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="08f0d-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="08f0d-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="08f0d-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="08f0d-150">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="08f0d-150">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="08f0d-151">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="08f0d-151">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="08f0d-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="08f0d-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
