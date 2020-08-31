---
title: Modalità console
description: Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060097"
---
# <a name="console-modes"></a><span data-ttu-id="5c5af-104">Modalità console</span><span class="sxs-lookup"><span data-stu-id="5c5af-104">Console Modes</span></span>


<span data-ttu-id="5c5af-105">Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input.</span><span class="sxs-lookup"><span data-stu-id="5c5af-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="5c5af-106">Analogamente, ogni buffer dello schermo della console dispone di un set di modalità di output che influiscono sulle operazioni di output.</span><span class="sxs-lookup"><span data-stu-id="5c5af-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="5c5af-107">Le modalità di input possono essere divise in due gruppi: quelli che interessano le funzioni di input di alto livello e quelle che interessano le funzioni di input di basso livello.</span><span class="sxs-lookup"><span data-stu-id="5c5af-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="5c5af-108">Le modalità di output influiscono solo sulle applicazioni che utilizzano le funzioni di output di alto livello.</span><span class="sxs-lookup"><span data-stu-id="5c5af-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="5c5af-109">La funzione [**GetConsoleMode**](getconsolemode.md) segnala la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="5c5af-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="5c5af-110">La funzione [**SetConsoleMode**](setconsolemode.md) imposta la modalità corrente di un buffer di input della console o di un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="5c5af-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="5c5af-111">Se una console dispone di più buffer dello schermo, le modalità di output di ciascuna di esse possono essere diverse.</span><span class="sxs-lookup"><span data-stu-id="5c5af-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="5c5af-112">Un'applicazione può modificare le modalità I/O in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="5c5af-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="5c5af-113">Per ulteriori informazioni sulle modalità della console che interessano le operazioni di I/O di alto livello e di basso livello, vedere [modalità console di alto livello](high-level-console-modes.md) e [modalità console di basso livello](low-level-console-modes.md).</span><span class="sxs-lookup"><span data-stu-id="5c5af-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="5c5af-114">La funzione [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indica se la console corrente è in modalità schermo intero e se comunica direttamente con l'hardware.</span><span class="sxs-lookup"><span data-stu-id="5c5af-114">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode and whether it communicates directly with the hardware.</span></span>

 

 




