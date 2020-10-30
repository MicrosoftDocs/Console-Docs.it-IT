---
title: GetConsoleScreenBufferInfoEx (funzione)
description: Recupera le informazioni estese sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 5f4b0f11821b7d5b61c61d4ab8f9774c4a69eec0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037939"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="4199a-104">GetConsoleScreenBufferInfoEx (funzione)</span><span class="sxs-lookup"><span data-stu-id="4199a-104">GetConsoleScreenBufferInfoEx function</span></span>

<span data-ttu-id="4199a-105">Recupera le informazioni estese sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="4199a-105">Retrieves extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4199a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4199a-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="4199a-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4199a-107">Parameters</span></span>

<span data-ttu-id="4199a-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4199a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4199a-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="4199a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4199a-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="4199a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4199a-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4199a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4199a-112">*lpConsoleScreenBufferInfoEx* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="4199a-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="4199a-113">Struttura [**\_ INFOEX del \_ buffer \_ dello schermo della console**](console-screen-buffer-infoex.md) che riceve le informazioni sul buffer dello schermo della console richieste.</span><span class="sxs-lookup"><span data-stu-id="4199a-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="4199a-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4199a-114">Return value</span></span>

<span data-ttu-id="4199a-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="4199a-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4199a-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="4199a-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4199a-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4199a-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4199a-118">Commenti</span><span class="sxs-lookup"><span data-stu-id="4199a-118">Remarks</span></span>

<span data-ttu-id="4199a-119">Il rettangolo restituito nel membro **srWindow** della struttura [**INFOEX del \_ \_ buffer dello \_ schermo della console**](console-screen-buffer-infoex.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.</span><span class="sxs-lookup"><span data-stu-id="4199a-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="4199a-120">Tutte le coordinate restituite nella struttura [**\_ \_ \_ INFOEX buffer dello schermo della console**](console-screen-buffer-infoex.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="4199a-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="4199a-121">Questa API non ha un equivalente del **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="4199a-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="4199a-122">Il suo utilizzo potrebbe essere ancora necessario per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione per recuperare le dimensioni della finestra.</span><span class="sxs-lookup"><span data-stu-id="4199a-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="4199a-123">Questo stato della finestra viene gestito da TTY/PTY/Pseudoconsole all'esterno del flusso di flusso normale ed è in genere considerato un privilegio utente non modificabile dall'applicazione client.</span><span class="sxs-lookup"><span data-stu-id="4199a-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="4199a-124">Gli aggiornamenti possono essere ricevuti in [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="4199a-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4199a-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4199a-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4199a-126">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4199a-126">Minimum supported client</span></span> | <span data-ttu-id="4199a-127">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="4199a-127">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="4199a-128">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4199a-128">Minimum supported server</span></span> | <span data-ttu-id="4199a-129">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="4199a-129">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="4199a-130">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4199a-130">Header</span></span> | <span data-ttu-id="4199a-131">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4199a-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4199a-132">Libreria</span><span class="sxs-lookup"><span data-stu-id="4199a-132">Library</span></span> | <span data-ttu-id="4199a-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4199a-133">Kernel32.lib</span></span> |
| <span data-ttu-id="4199a-134">DLL</span><span class="sxs-lookup"><span data-stu-id="4199a-134">DLL</span></span> | <span data-ttu-id="4199a-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4199a-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4199a-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4199a-136">See also</span></span>

[<span data-ttu-id="4199a-137">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="4199a-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4199a-138">**\_INFOEX buffer dello schermo della console \_ \_**</span><span class="sxs-lookup"><span data-stu-id="4199a-138">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="4199a-139">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="4199a-139">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)
