---
title: CTRL + C e CTRL + INTERROMPi segnali
description: Le combinazioni di tasti CTRL + C e CTRL + INTERr ricevono una gestione speciale dai processi della console.
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
ms.openlocfilehash: 12a4541d51cb18109caa6d1c15c25479c9e91a7a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039099"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="8bd38-104">CTRL + C e CTRL + INTERROMPi segnali</span><span class="sxs-lookup"><span data-stu-id="8bd38-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="8bd38-105">Le <kbd>CTRL</kbd> + combinazioni di tasti CTRL<kbd>C</kbd> e <kbd>CTRL</kbd> + <kbd>Interrompi</kbd> ricevono una gestione speciale dai processi della console.</span><span class="sxs-lookup"><span data-stu-id="8bd38-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="8bd38-106">Per impostazione predefinita, quando una finestra della console dispone dello stato attivo della tastiera, <kbd>CTRL</kbd> + <kbd>C</kbd> o <kbd>CTRL</kbd> + <kbd>break</kbd> viene considerato come un segnale (SIGINT o SIGBREAK) e non come input da tastiera.</span><span class="sxs-lookup"><span data-stu-id="8bd38-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="8bd38-107">Per impostazione predefinita, questi segnali vengono passati a tutti i processi della console collegati alla console.</span><span class="sxs-lookup"><span data-stu-id="8bd38-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="8bd38-108">I processi scollegati non sono interessati.</span><span class="sxs-lookup"><span data-stu-id="8bd38-108">(Detached processes are not affected.</span></span> <span data-ttu-id="8bd38-109">Vedere [**creazione di una console**](creation-of-a-console.md). Il sistema crea un nuovo thread in ogni processo client per gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="8bd38-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="8bd38-110">Il thread genera un'eccezione se è in corso il debug del processo.</span><span class="sxs-lookup"><span data-stu-id="8bd38-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="8bd38-111">Il debugger può gestire l'eccezione o continuare con l'eccezione non gestita.</span><span class="sxs-lookup"><span data-stu-id="8bd38-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="8bd38-112"><kbd>CTRL</kbd> + <kbd>Break</kbd> viene sempre considerato come un segnale, ma un'applicazione può modificare il comportamento predefinito di <kbd>CTRL</kbd> + <kbd>C</kbd> in due modi che impediscono la chiamata delle funzioni del gestore:</span><span class="sxs-lookup"><span data-stu-id="8bd38-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="8bd38-113">La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità di input di input **\_ elaborata \_** per il buffer di input di una console, quindi CTRL + C viene segnalato come input da tastiera anziché come segnale.</span><span class="sxs-lookup"><span data-stu-id="8bd38-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="8bd38-114">Quando [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) viene chiamato con valori **null** e **true** per i relativi parametri, il processo chiamante ignora i segnali CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="8bd38-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="8bd38-115">La normale elaborazione di CTRL + C viene ripristinata chiamando **SetConsoleCtrlHandler** con valori **null** e **false** .</span><span class="sxs-lookup"><span data-stu-id="8bd38-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="8bd38-116">Questo attributo di ignorare o ignorare i segnali CTRL + C viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.</span><span class="sxs-lookup"><span data-stu-id="8bd38-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="8bd38-117">Per ulteriori informazioni sull'elaborazione di questi segnali, inclusi i timeout, vedere la documentazione relativa alla routine di callback del [**gestore**](handlerroutine.md) .</span><span class="sxs-lookup"><span data-stu-id="8bd38-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
