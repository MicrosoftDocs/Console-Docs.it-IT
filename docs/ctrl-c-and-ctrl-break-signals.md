---
title: CTRL + C e CTRL + INTERROMPi segnali
description: Le combinazioni di tasti CTRL + C e CTRL + INTERr ricevono una gestione speciale dai processi della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059892"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>CTRL + C e CTRL + INTERROMPi segnali


Le combinazioni di tasti CTRL + C e CTRL + INTERr ricevono una gestione speciale dai processi della console. Per impostazione predefinita, quando una finestra della console dispone dello stato attivo della tastiera, CTRL + C o CTRL + INTERr viene considerato come un segnale (SIGINT o SIGBREAK) e non come input da tastiera. Per impostazione predefinita, questi segnali vengono passati a tutti i processi della console collegati alla console. (I processi scollegati non sono interessati). Il sistema crea un nuovo thread in ogni processo client per gestire l'evento. Il thread genera un'eccezione se è in corso il debug del processo. Il debugger può gestire l'eccezione o continuare con l'eccezione non gestita.

CTRL + INTERr viene sempre considerato come un segnale, ma un'applicazione può modificare il comportamento predefinito di CTRL + C in due modi che impediscono la chiamata delle funzioni del gestore:

- La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità di input di input ** \_ elaborata \_ ** per il buffer di input di una console, quindi CTRL + C viene segnalato come input da tastiera anziché come segnale.
- Quando [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) viene chiamato con valori **null** e **true** per i relativi parametri, il processo chiamante ignora i segnali CTRL + C. La normale elaborazione di CTRL + C viene ripristinata chiamando **SetConsoleCtrlHandler** con valori **null** e **false** . Questo attributo di ignorare o ignorare i segnali CTRL + C viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.

 

 




