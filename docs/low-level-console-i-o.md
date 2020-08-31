---
title: I/O console di basso livello
description: Le funzioni di I/O della console di basso livello espandono il controllo di un'applicazione sull'I/O della console consentendo l'accesso diretto ai buffer di input e dello schermo di una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b548a188189b597a270faac1cfbc83a2af699fab
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060404"
---
# <a name="low-level-console-io"></a>I/O console di basso livello


Le funzioni di I/O della console di basso livello espandono il controllo di un'applicazione sull'I/O della console consentendo l'accesso diretto ai buffer di input e dello schermo di una console. Queste funzioni consentono a un'applicazione di eseguire le attività seguenti:

- Ricevere input sugli eventi di ridimensionamento del mouse e del buffer
- Ricevere informazioni estese sugli eventi di input da tastiera
- Scrivere record di input nel buffer di input
- Legge i record di input senza rimuoverli dal buffer di input
- Determinare il numero di eventi in sospeso nel buffer di input
- Svuotare il buffer di input
- Lettura e scrittura di stringhe di caratteri Unicode o ANSI in una posizione specificata in un buffer dello schermo
- Lettura e scrittura di stringhe di testo e di attributi di colore di sfondo in una posizione specificata del buffer dello schermo
- Lettura e scrittura di blocchi rettangolari di dati di tipo carattere e colore in una posizione specificata del buffer dello schermo
- Scrivere un singolo carattere Unicode o ANSI o una combinazione di attributi di colore di sfondo e testo in un numero specificato di celle consecutive a partire da una posizione specificata del buffer dello schermo

Per altre informazioni, vedere gli argomenti seguenti:

- [Modalità console](console-modes.md)
- [Modalità console di basso livello](low-level-console-modes.md)
- [Funzioni di input della console di basso livello](low-level-console-input-functions.md)
- [Funzioni di output della console di basso livello](low-level-console-output-functions.md)

 

 




