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
# <a name="high-level-console-modes"></a>Modalità console High-Level

Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console. Tutte le modalità di input della console seguenti sono abilitate per il buffer di input di una console quando viene creata una console:

- Modalità input linea
- Modalità di input elaborata
- Modalità input echo

Entrambe le modalità di output della console seguenti sono abilitate per un buffer dello schermo della console quando viene creato:

- Modalità output elaborata
- Wrapping in modalità di output EOL

Tutte e tre le modalità di input, insieme alla modalità output elaborata, sono progettate per essere utilizzate insieme. È consigliabile abilitare o disabilitare tutte queste modalità come gruppo. Quando tutti sono abilitati, l'applicazione viene definita in modalità "cotta", il che significa che la maggior parte dell'elaborazione viene gestita per l'applicazione. Quando tutti sono disabilitati, l'applicazione è in modalità "Raw", il che significa che l'input non viene filtrato e l'elaborazione viene lasciata all'applicazione.

Un'applicazione può usare la funzione [**GetConsoleMode**](getconsolemode.md) per determinare la modalità corrente del buffer di input o dello schermo di una console. È possibile abilitare o disabilitare una qualsiasi di queste modalità usando i valori seguenti nella funzione [**SetConsoleMode**](setconsolemode.md) . Si noti che l'impostazione della modalità di output di un buffer dello schermo non influisce sulla modalità di output di altri buffer dello schermo.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
