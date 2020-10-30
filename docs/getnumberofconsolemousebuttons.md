---
title: GetNumberOfConsoleMouseButtons (funzione)
description: Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037829"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="77b81-104">GetNumberOfConsoleMouseButtons (funzione)</span><span class="sxs-lookup"><span data-stu-id="77b81-104">GetNumberOfConsoleMouseButtons function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="77b81-105">Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.</span><span class="sxs-lookup"><span data-stu-id="77b81-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="77b81-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="77b81-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a><span data-ttu-id="77b81-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="77b81-107">Parameters</span></span>

<span data-ttu-id="77b81-108">*lpNumberOfMouseButtons* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="77b81-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="77b81-109">Puntatore a una variabile che riceve il numero di pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="77b81-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

## <a name="return-value"></a><span data-ttu-id="77b81-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="77b81-110">Return value</span></span>

<span data-ttu-id="77b81-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="77b81-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="77b81-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="77b81-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="77b81-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="77b81-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="77b81-114">Commenti</span><span class="sxs-lookup"><span data-stu-id="77b81-114">Remarks</span></span>

<span data-ttu-id="77b81-115">Quando una console riceve l'input del mouse, una struttura di [**\_ record di input**](input-record-str.md) contenente una struttura di [**\_ \_ record di eventi del mouse**](mouse-event-record-str.md) viene inserita nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="77b81-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="77b81-116">Il membro **dwButtonState** del **\_ \_ record dell'evento del mouse** presenta un bit che indica lo stato di ogni pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="77b81-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="77b81-117">Il bit è 1 se il pulsante è inattivo e 0 se il pulsante è attivo.</span><span class="sxs-lookup"><span data-stu-id="77b81-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="77b81-118">Per determinare il numero di bit significativi, utilizzare **GetNumberOfConsoleMouseButtons** .</span><span class="sxs-lookup"><span data-stu-id="77b81-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons** .</span></span>

> [!TIP]
> <span data-ttu-id="77b81-119">Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="77b81-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="77b81-120">Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="77b81-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="77b81-121">Questo stato è pertinente solo per l'utente locale, la sessione e il contesto dei privilegi.</span><span class="sxs-lookup"><span data-stu-id="77b81-121">This state is only relevant to the local user, session, and privilege context.</span></span> <span data-ttu-id="77b81-122">Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.</span><span class="sxs-lookup"><span data-stu-id="77b81-122">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="77b81-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="77b81-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="77b81-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="77b81-124">Minimum supported client</span></span> | <span data-ttu-id="77b81-125">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="77b81-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="77b81-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="77b81-126">Minimum supported server</span></span> | <span data-ttu-id="77b81-127">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="77b81-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="77b81-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="77b81-128">Header</span></span> | <span data-ttu-id="77b81-129">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="77b81-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="77b81-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="77b81-130">Library</span></span> | <span data-ttu-id="77b81-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="77b81-131">Kernel32.lib</span></span> |
| <span data-ttu-id="77b81-132">DLL</span><span class="sxs-lookup"><span data-stu-id="77b81-132">DLL</span></span> | <span data-ttu-id="77b81-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="77b81-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="77b81-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="77b81-134">See also</span></span>

[<span data-ttu-id="77b81-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="77b81-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="77b81-136">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="77b81-136">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="77b81-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="77b81-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="77b81-138">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="77b81-138">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="77b81-139">**\_record evento \_ mouse**</span><span class="sxs-lookup"><span data-stu-id="77b81-139">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)
