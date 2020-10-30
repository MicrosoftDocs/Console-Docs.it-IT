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
# <a name="console-selection"></a>Selezione nella console

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Un'applicazione di accessibilità richiede informazioni sulla selezione dell'utente nella console di. Per recuperare la selezione corrente della console, chiamare la funzione [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) . La struttura delle [**\_ \_ informazioni di selezione della console**](console-selection-info-str.md) contiene informazioni sulla selezione, ad esempio l'ancoraggio, le coordinate e lo stato.
