---
title: Modalità console High-Level
description: Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038644"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="08904-104">Modalità console High-Level</span><span class="sxs-lookup"><span data-stu-id="08904-104">High-Level Console Modes</span></span>

<span data-ttu-id="08904-105">Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console.</span><span class="sxs-lookup"><span data-stu-id="08904-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="08904-106">Tutte le modalità di input della console seguenti sono abilitate per il buffer di input di una console quando viene creata una console:</span><span class="sxs-lookup"><span data-stu-id="08904-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="08904-107">Modalità input linea</span><span class="sxs-lookup"><span data-stu-id="08904-107">Line input mode</span></span>
- <span data-ttu-id="08904-108">Modalità di input elaborata</span><span class="sxs-lookup"><span data-stu-id="08904-108">Processed input mode</span></span>
- <span data-ttu-id="08904-109">Modalità input echo</span><span class="sxs-lookup"><span data-stu-id="08904-109">Echo input mode</span></span>

<span data-ttu-id="08904-110">Entrambe le modalità di output della console seguenti sono abilitate per un buffer dello schermo della console quando viene creato:</span><span class="sxs-lookup"><span data-stu-id="08904-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="08904-111">Modalità output elaborata</span><span class="sxs-lookup"><span data-stu-id="08904-111">Processed output mode</span></span>
- <span data-ttu-id="08904-112">Wrapping in modalità di output EOL</span><span class="sxs-lookup"><span data-stu-id="08904-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="08904-113">Tutte e tre le modalità di input, insieme alla modalità output elaborata, sono progettate per essere utilizzate insieme.</span><span class="sxs-lookup"><span data-stu-id="08904-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="08904-114">È consigliabile abilitare o disabilitare tutte queste modalità come gruppo.</span><span class="sxs-lookup"><span data-stu-id="08904-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="08904-115">Quando tutti sono abilitati, l'applicazione viene definita in modalità "cotta", il che significa che la maggior parte dell'elaborazione viene gestita per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="08904-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="08904-116">Quando tutti sono disabilitati, l'applicazione è in modalità "Raw", il che significa che l'input non viene filtrato e l'elaborazione viene lasciata all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="08904-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="08904-117">Un'applicazione può usare la funzione [**GetConsoleMode**](getconsolemode.md) per determinare la modalità corrente del buffer di input o dello schermo di una console.</span><span class="sxs-lookup"><span data-stu-id="08904-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="08904-118">È possibile abilitare o disabilitare una qualsiasi di queste modalità usando i valori seguenti nella funzione [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="08904-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="08904-119">Si noti che l'impostazione della modalità di output di un buffer dello schermo non influisce sulla modalità di output di altri buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="08904-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
