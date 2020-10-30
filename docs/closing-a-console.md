---
title: Chiusura di una console
description: Un processo può utilizzare la funzione FreeConsole per scollegarsi dalla console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: db424e6d9fc91a7a3b6cff3b5fc5028833d208f9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037319"
---
# <a name="closing-a-console"></a><span data-ttu-id="daeb8-104">Chiusura di una console</span><span class="sxs-lookup"><span data-stu-id="daeb8-104">Closing a Console</span></span>

<span data-ttu-id="daeb8-105">Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console.</span><span class="sxs-lookup"><span data-stu-id="daeb8-105">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="daeb8-106">Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="daeb8-106">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="daeb8-107">Dopo la chiamata a **FreeConsole** , il processo può usare [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.</span><span class="sxs-lookup"><span data-stu-id="daeb8-107">After calling **FreeConsole** , the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="daeb8-108">Una console viene chiusa quando l'ultimo processo collegato termina o chiama [**FreeConsole**](freeconsole.md).</span><span class="sxs-lookup"><span data-stu-id="daeb8-108">A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).</span></span>
