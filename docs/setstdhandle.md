---
title: SetStdHandle (funzione)
description: Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039299"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="4c816-104">SetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="4c816-104">SetStdHandle function</span></span>

<span data-ttu-id="4c816-105">Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="4c816-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="4c816-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4c816-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="4c816-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4c816-107">Parameters</span></span>

<span data-ttu-id="4c816-108">*nStdHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4c816-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="4c816-109">Dispositivo standard per il quale deve essere impostato l'handle.</span><span class="sxs-lookup"><span data-stu-id="4c816-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="4c816-110">Questo parametro può essere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="4c816-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="4c816-111">Valore</span><span class="sxs-lookup"><span data-stu-id="4c816-111">Value</span></span> | <span data-ttu-id="4c816-112">Significato</span><span class="sxs-lookup"><span data-stu-id="4c816-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="4c816-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="4c816-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="4c816-114">Dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="4c816-114">The standard input device.</span></span> <span data-ttu-id="4c816-115">Inizialmente, si tratta del buffer di input della console `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="4c816-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="4c816-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="4c816-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="4c816-117">Dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="4c816-117">The standard output device.</span></span> <span data-ttu-id="4c816-118">Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="4c816-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="4c816-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="4c816-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="4c816-120">Dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="4c816-120">The standard error device.</span></span> <span data-ttu-id="4c816-121">Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="4c816-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="4c816-122">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4c816-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="4c816-123">Handle per il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="4c816-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c816-124">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4c816-124">Return value</span></span>

<span data-ttu-id="4c816-125">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="4c816-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4c816-126">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="4c816-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4c816-127">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c816-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4c816-128">Commenti</span><span class="sxs-lookup"><span data-stu-id="4c816-128">Remarks</span></span>

<span data-ttu-id="4c816-129">Gli handle standard di un processo potrebbero essere stati reindirizzati da una chiamata a **SetStdHandle** , nel qual caso [**GetStdHandle**](getstdhandle.md) restituirà l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="4c816-129">The standard handles of a process may have been redirected by a call to **SetStdHandle** , in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="4c816-130">Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="4c816-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="4c816-131">Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="4c816-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="4c816-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="4c816-132">Examples</span></span>

<span data-ttu-id="4c816-133">Per un esempio, vedere [creazione di un processo figlio con input e output reindirizzati](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="4c816-133">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

## <a name="requirements"></a><span data-ttu-id="4c816-134">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4c816-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4c816-135">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4c816-135">Minimum supported client</span></span> | <span data-ttu-id="4c816-136">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="4c816-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c816-137">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4c816-137">Minimum supported server</span></span> | <span data-ttu-id="4c816-138">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4c816-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c816-139">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4c816-139">Header</span></span> | <span data-ttu-id="4c816-140">ProcessEnv. h (tramite Winbase. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c816-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="4c816-141">Libreria</span><span class="sxs-lookup"><span data-stu-id="4c816-141">Library</span></span> | <span data-ttu-id="4c816-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c816-142">Kernel32.lib</span></span> |
| <span data-ttu-id="4c816-143">DLL</span><span class="sxs-lookup"><span data-stu-id="4c816-143">DLL</span></span> | <span data-ttu-id="4c816-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c816-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4c816-145">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4c816-145">See also</span></span>

[<span data-ttu-id="4c816-146">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="4c816-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c816-147">Handle della console</span><span class="sxs-lookup"><span data-stu-id="4c816-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="4c816-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="4c816-148">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="4c816-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="4c816-149">**GetStdHandle**</span></span>](getstdhandle.md)
