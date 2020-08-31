---
title: Modalità console
description: Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060097"
---
# <a name="console-modes"></a>Modalità console


Associato a ogni buffer di input della console è un set di modalità di input che influiscono sulle operazioni di input. Analogamente, ogni buffer dello schermo della console dispone di un set di modalità di output che influiscono sulle operazioni di output. Le modalità di input possono essere divise in due gruppi: quelli che interessano le funzioni di input di alto livello e quelle che interessano le funzioni di input di basso livello. Le modalità di output influiscono solo sulle applicazioni che utilizzano le funzioni di output di alto livello.

La funzione [**GetConsoleMode**](getconsolemode.md) segnala la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo. La funzione [**SetConsoleMode**](setconsolemode.md) imposta la modalità corrente di un buffer di input della console o di un buffer dello schermo. Se una console dispone di più buffer dello schermo, le modalità di output di ciascuna di esse possono essere diverse. Un'applicazione può modificare le modalità I/O in qualsiasi momento. Per ulteriori informazioni sulle modalità della console che interessano le operazioni di I/O di alto livello e di basso livello, vedere [modalità console di alto livello](high-level-console-modes.md) e [modalità console di basso livello](low-level-console-modes.md).

La funzione [**GetConsoleDisplayMode**](getconsoledisplaymode.md) indica se la console corrente è in modalità schermo intero e se comunica direttamente con l'hardware.

 

 




