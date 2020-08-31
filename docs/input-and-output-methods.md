---
title: Metodi di input e output
description: Esistono due approcci diversi per l'I/O della console, la scelta tra cui dipende la flessibilità e il controllo delle esigenze di un'applicazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 29f4ca8f4851c73f79d810f56b57f490995cad04
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060436"
---
# <a name="input-and-output-methods"></a><span data-ttu-id="37e01-104">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="37e01-104">Input and Output Methods</span></span>


<span data-ttu-id="37e01-105">Esistono due approcci diversi per l'I/O della console, la scelta tra cui dipende la flessibilità e il controllo delle esigenze di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="37e01-105">There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.</span></span> <span data-ttu-id="37e01-106">L'approccio generale consente l'I/O del flusso di caratteri semplice, ma limita l'accesso ai buffer di input e dello schermo di una console.</span><span class="sxs-lookup"><span data-stu-id="37e01-106">The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers.</span></span> <span data-ttu-id="37e01-107">Con l'approccio di basso livello è necessario che gli sviluppatori scrivano altro codice e scelgano tra una gamma maggiore di funzioni, ma offre anche una maggiore flessibilità per un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="37e01-107">The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.</span></span>

<span data-ttu-id="37e01-108">Un'applicazione può usare le funzioni di I/O dei file, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), e le funzioni console, [**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md), per l'i/o di alto livello che fornisce l'accesso indiretto ai buffer di input e dello schermo di una console.</span><span class="sxs-lookup"><span data-stu-id="37e01-108">An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers.</span></span> <span data-ttu-id="37e01-109">Le funzioni di input di alto livello filtrano ed elaborano i dati nel buffer di input di una console per restituire l'input come flusso di caratteri, ignorando l'input del mouse e del ridimensionamento del buffer.</span><span class="sxs-lookup"><span data-stu-id="37e01-109">The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input.</span></span> <span data-ttu-id="37e01-110">Analogamente, le funzioni di output di alto livello scrivono un flusso di caratteri visualizzati nella posizione corrente del cursore in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="37e01-110">Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer.</span></span> <span data-ttu-id="37e01-111">Un'applicazione controlla la modalità di funzionamento di queste funzioni impostando le modalità I/O della console.</span><span class="sxs-lookup"><span data-stu-id="37e01-111">An application controls the way these functions work by setting a console's I/O modes.</span></span>

<span data-ttu-id="37e01-112">Le funzioni di I/O di basso livello forniscono l'accesso diretto ai buffer di input e dello schermo di una console, consentendo a un'applicazione di accedere a eventi di input per il mouse e il ridimensionamento del buffer e le informazioni estese per gli eventi della tastiera.</span><span class="sxs-lookup"><span data-stu-id="37e01-112">The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events.</span></span> <span data-ttu-id="37e01-113">Le funzioni di output di basso livello consentono a un'applicazione di leggere o scrivere in un numero specificato di celle di caratteri consecutivi in un buffer dello schermo o di leggere o scrivere in blocchi rettangolari di celle di tipo carattere in una posizione specificata in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="37e01-113">Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span> <span data-ttu-id="37e01-114">Le modalità di input di una console influiscono sull'input di basso livello, consentendo all'applicazione di determinare se gli eventi del mouse e del ridimensionamento del buffer vengono inseriti nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="37e01-114">A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer.</span></span> <span data-ttu-id="37e01-115">Le modalità di output di una console non hanno effetto sull'output di basso livello.</span><span class="sxs-lookup"><span data-stu-id="37e01-115">A console's output modes have no effect on low-level output.</span></span>

<span data-ttu-id="37e01-116">I metodi di I/O di alto livello e di basso livello non si escludono a vicenda e un'applicazione può usare qualsiasi combinazione di queste funzioni.</span><span class="sxs-lookup"><span data-stu-id="37e01-116">The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions.</span></span> <span data-ttu-id="37e01-117">In genere, tuttavia, un'applicazione usa esclusivamente un approccio o l'altro.</span><span class="sxs-lookup"><span data-stu-id="37e01-117">Typically, however, an application uses one approach or the other exclusively.</span></span>

<span data-ttu-id="37e01-118">Negli argomenti seguenti vengono descritte le modalità console e le funzioni di I/O di alto livello e di basso livello.</span><span class="sxs-lookup"><span data-stu-id="37e01-118">The following topics describe the console modes and the high-level and low-level I/O functions.</span></span>

- [<span data-ttu-id="37e01-119">Modalità console</span><span class="sxs-lookup"><span data-stu-id="37e01-119">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="37e01-120">I/O console di alto livello</span><span class="sxs-lookup"><span data-stu-id="37e01-120">High-Level Console I/O</span></span>](high-level-console-i-o.md)
- [<span data-ttu-id="37e01-121">Modalità console di alto livello</span><span class="sxs-lookup"><span data-stu-id="37e01-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="37e01-122">Funzioni di input e output console di alto livello</span><span class="sxs-lookup"><span data-stu-id="37e01-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="37e01-123">I/O console di basso livello</span><span class="sxs-lookup"><span data-stu-id="37e01-123">Low-Level Console I/O</span></span>](low-level-console-i-o.md)
- [<span data-ttu-id="37e01-124">Modalità console di basso livello</span><span class="sxs-lookup"><span data-stu-id="37e01-124">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="37e01-125">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="37e01-125">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="37e01-126">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="37e01-126">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

 

 




