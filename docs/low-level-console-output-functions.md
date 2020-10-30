---
title: Funzioni di output della console Low-Level
description: Le funzioni di output della console di basso livello forniscono l'accesso diretto alle celle di tipo carattere di un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 70782c7bdc6d009be97315d3405cd44e4e7aa866
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038559"
---
# <a name="low-level-console-output-functions"></a>Funzioni di output della console Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Le funzioni di output della console di basso livello forniscono l'accesso diretto alle celle di tipo carattere di un buffer dello schermo. Un set di funzioni legge o scrive in celle consecutive a partire da qualsiasi posizione nel buffer dello schermo della console. Un altro set di funzioni legge o scrive in blocchi rettangolari di celle.

Le funzioni seguenti leggono o scrivono in un numero specificato di celle di caratteri consecutivi in un buffer dello schermo, a partire da una cella specificata.

| Funzione | Descrizione |
|-|-|
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | Copia una stringa di caratteri Unicode o ANSI da un buffer dello schermo. |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Scrive una stringa di caratteri Unicode o ANSI in un buffer dello schermo. |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | Copia una stringa di testo e gli attributi di colore di sfondo da un buffer dello schermo. |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Scrive una stringa di attributi di colore di sfondo e di testo in un buffer dello schermo. |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | Scrive un singolo carattere Unicode o ANSI in un numero specificato di celle consecutive in un buffer dello schermo. |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | Scrive una combinazione di attributi di colore di sfondo e testo in un numero specificato di celle consecutive in un buffer dello schermo. |

Per tutte queste funzioni, quando viene rilevata l'ultima cella di una riga, la lettura o la scrittura di un ritorno a capo nella prima cella della riga successiva. Quando viene rilevata la fine dell'ultima riga del buffer dello schermo della console, le funzioni di scrittura ignorano tutti gli attributi o i caratteri non scritti, mentre le funzioni di lettura segnalano il numero di caratteri o attributi effettivamente scritti.

Le funzioni seguenti leggono o scrivono in blocchi rettangolari di celle di tipo carattere in una posizione specificata in un buffer dello schermo.

| Funzione | Descrizione |
|-|-|
| [**ReadConsoleOutput**](readconsoleoutput.md) | Copia i dati di tipo carattere e colore da un blocco specificato di celle del buffer dello schermo in un blocco specificato in un buffer di destinazione. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Scrive i dati di tipo carattere e colore in un blocco specificato di celle del buffer dello schermo da un blocco specificato in un buffer di origine. |

Queste funzioni considerano i buffer dello schermo e i buffer di origine o di destinazione come matrici bidimensionali di strutture di [**\_ informazioni char**](char-info-str.md) (contenenti i dati degli attributi di tipo carattere e colore per ogni cella). Le funzioni specificano la larghezza e l'altezza, in celle di tipo carattere, del buffer di origine o di destinazione e il puntatore al buffer viene considerato un puntatore alla cella di origine (0,0) della matrice bidimensionale. Le funzioni utilizzano una [**piccola struttura \_ Rect**](small-rect-str.md) per specificare il rettangolo a cui accedere nel buffer dello schermo della console e le coordinate della cella superiore sinistra nel buffer di origine o di destinazione determinano la posizione del rettangolo corrispondente nel buffer.

Queste funzioni ritagliano automaticamente il rettangolo del buffer dello schermo specificato per adattarsi ai limiti del buffer dello schermo della console. Se ad esempio il rettangolo specifica le coordinate in basso a destra (colonna 100, riga 50) e il buffer dello schermo della console è costituito solo da 80 colonne, le coordinate vengono ritagliate in modo che siano (colonna 79, riga 50). Analogamente, questo rettangolo modificato viene nuovamente ritagliato per adattarsi ai limiti del buffer di origine o di destinazione. Vengono specificate le coordinate del buffer dello schermo del rettangolo effettivo letto o scritto. Per un esempio che usa queste funzioni, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).

Nella figura è illustrata un'operazione [**ReadConsoleOutput**](readconsoleoutput.md) in cui il ritaglio si verifica quando il blocco viene letto dal buffer dello schermo della console e di nuovo quando il blocco viene copiato nel buffer di destinazione. La funzione segnala il rettangolo del buffer dello schermo effettivo da cui è stato copiato.

![finestra buffer dello schermo con buffer di destinazione](images/cscon-03.png)
