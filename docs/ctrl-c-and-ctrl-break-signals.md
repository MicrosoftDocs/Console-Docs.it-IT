---
title: Segnali CTRL+C e CTRL+INTERR
description: Le combinazioni di tasti CTRL+C e CTRL+INTERR ricevono una specifica gestione da parte dei processi della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420190"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="3b45e-104">Segnali CTRL+C e CTRL+INTERR</span><span class="sxs-lookup"><span data-stu-id="3b45e-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="3b45e-105">Le combinazioni di tasti <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>INTERR</kbd> ricevono una specifica gestione da parte dei processi della console.</span><span class="sxs-lookup"><span data-stu-id="3b45e-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="3b45e-106">Per impostazione predefinita, quando una finestra della console dispone dello stato attivo della tastiera, <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene considerato come segnale (SIGINT o SIGBREAK) e non come input da tastiera.</span><span class="sxs-lookup"><span data-stu-id="3b45e-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="3b45e-107">Per impostazione predefinita, questi segnali vengono passati a tutti i processi della console collegati alla console.</span><span class="sxs-lookup"><span data-stu-id="3b45e-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="3b45e-108">I processi scollegati non sono interessati.</span><span class="sxs-lookup"><span data-stu-id="3b45e-108">(Detached processes are not affected.</span></span> <span data-ttu-id="3b45e-109">Vedere [**Creazione di una console**](creation-of-a-console.md). Il sistema crea un nuovo thread in ogni processo client per gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="3b45e-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="3b45e-110">Il thread genera un'eccezione se è in corso il debug del processo.</span><span class="sxs-lookup"><span data-stu-id="3b45e-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="3b45e-111">Il debugger può gestire l'eccezione o continuare a lasciarla non gestita.</span><span class="sxs-lookup"><span data-stu-id="3b45e-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="3b45e-112"><kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene sempre considerato come segnale, ma un'applicazione può modificare il comportamento predefinito di <kbd>CTRL</kbd>+<kbd>C</kbd> in due modi che impediscono la chiamata delle funzioni gestore:</span><span class="sxs-lookup"><span data-stu-id="3b45e-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="3b45e-113">La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità di input **ENABLE\_PROCESSED\_INPUT** per un buffer di input della console, in modo che CTRL+C venga segnalato come input da tastiera anziché come segnale.</span><span class="sxs-lookup"><span data-stu-id="3b45e-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="3b45e-114">Quando [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) viene chiamata con i valori **NULL** e **TRUE** per i relativi parametri, il processo chiamante ignora i segnali di CTRL+C.</span><span class="sxs-lookup"><span data-stu-id="3b45e-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="3b45e-115">La normale elaborazione di CTRL+C viene ripristinata chiamando **SetConsoleCtrlHandler** con i valori **NULL** e **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="3b45e-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="3b45e-116">Questo attributo che consente di ignorare o meno i segnali di CTRL+C, viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.</span><span class="sxs-lookup"><span data-stu-id="3b45e-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="3b45e-117">Per altre informazioni sull'elaborazione di questi segnali, inclusi i timeout, vedere la documentazione della funzione di callback [**HandlerRoutine**](handlerroutine.md).</span><span class="sxs-lookup"><span data-stu-id="3b45e-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
