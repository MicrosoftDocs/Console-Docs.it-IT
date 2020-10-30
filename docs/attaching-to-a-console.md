---
title: Collegamento a una console
description: Un processo può usare la funzione AttachConsole per connettersi a una console. Un processo può essere collegato a una console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037459"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="1664b-105">Collegamento a una console</span><span class="sxs-lookup"><span data-stu-id="1664b-105">Attaching to a Console</span></span>

<span data-ttu-id="1664b-106">Un processo può usare la funzione [**AttachConsole**](attachconsole.md) per connettersi a una console come client.</span><span class="sxs-lookup"><span data-stu-id="1664b-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console as a client.</span></span> <span data-ttu-id="1664b-107">Un processo può essere collegato a una console.</span><span class="sxs-lookup"><span data-stu-id="1664b-107">A process can be attached to one console.</span></span>

<span data-ttu-id="1664b-108">A una console possono essere collegati molti processi.</span><span class="sxs-lookup"><span data-stu-id="1664b-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="1664b-109">Per recuperare un elenco dei processi collegati a una console, chiamare la funzione [**GetConsoleProcessList**](getconsoleprocesslist.md) .</span><span class="sxs-lookup"><span data-stu-id="1664b-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

<span data-ttu-id="1664b-110">Per connettersi come server, vedere informazioni su [**Pseudoconsoles**](pseudoconsoles.md).</span><span class="sxs-lookup"><span data-stu-id="1664b-110">To attach as a server, see information about [**Pseudoconsoles**](pseudoconsoles.md).</span></span>
