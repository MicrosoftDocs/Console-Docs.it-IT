---
title: Console-desktop di Windows
description: Una console è un'applicazione che fornisce I/O alle applicazioni della riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039119"
---
# <a name="consoles"></a>Console

Una *console* è un'applicazione che fornisce servizi di I/O alle applicazioni in modalità carattere.

Una console di è costituita da un buffer di input e uno o più buffer dello schermo. Il *buffer di input* contiene una coda di record di input, ognuno dei quali contiene informazioni su un evento di input. La coda di input include sempre gli eventi chiave-pressione e rilascio chiave. Può inoltre includere eventi del mouse (movimenti del puntatore e pressioni e versioni dei pulsanti) ed eventi durante i quali le azioni utente influiscono sulle dimensioni del buffer dello schermo attivo. Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console. Un qualsiasi numero di processi può condividere una console.

> [!TIP]
>Una concezione più ampia delle console e del modo in cui sono correlate ai terminali e alle applicazioni client da riga di comando sono reperibili nella Guida di **[orientamento dell'ecosistema](ecosystem-roadmap.md)** .

- [Creazione di una console](creation-of-a-console.md)
- [Collegamento a una console](attaching-to-a-console.md)
- [Chiusura di una console](closing-a-console.md)
- [Handle della console](console-handles.md)
- [Buffer di input della console](console-input-buffer.md)
- [Buffer dello schermo della console](console-screen-buffers.md)
- [Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)
- [Selezione nella console](console-selection.md)
- [Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)
