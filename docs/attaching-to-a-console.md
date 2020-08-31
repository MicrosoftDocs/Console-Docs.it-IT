---
title: Connessione a una console
description: Un processo può usare la funzione AttachConsole per connettersi a una console. Un processo può essere collegato a una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: e6ab7da4022d45cd2b1d42957f15f4ffa7e068f3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060217"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="cb6a8-105">Connessione a una console</span><span class="sxs-lookup"><span data-stu-id="cb6a8-105">Attaching to a Console</span></span>


<span data-ttu-id="cb6a8-106">Un processo può usare la funzione [**AttachConsole**](attachconsole.md) per connettersi a una console.</span><span class="sxs-lookup"><span data-stu-id="cb6a8-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console.</span></span> <span data-ttu-id="cb6a8-107">Un processo può essere collegato a una console.</span><span class="sxs-lookup"><span data-stu-id="cb6a8-107">A process can be attached to one console.</span></span>

<span data-ttu-id="cb6a8-108">A una console possono essere collegati molti processi.</span><span class="sxs-lookup"><span data-stu-id="cb6a8-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="cb6a8-109">Per recuperare un elenco dei processi collegati a una console, chiamare la funzione [**GetConsoleProcessList**](getconsoleprocesslist.md) .</span><span class="sxs-lookup"><span data-stu-id="cb6a8-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

 

 




