---
title: Modalità console
description: Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039199"
---
# <a name="console-modes"></a><span data-ttu-id="51466-104">Modalità console</span><span class="sxs-lookup"><span data-stu-id="51466-104">Console Modes</span></span>

<span data-ttu-id="51466-105">Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input.</span><span class="sxs-lookup"><span data-stu-id="51466-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="51466-106">Analogamente, ogni buffer dello schermo della console dispone di un set di modalità di output che influiscono sulle operazioni di output.</span><span class="sxs-lookup"><span data-stu-id="51466-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="51466-107">Le modalità di input possono essere divise in due gruppi: quelli che interessano le funzioni di input di alto livello e quelle che interessano le funzioni di input di basso livello.</span><span class="sxs-lookup"><span data-stu-id="51466-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="51466-108">Le modalità di output influiscono solo sulle applicazioni che utilizzano le funzioni di output di alto livello.</span><span class="sxs-lookup"><span data-stu-id="51466-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="51466-109">La funzione [**GetConsoleMode**](getconsolemode.md) segnala la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="51466-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="51466-110">La funzione [**SetConsoleMode**](setconsolemode.md) imposta la modalità corrente di un buffer di input della console o di un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="51466-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="51466-111">Se una console dispone di più buffer dello schermo, le modalità di output di ciascuna di esse possono essere diverse.</span><span class="sxs-lookup"><span data-stu-id="51466-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="51466-112">Un'applicazione può modificare le modalità I/O in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="51466-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="51466-113">Per ulteriori informazioni sulle modalità della console che interessano le operazioni di I/O di alto livello e di basso livello, vedere [modalità console di alto livello](high-level-console-modes.md) e [modalità console di basso livello](low-level-console-modes.md).</span><span class="sxs-lookup"><span data-stu-id="51466-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="51466-114">Un'applicazione della riga di comando dovrebbe prevedere che altre applicazioni della riga di comando possano modificare la modalità console in qualsiasi momento e non ripristinare il modulo originale prima di restituire il controllo.</span><span class="sxs-lookup"><span data-stu-id="51466-114">A command-line application should expect that other command-line applications may change the console mode at any time and may not restore it to its original form before control is returned.</span></span> <span data-ttu-id="51466-115">Inoltre, è consigliabile che tutte le applicazioni della riga di comando acquisiscano la modalità iniziale della console all'avvio e tentano di ripristinarla quando si esce per garantire un effetto minimo sulle altre applicazioni della riga di comando collegate alla stessa console.</span><span class="sxs-lookup"><span data-stu-id="51466-115">Additionally, we recommend that all command-line applications should capture the initial console mode at startup and attempt to restore it when exiting to ensure minimal impact on other command-line applications attached to the same console.</span></span>

<span data-ttu-id="51466-116">La funzione [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indica se la console corrente è in modalità schermo intero.</span><span class="sxs-lookup"><span data-stu-id="51466-116">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode.</span></span>
