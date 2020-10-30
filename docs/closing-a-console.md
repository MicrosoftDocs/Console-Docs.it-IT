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
# <a name="closing-a-console"></a>Chiusura di una console

Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console. Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento. Dopo la chiamata a **FreeConsole** , il processo può usare [**AllocConsole**](allocconsole.md) per creare una nuova console o [**AttachConsole**](attachconsole.md) per connettersi a un'altra console.

Una console viene chiusa quando l'ultimo processo collegato termina o chiama [**FreeConsole**](freeconsole.md).
