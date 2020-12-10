---
title: Segnali CTRL+C e CTRL+INTERR
description: Le combinazioni di tasti CTRL+C e CTRL+INTERR ricevono una specifica gestione da parte dei processi della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420190"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Segnali CTRL+C e CTRL+INTERR

Le combinazioni di tasti <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>INTERR</kbd> ricevono una specifica gestione da parte dei processi della console. Per impostazione predefinita, quando una finestra della console dispone dello stato attivo della tastiera, <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene considerato come segnale (SIGINT o SIGBREAK) e non come input da tastiera. Per impostazione predefinita, questi segnali vengono passati a tutti i processi della console collegati alla console. I processi scollegati non sono interessati. Vedere [**Creazione di una console**](creation-of-a-console.md). Il sistema crea un nuovo thread in ogni processo client per gestire l'evento. Il thread genera un'eccezione se è in corso il debug del processo. Il debugger può gestire l'eccezione o continuare a lasciarla non gestita.

<kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene sempre considerato come segnale, ma un'applicazione può modificare il comportamento predefinito di <kbd>CTRL</kbd>+<kbd>C</kbd> in due modi che impediscono la chiamata delle funzioni gestore:

- La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità di input **ENABLE\_PROCESSED\_INPUT** per un buffer di input della console, in modo che CTRL+C venga segnalato come input da tastiera anziché come segnale.
- Quando [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) viene chiamata con i valori **NULL** e **TRUE** per i relativi parametri, il processo chiamante ignora i segnali di CTRL+C. La normale elaborazione di CTRL+C viene ripristinata chiamando **SetConsoleCtrlHandler** con i valori **NULL** e **FALSE**. Questo attributo che consente di ignorare o meno i segnali di CTRL+C, viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.

Per altre informazioni sull'elaborazione di questi segnali, inclusi i timeout, vedere la documentazione della funzione di callback [**HandlerRoutine**](handlerroutine.md).
