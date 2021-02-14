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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358511"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="b4663-104">SetStdHandle (funzione)</span><span class="sxs-lookup"><span data-stu-id="b4663-104">SetStdHandle function</span></span>

<span data-ttu-id="b4663-105">Imposta l'handle per il dispositivo standard specificato (input standard, output standard o errore standard).</span><span class="sxs-lookup"><span data-stu-id="b4663-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="b4663-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b4663-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="b4663-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="b4663-107">Parameters</span></span>

<span data-ttu-id="b4663-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b4663-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="b4663-109">Dispositivo standard per il quale deve essere impostato l'handle.</span><span class="sxs-lookup"><span data-stu-id="b4663-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="b4663-110">Questo parametro può avere uno dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="b4663-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="b4663-111">Valore</span><span class="sxs-lookup"><span data-stu-id="b4663-111">Value</span></span> | <span data-ttu-id="b4663-112">Significato</span><span class="sxs-lookup"><span data-stu-id="b4663-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="b4663-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="b4663-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="b4663-114">Il dispositivo di input standard.</span><span class="sxs-lookup"><span data-stu-id="b4663-114">The standard input device.</span></span> <span data-ttu-id="b4663-115">Inizialmente si tratta del buffer di input della console, ovvero `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="b4663-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="b4663-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="b4663-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="b4663-117">Il dispositivo di output standard.</span><span class="sxs-lookup"><span data-stu-id="b4663-117">The standard output device.</span></span> <span data-ttu-id="b4663-118">Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="b4663-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="b4663-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="b4663-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="b4663-120">Il dispositivo di errore standard.</span><span class="sxs-lookup"><span data-stu-id="b4663-120">The standard error device.</span></span> <span data-ttu-id="b4663-121">Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="b4663-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="b4663-122">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b4663-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="b4663-123">Handle per il dispositivo standard.</span><span class="sxs-lookup"><span data-stu-id="b4663-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="b4663-124">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b4663-124">Return value</span></span>

<span data-ttu-id="b4663-125">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="b4663-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b4663-126">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="b4663-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b4663-127">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="b4663-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b4663-128">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b4663-128">Remarks</span></span>

<span data-ttu-id="b4663-129">Gli handle standard di un processo potrebbero essere stati reindirizzati da una chiamata a **SetStdHandle**, nel qual caso [**GetStdHandle**](getstdhandle.md) restituirà l'handle reindirizzato.</span><span class="sxs-lookup"><span data-stu-id="b4663-129">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="b4663-130">Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) per ottenere un handle per il buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="b4663-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="b4663-131">Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo della console.</span><span class="sxs-lookup"><span data-stu-id="b4663-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="b4663-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="b4663-132">Examples</span></span>

<span data-ttu-id="b4663-133">Per un esempio, vedere [creazione di un processo figlio con input e output reindirizzati](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="b4663-133">For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span></span>

## <a name="requirements"></a><span data-ttu-id="b4663-134">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b4663-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b4663-135">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b4663-135">Minimum supported client</span></span> | <span data-ttu-id="b4663-136">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="b4663-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b4663-137">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b4663-137">Minimum supported server</span></span> | <span data-ttu-id="b4663-138">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="b4663-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b4663-139">Intestazione</span><span class="sxs-lookup"><span data-stu-id="b4663-139">Header</span></span> | <span data-ttu-id="b4663-140">ProcessEnv.h (tramite Winbase.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="b4663-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="b4663-141">Libreria</span><span class="sxs-lookup"><span data-stu-id="b4663-141">Library</span></span> | <span data-ttu-id="b4663-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b4663-142">Kernel32.lib</span></span> |
| <span data-ttu-id="b4663-143">DLL</span><span class="sxs-lookup"><span data-stu-id="b4663-143">DLL</span></span> | <span data-ttu-id="b4663-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b4663-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b4663-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4663-145">See also</span></span>

[<span data-ttu-id="b4663-146">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="b4663-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b4663-147">Handle della console</span><span class="sxs-lookup"><span data-stu-id="b4663-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="b4663-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="b4663-148">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="b4663-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="b4663-149">**GetStdHandle**</span></span>](getstdhandle.md)