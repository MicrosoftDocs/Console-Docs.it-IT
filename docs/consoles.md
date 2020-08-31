---
title: Console-desktop di Windows
description: Una console è un'applicazione che fornisce I/O alle applicazioni della riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059945"
---
# <a name="consoles"></a>Console

Una *console* (o *terminale*) è un'applicazione che fornisce I/O alle applicazioni in modalità carattere. Questo meccanismo indipendente dal processore semplifica la portabilità delle applicazioni in modalità carattere esistenti o la creazione di nuovi strumenti e applicazioni in modalità carattere.

Una console di è costituita da un buffer di input e uno o più buffer dello schermo. Il *buffer di input* contiene una coda di record di input, ognuno dei quali contiene informazioni su un evento di input. La coda di input include sempre gli eventi chiave-pressione e rilascio chiave. Può inoltre includere eventi del mouse (movimenti del puntatore e pressioni e versioni dei pulsanti) ed eventi durante i quali le azioni utente influiscono sulle dimensioni del buffer dello schermo attivo. Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console. Un qualsiasi numero di processi può condividere una console.

- [Creazione di una console](creation-of-a-console.md)
- [Connessione a una console](attaching-to-a-console.md)
- [Chiusura di una console](closing-a-console.md)
- [Handle della console](console-handles.md)
- [Buffer di input della console](console-input-buffer.md)
- [Buffer dello schermo della console](console-screen-buffers.md)
- [Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)
- [Selezione della console](console-selection.md)
- [Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)
