---
title: Modalità console Low-Level
description: I tipi di eventi di input segnalati nel buffer di input di una console dipendono dalle modalità di input del mouse e della finestra della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: acd68e9679f209349f3e0db6989ca905815525a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039539"
---
# <a name="low-level-console-modes"></a>Modalità console Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

I tipi di eventi di input segnalati nel buffer di input di una console dipendono dalle modalità di input del mouse e della finestra della console. La modalità di input elaborata della console determina il modo in cui il sistema gestisce la combinazione di tasti CTRL + C. Per impostare o recuperare lo stato delle modalità di input di una console, un'applicazione può specificare un handle del buffer di input della console in una chiamata alla funzione [**SetConsoleMode**](setconsolemode.md) o [**GetConsoleMode**](getconsolemode.md) . Le modalità seguenti vengono usate con gli handle di input della console.

| Mode | Descrizione |
|-|-|
| **Abilita \_ input del mouse \_**     | Controlla se gli eventi del mouse vengono segnalati nel buffer di input. Per impostazione predefinita, l'input del mouse è abilitato e l'input della finestra è disabilitato. La modifica di una di queste modalità influisca solo sugli input che si verificano dopo l'impostazione della modalità; gli eventi del mouse o della finestra in sospeso nel buffer di input non vengono scaricati. Il puntatore del mouse viene visualizzato indipendentemente dalla modalità del mouse.                                                |
| **Abilita \_ \_ input finestra**    | Controlla se gli eventi di ridimensionamento del buffer vengono segnalati nel buffer di input. Per impostazione predefinita, l'input del mouse è abilitato e l'input della finestra è disabilitato. La modifica di una di queste modalità influisca solo sugli input che si verificano dopo l'impostazione della modalità; gli eventi del mouse o della finestra in sospeso nel buffer di input non vengono scaricati. Il puntatore del mouse viene visualizzato indipendentemente dalla modalità del mouse.                                      |
| **Abilita \_ \_ input elaborato** | Controlla l'elaborazione dell'input per le applicazioni mediante le funzioni di I/O della console di alto livello. Tuttavia, se la modalità di input elaborata è abilitata, la combinazione di tasti CTRL + C non viene segnalata nel buffer di input della console. Viene invece passato alla funzione del gestore di controllo appropriata. Per altre informazioni sui gestori di controllo, vedere [gestori di controlli della console](console-control-handlers.md). |

Le modalità di output di un buffer dello schermo non influiscono sul comportamento delle funzioni di output di basso livello.
