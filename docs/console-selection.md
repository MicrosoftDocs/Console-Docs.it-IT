---
title: Selezione nella console
description: Un'applicazione di accessibilità richiede informazioni sulla selezione dell'utente nella console di.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_selection'
- base.console\_selection
- consoles.console\_selection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
ms.openlocfilehash: afc2d0a7615381b394df7f496aaf1b2a6002d04f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039159"
---
# <a name="console-selection"></a><span data-ttu-id="cbd82-104">Selezione nella console</span><span class="sxs-lookup"><span data-stu-id="cbd82-104">Console Selection</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="cbd82-105">Un'applicazione di accessibilità richiede informazioni sulla selezione dell'utente nella console di.</span><span class="sxs-lookup"><span data-stu-id="cbd82-105">An accessibility application needs information about the user's selection in the console.</span></span> <span data-ttu-id="cbd82-106">Per recuperare la selezione corrente della console, chiamare la funzione [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) .</span><span class="sxs-lookup"><span data-stu-id="cbd82-106">To retrieve the current console selection, call the [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) function.</span></span> <span data-ttu-id="cbd82-107">La struttura delle [**\_ \_ informazioni di selezione della console**](console-selection-info-str.md) contiene informazioni sulla selezione, ad esempio l'ancoraggio, le coordinate e lo stato.</span><span class="sxs-lookup"><span data-stu-id="cbd82-107">The [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure contains information about the selection, such as the anchor, coordinates, and status.</span></span>
