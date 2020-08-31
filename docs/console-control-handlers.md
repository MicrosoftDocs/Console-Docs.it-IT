---
title: Gestori di controlli console
description: Ogni processo della console dispone di un proprio elenco di funzioni del gestore di controllo chiamate dal sistema quando il processo riceve un segnale CTRL + C, CTRL + INTERr o CTRL + CLOSE.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: b3fa6f3e842d1757b90ff03c30a343ad12964882
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060137"
---
# <a name="console-control-handlers"></a><span data-ttu-id="888da-104">Gestori di controlli console</span><span class="sxs-lookup"><span data-stu-id="888da-104">Console Control Handlers</span></span>


<span data-ttu-id="888da-105">Ogni processo della console dispone di un proprio elenco di funzioni del gestore di controllo chiamate dal sistema quando il processo riceve un segnale [CTRL + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + INTERR](ctrl-c-and-ctrl-break-signals.md)o [CTRL + Close](ctrl-close-signal.md) .</span><span class="sxs-lookup"><span data-stu-id="888da-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="888da-106">Inizialmente, l'elenco dei gestori di controllo per ogni processo contiene solo una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) .</span><span class="sxs-lookup"><span data-stu-id="888da-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="888da-107">Un processo della console può aggiungere o rimuovere funzioni [**HandlerRoutine**](handlerroutine.md) aggiuntive chiamando la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) .</span><span class="sxs-lookup"><span data-stu-id="888da-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="888da-108">Questa funzione non influisce sugli elenchi di gestori di controllo per altri processi.</span><span class="sxs-lookup"><span data-stu-id="888da-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="888da-109">Quando un processo della console riceve uno dei segnali di controllo, chiama le funzioni del gestore su una base Ultima registrazione, prima chiamata, fino a quando uno dei gestori non restituisce **true**.</span><span class="sxs-lookup"><span data-stu-id="888da-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**.</span></span> <span data-ttu-id="888da-110">Se nessuno dei gestori restituisce **true**, viene chiamato il gestore predefinito.</span><span class="sxs-lookup"><span data-stu-id="888da-110">If none of the handlers returns **TRUE**, the default handler is called.</span></span>

<span data-ttu-id="888da-111">Il parametro *dwCtrlType* della funzione identifica il segnale di controllo ricevuto e il valore restituito indica se il segnale è stato gestito.</span><span class="sxs-lookup"><span data-stu-id="888da-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="888da-112">Per un esempio di una funzione del gestore di controllo, vedere [registrazione di una funzione](registering-a-control-handler-function.md)di gestione del controllo.</span><span class="sxs-lookup"><span data-stu-id="888da-112">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

 

 




