---
title: GetConsoleScreenBufferInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleScreenBufferInfo, che recupera le informazioni sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038769"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="6d13e-104">GetConsoleScreenBufferInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="6d13e-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="6d13e-105">Recupera le informazioni sul buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="6d13e-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6d13e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6d13e-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="6d13e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="6d13e-107">Parameters</span></span>

<span data-ttu-id="6d13e-108">*hConsoleOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6d13e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6d13e-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6d13e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6d13e-110">L'handle deve avere il diritto di accesso in **\_ lettura generico** .</span><span class="sxs-lookup"><span data-stu-id="6d13e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6d13e-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6d13e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6d13e-112">*lpConsoleScreenBufferInfo* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="6d13e-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="6d13e-113">Puntatore a una struttura [**di \_ \_ \_ informazioni sul buffer dello schermo della console**](console-screen-buffer-info-str.md) che riceve le informazioni sul buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6d13e-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6d13e-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6d13e-114">Return value</span></span>

<span data-ttu-id="6d13e-115">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="6d13e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6d13e-116">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="6d13e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6d13e-117">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6d13e-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="6d13e-118">Commenti</span><span class="sxs-lookup"><span data-stu-id="6d13e-118">Remarks</span></span>

<span data-ttu-id="6d13e-119">Il rettangolo restituito nel membro **srWindow** della struttura di [**\_ informazioni sul \_ buffer \_ dello schermo della console**](console-screen-buffer-info-str.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.</span><span class="sxs-lookup"><span data-stu-id="6d13e-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="6d13e-120">Tutte le coordinate restituite nella struttura delle [**\_ \_ \_ informazioni del buffer dello schermo della console**](console-screen-buffer-info-str.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6d13e-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="6d13e-121">Questa API non ha un equivalente del **[terminale virtuale](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="6d13e-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="6d13e-122">Il suo utilizzo potrebbe essere ancora necessario per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione per recuperare le dimensioni della finestra.</span><span class="sxs-lookup"><span data-stu-id="6d13e-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="6d13e-123">Questo stato della finestra viene gestito da TTY/PTY/Pseudoconsole all'esterno del flusso di flusso normale ed è in genere considerato un privilegio utente non modificabile dall'applicazione client.</span><span class="sxs-lookup"><span data-stu-id="6d13e-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="6d13e-124">Gli aggiornamenti possono essere ricevuti in [**ReadConsoleInput**](readconsoleinput.md).</span><span class="sxs-lookup"><span data-stu-id="6d13e-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6d13e-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="6d13e-125">Examples</span></span>

<span data-ttu-id="6d13e-126">Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="6d13e-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6d13e-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6d13e-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6d13e-128">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6d13e-128">Minimum supported client</span></span> | <span data-ttu-id="6d13e-129">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="6d13e-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6d13e-130">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6d13e-130">Minimum supported server</span></span> | <span data-ttu-id="6d13e-131">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="6d13e-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6d13e-132">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6d13e-132">Header</span></span> | <span data-ttu-id="6d13e-133">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6d13e-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6d13e-134">Libreria</span><span class="sxs-lookup"><span data-stu-id="6d13e-134">Library</span></span> | <span data-ttu-id="6d13e-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6d13e-135">Kernel32.lib</span></span> |
| <span data-ttu-id="6d13e-136">DLL</span><span class="sxs-lookup"><span data-stu-id="6d13e-136">DLL</span></span> | <span data-ttu-id="6d13e-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6d13e-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6d13e-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="6d13e-138">See also</span></span>

[<span data-ttu-id="6d13e-139">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="6d13e-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6d13e-140">**\_informazioni sul \_ buffer dello schermo della console \_**</span><span class="sxs-lookup"><span data-stu-id="6d13e-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="6d13e-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="6d13e-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="6d13e-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="6d13e-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="6d13e-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="6d13e-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="6d13e-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="6d13e-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="6d13e-145">Dimensioni del buffer della finestra e dello schermo</span><span class="sxs-lookup"><span data-stu-id="6d13e-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
