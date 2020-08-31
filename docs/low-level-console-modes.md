---
title: Modalità console di basso livello
description: I tipi di eventi di input segnalati nel buffer di input di una console dipendono dalle modalità di input del mouse e della finestra della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: 375b3b6eaef499324bdbde24ec973d91c50dda5b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060028"
---
# <a name="low-level-console-modes"></a><span data-ttu-id="c57a9-104">Modalità console di basso livello</span><span class="sxs-lookup"><span data-stu-id="c57a9-104">Low-Level Console Modes</span></span>


<span data-ttu-id="c57a9-105">I tipi di eventi di input segnalati nel buffer di input di una console dipendono dalle modalità di input del mouse e della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="c57a9-105">The types of input events reported in a console's input buffer depend on the console's mouse and window input modes.</span></span> <span data-ttu-id="c57a9-106">La modalità di input elaborata della console determina il modo in cui il sistema gestisce la combinazione di tasti CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="c57a9-106">The console's processed input mode determines how the system handles the CTRL+C key combination.</span></span> <span data-ttu-id="c57a9-107">Per impostare o recuperare lo stato delle modalità di input di una console, un'applicazione può specificare un handle del buffer di input della console in una chiamata alla funzione [**SetConsoleMode**](setconsolemode.md) o [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="c57a9-107">To set or retrieve the state of a console's input modes, an application can specify a console input buffer handle in a call to the [**SetConsoleMode**](setconsolemode.md) or [**GetConsoleMode**](getconsolemode.md) function.</span></span> <span data-ttu-id="c57a9-108">Le modalità seguenti vengono usate con gli handle di input della console.</span><span class="sxs-lookup"><span data-stu-id="c57a9-108">The following modes are used with console input handles.</span></span>


| <span data-ttu-id="c57a9-109">Mode</span><span class="sxs-lookup"><span data-stu-id="c57a9-109">Mode</span></span>                         | <span data-ttu-id="c57a9-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c57a9-110">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c57a9-111">**Abilita \_ input del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="c57a9-111">**ENABLE\_MOUSE\_INPUT**</span></span>     | <span data-ttu-id="c57a9-112">Controlla se gli eventi del mouse vengono segnalati nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="c57a9-112">Controls whether mouse events are reported in the input buffer.</span></span> <span data-ttu-id="c57a9-113">Per impostazione predefinita, l'input del mouse è abilitato e l'input della finestra è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="c57a9-113">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="c57a9-114">La modifica di una di queste modalità influisca solo sugli input che si verificano dopo l'impostazione della modalità; gli eventi del mouse o della finestra in sospeso nel buffer di input non vengono scaricati.</span><span class="sxs-lookup"><span data-stu-id="c57a9-114">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="c57a9-115">Il puntatore del mouse viene visualizzato indipendentemente dalla modalità del mouse.</span><span class="sxs-lookup"><span data-stu-id="c57a9-115">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                                |
| <span data-ttu-id="c57a9-116">**Abilita \_ \_ input finestra**</span><span class="sxs-lookup"><span data-stu-id="c57a9-116">**ENABLE\_WINDOW\_INPUT**</span></span>    | <span data-ttu-id="c57a9-117">Controlla se gli eventi di ridimensionamento del buffer vengono segnalati nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="c57a9-117">Controls whether buffer-resizing events are reported in the input buffer.</span></span> <span data-ttu-id="c57a9-118">Per impostazione predefinita, l'input del mouse è abilitato e l'input della finestra è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="c57a9-118">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="c57a9-119">La modifica di una di queste modalità influisca solo sugli input che si verificano dopo l'impostazione della modalità; gli eventi del mouse o della finestra in sospeso nel buffer di input non vengono scaricati.</span><span class="sxs-lookup"><span data-stu-id="c57a9-119">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="c57a9-120">Il puntatore del mouse viene visualizzato indipendentemente dalla modalità del mouse.</span><span class="sxs-lookup"><span data-stu-id="c57a9-120">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                      |
| <span data-ttu-id="c57a9-121">**Abilita \_ \_ input elaborato**</span><span class="sxs-lookup"><span data-stu-id="c57a9-121">**ENABLE\_PROCESSED\_INPUT**</span></span> | <span data-ttu-id="c57a9-122">Controlla l'elaborazione dell'input per le applicazioni mediante le funzioni di I/O della console di alto livello.</span><span class="sxs-lookup"><span data-stu-id="c57a9-122">Controls the processing of input for applications using the high-level console I/O functions.</span></span> <span data-ttu-id="c57a9-123">Tuttavia, se la modalità di input elaborata è abilitata, la combinazione di tasti CTRL + C non viene segnalata nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="c57a9-123">However, if processed input mode is enabled, the CTRL+C key combination is not reported in the console's input buffer.</span></span> <span data-ttu-id="c57a9-124">Viene invece passato alla funzione del gestore di controllo appropriata.</span><span class="sxs-lookup"><span data-stu-id="c57a9-124">Instead, it is passed on to the appropriate control handler function.</span></span> <span data-ttu-id="c57a9-125">Per altre informazioni sui gestori di controllo, vedere [gestori di controlli della console](console-control-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="c57a9-125">For more information about control handlers, see [Console Control Handlers](console-control-handlers.md).</span></span> |



<span data-ttu-id="c57a9-126">Le modalità di output di un buffer dello schermo non influiscono sul comportamento delle funzioni di output di basso livello.</span><span class="sxs-lookup"><span data-stu-id="c57a9-126">The output modes of a screen buffer do not affect the behavior of the low-level output functions.</span></span>








