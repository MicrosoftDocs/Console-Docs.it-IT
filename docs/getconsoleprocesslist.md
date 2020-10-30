---
title: GetConsoleProcessList (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleProcessList, che recupera un elenco dei processi collegati alla console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bfc16edccb2f1be2b22c81992800d8f62d86cf4f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037984"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="c9092-104">GetConsoleProcessList (funzione)</span><span class="sxs-lookup"><span data-stu-id="c9092-104">GetConsoleProcessList function</span></span>

<span data-ttu-id="c9092-105">Recupera un elenco dei processi collegati alla console corrente.</span><span class="sxs-lookup"><span data-stu-id="c9092-105">Retrieves a list of the processes attached to the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9092-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9092-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a><span data-ttu-id="c9092-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="c9092-107">Parameters</span></span>

<span data-ttu-id="c9092-108">*lpdwProcessList* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="c9092-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="c9092-109">Puntatore a un buffer che riceve una matrice di identificatori di processo al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="c9092-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="c9092-110">Deve essere un buffer valido e non può essere `NULL` .</span><span class="sxs-lookup"><span data-stu-id="c9092-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="c9092-111">Il buffer deve avere spazio per ricevere almeno 1 ID processo restituito.</span><span class="sxs-lookup"><span data-stu-id="c9092-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="c9092-112">*dwProcessCount* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c9092-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="c9092-113">Numero massimo di identificatori di processo che è possibile archiviare nel buffer *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="c9092-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="c9092-114">Deve essere maggiore di 0.</span><span class="sxs-lookup"><span data-stu-id="c9092-114">This must be greater than 0.</span></span>

## <a name="return-value"></a><span data-ttu-id="c9092-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c9092-115">Return value</span></span>

<span data-ttu-id="c9092-116">Se la funzione ha esito positivo, il valore restituito è minore o uguale a *dwProcessCount* e rappresenta il numero di identificatori di processo archiviati nel buffer *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="c9092-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="c9092-117">Se il buffer è troppo piccolo per conservare tutti gli identificatori di processo validi, il valore restituito è il numero necessario di elementi di matrice.</span><span class="sxs-lookup"><span data-stu-id="c9092-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="c9092-118">La funzione non avrà archiviato identificatori nel buffer.</span><span class="sxs-lookup"><span data-stu-id="c9092-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="c9092-119">In questa situazione, utilizzare il valore restituito per allocare un buffer sufficientemente grande da archiviare l'intero elenco e chiamare di nuovo la funzione.</span><span class="sxs-lookup"><span data-stu-id="c9092-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="c9092-120">Se il valore restituito è zero, la funzione non è riuscita perché a ogni console è associato almeno un processo.</span><span class="sxs-lookup"><span data-stu-id="c9092-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="c9092-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c9092-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="c9092-122">Se `NULL` è stato specificato un elenco di processi o il numero di processi è pari a 0, la chiamata restituirà 0 e restituirà `GetLastError` `ERROR_INVALID_PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="c9092-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="c9092-123">Fornire un buffer di almeno un elemento per chiamare questa funzione.</span><span class="sxs-lookup"><span data-stu-id="c9092-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="c9092-124">Allocare un buffer più grande e chiamare di nuovo se il codice restituito è più grande della lunghezza del buffer fornito.</span><span class="sxs-lookup"><span data-stu-id="c9092-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9092-125">Commenti</span><span class="sxs-lookup"><span data-stu-id="c9092-125">Remarks</span></span>

<span data-ttu-id="c9092-126">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c9092-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c9092-127">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c9092-127">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a><span data-ttu-id="c9092-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c9092-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c9092-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c9092-129">Minimum supported client</span></span> | <span data-ttu-id="c9092-130">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="c9092-130">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="c9092-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="c9092-131">Minimum supported server</span></span> | <span data-ttu-id="c9092-132">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="c9092-132">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c9092-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="c9092-133">Header</span></span> | <span data-ttu-id="c9092-134">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c9092-134">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c9092-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="c9092-135">Library</span></span> | <span data-ttu-id="c9092-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c9092-136">Kernel32.lib</span></span> |
| <span data-ttu-id="c9092-137">DLL</span><span class="sxs-lookup"><span data-stu-id="c9092-137">DLL</span></span> | <span data-ttu-id="c9092-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c9092-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c9092-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c9092-139">See also</span></span>

[<span data-ttu-id="c9092-140">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="c9092-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="c9092-141">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="c9092-141">Console Functions</span></span>](console-functions.md)
