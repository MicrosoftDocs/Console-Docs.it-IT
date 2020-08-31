---
title: I/O console di alto livello
description: Le funzioni di I/O di alto livello forniscono un modo semplice per leggere un flusso di caratteri dall'input della console o per scrivere un flusso di caratteri nell'output della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 2209259f604bb8653bca6ab38ca763b63f65713f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059612"
---
# <a name="high-level-console-io"></a><span data-ttu-id="58a23-104">I/O console di alto livello</span><span class="sxs-lookup"><span data-stu-id="58a23-104">High-Level Console I/O</span></span>


<span data-ttu-id="58a23-105">Le funzioni di I/O di alto livello forniscono un modo semplice per leggere un flusso di caratteri dall'input della console o per scrivere un flusso di caratteri nell'output della console.</span><span class="sxs-lookup"><span data-stu-id="58a23-105">The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output.</span></span> <span data-ttu-id="58a23-106">Un'operazione di lettura di alto livello ottiene i caratteri di input dal buffer di input di una console e li archivia in un buffer specificato.</span><span class="sxs-lookup"><span data-stu-id="58a23-106">A high-level read operation gets input characters from a console's input buffer and stores them in a specified buffer.</span></span> <span data-ttu-id="58a23-107">Un'operazione di scrittura di alto livello accetta caratteri da un buffer specificato e li scrive in un buffer dello schermo in corrispondenza della posizione corrente del cursore, spostando il cursore mentre viene scritto ogni carattere.</span><span class="sxs-lookup"><span data-stu-id="58a23-107">A high-level write operation takes characters from a specified buffer and writes them to a screen buffer at the current cursor location, advancing the cursor as each character is written.</span></span>

<span data-ttu-id="58a23-108">L'I/O di alto livello consente di scegliere tra le funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) e le funzioni [**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="58a23-108">High-level I/O gives you a choice between the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions and the [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md) functions.</span></span> <span data-ttu-id="58a23-109">Sono identici, tranne che per due importanti differenze.</span><span class="sxs-lookup"><span data-stu-id="58a23-109">They are identical, except for two important differences.</span></span> <span data-ttu-id="58a23-110">Le funzioni della console supportano l'utilizzo di caratteri Unicode o del set di caratteri ANSI; le funzioni di I/O dei file non supportano Unicode.</span><span class="sxs-lookup"><span data-stu-id="58a23-110">The console functions support the use of either Unicode characters or the ANSI character set; the file I/O functions do not support Unicode.</span></span> <span data-ttu-id="58a23-111">Inoltre, è possibile utilizzare le funzioni di I/O dei file per accedere ai file, alle pipe e ai dispositivi di comunicazione seriale. le funzioni della console possono essere utilizzate solo con handle di console.</span><span class="sxs-lookup"><span data-stu-id="58a23-111">Also, the file I/O functions can be used to access files, pipes, and serial communications devices; the console functions can only be used with console handles.</span></span> <span data-ttu-id="58a23-112">Questa distinzione è importante se un'applicazione si basa su handle standard che potrebbero essere stati reindirizzati.</span><span class="sxs-lookup"><span data-stu-id="58a23-112">This distinction is important if an application relies on standard handles that may have been redirected.</span></span>

<span data-ttu-id="58a23-113">Quando si usa un set di funzioni di alto livello, un'applicazione può controllare il testo e i colori di sfondo usati per visualizzare i caratteri successivamente scritti in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="58a23-113">When using either set of high-level functions, an application can control the text and background colors used to display characters subsequently written to a screen buffer.</span></span> <span data-ttu-id="58a23-114">Un'applicazione può inoltre utilizzare le modalità console che interessano le operazioni di I/O della console di alto livello per abilitare o disabilitare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="58a23-114">An application can also use the console modes that affect high-level console I/O to enable or disable the following properties:</span></span>

- <span data-ttu-id="58a23-115">Ripetizione dell'input della tastiera sul buffer dello schermo attivo</span><span class="sxs-lookup"><span data-stu-id="58a23-115">Echoing of keyboard input to the active screen buffer</span></span>
- <span data-ttu-id="58a23-116">Input di riga, in cui un'operazione di lettura non viene restituita fino a quando non viene premuto il tasto invio</span><span class="sxs-lookup"><span data-stu-id="58a23-116">Line input, in which a read operation does not return until the ENTER key is pressed</span></span>
- <span data-ttu-id="58a23-117">Elaborazione automatica dell'input da tastiera per gestire i ritorni a capo, CTRL + C e altri dettagli di input</span><span class="sxs-lookup"><span data-stu-id="58a23-117">Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details</span></span>
- <span data-ttu-id="58a23-118">Elaborazione automatica dell'output per gestire il ritorno a capo delle righe, i ritorni a capo, gli spazi e gli altri dettagli di output</span><span class="sxs-lookup"><span data-stu-id="58a23-118">Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details</span></span>

<span data-ttu-id="58a23-119">Per altre informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="58a23-119">For more information, see the following topics:</span></span>

- [<span data-ttu-id="58a23-120">Modalità console</span><span class="sxs-lookup"><span data-stu-id="58a23-120">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="58a23-121">Modalità console di alto livello</span><span class="sxs-lookup"><span data-stu-id="58a23-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="58a23-122">Funzioni di input e output console di alto livello</span><span class="sxs-lookup"><span data-stu-id="58a23-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)

 

 




