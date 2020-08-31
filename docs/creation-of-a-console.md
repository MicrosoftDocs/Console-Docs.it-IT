---
title: Creazione di una console
description: Il sistema crea una nuova console quando avvia un processo della console, un processo in modalità carattere il cui punto di ingresso è la funzione principale.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.openlocfilehash: b3b4143596035fed6896243043853932ae68233f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059897"
---
# <a name="creation-of-a-console"></a>Creazione di una console


Il sistema crea una nuova console quando avvia un *processo della console*, un processo in modalità carattere il cui punto di ingresso è la funzione **principale** . Ad esempio, il sistema crea una nuova console all'avvio del processore dei comandi. Quando il processore dei comandi avvia un nuovo processo console, l'utente può specificare se il sistema crea una nuova console per il nuovo processo o se eredita la console del processore dei comandi.

Un processo può creare una console utilizzando uno dei metodi seguenti:

- Un processo della GUI o della console può usare la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con **Create \_ New \_ console** per creare un processo della console con una nuova console. Per impostazione predefinita, un processo console eredita la console padre e non vi è alcuna garanzia che l'input venga ricevuto dal processo per cui è stato progettato.
- Un'interfaccia utente grafica (GUI) o un processo console che non è attualmente collegato a una console di può utilizzare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console. I processi GUI non sono collegati a una console quando vengono creati. I processi della console non sono collegati a una console se vengono creati utilizzando [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con ** \_ processo scollegato**.

In genere, un processo USA [**AllocConsole**](allocconsole.md) per creare una console quando si verifica un errore che richiede l'interazione con l'utente. Un processo GUI, ad esempio, può creare una console quando si verifica un errore che impedisce di usare l'interfaccia grafica normale oppure un processo console che in genere non interagisce con l'utente può creare una console per visualizzare un errore.

Un processo può anche creare una console specificando il flag **Crea \_ nuova \_ console** in una chiamata a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425). Questo metodo crea una nuova console accessibile al processo figlio ma non al processo padre. Le console separate consentono ai processi padre e figlio di interagire con l'utente senza conflitti. Se questo flag non viene specificato quando viene creato un processo della console, entrambi i processi sono collegati alla stessa console e non è garantito che il processo corretto riceva l'input desiderato. Le applicazioni possono impedire confusione creando processi figlio che non ereditano gli handle del buffer di input o abilitando solo un processo figlio alla volta per ereditare un handle del buffer di input, impedendo al processo padre di leggere l'input della console fino al completamento dell'elemento figlio.

La creazione di una nuova console comporta la creazione di una nuova finestra della console, nonché I buffer dello schermo di I/O separati. Il processo associato alla nuova console usa la funzione [**GetStdHandle**](getstdhandle.md) per ottenere gli handle dei buffer di input e dello schermo della nuova console. Questi handle consentono al processo di accedere alla console.

Quando un processo USA [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), può specificare una struttura [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) , i cui membri controllano le caratteristiche della prima nuova console (se presente) creata per il processo figlio. La struttura **STARTUPINFO** specificata nella chiamata a **CreateProcess** influisca su una console creata se viene specificato il flag **Create \_ New \_ console** . Influiscono anche su una console creata se il processo figlio usa successivamente [**AllocConsole**](allocconsole.md). È possibile specificare le seguenti caratteristiche della console:

- Dimensioni della nuova finestra della console, in celle di tipo carattere
- Posizione della nuova finestra della console, in coordinate pixel dello schermo
- Dimensioni del buffer dello schermo della nuova console, in celle di tipo carattere
- Attributi del colore di sfondo e di testo del buffer dello schermo della nuova console
- Nome visualizzato per la barra del titolo della finestra della nuova console

Il sistema usa i valori predefiniti se i valori [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) non sono specificati. Un processo figlio può utilizzare la funzione [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) per determinare i valori nella struttura **STARTUPINFO** .

Un processo non può modificare la posizione della finestra della console sullo schermo, ma sono disponibili le funzioni console seguenti per impostare o recuperare le altre proprietà specificate nella struttura [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) .


| Funzione                                                         | Descrizione                                                          |
|------------------------------------------------------------------|----------------------------------------------------------------------|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera le dimensioni della finestra, le dimensioni del buffer dello schermo e gli attributi di colore. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)             | Modifica la dimensione della finestra della console.                              |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Modifica la dimensione del buffer dello schermo della console.                       |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md)       | Imposta gli attributi di colore.                                           |
| [**SetConsoleTitle**](setconsoletitle.md)                       | Imposta il titolo della finestra della console.                                       |
| [**GetConsoleTitle**](getconsoletitle.md)                       | Recupera il titolo della finestra della console.                                  |




Un processo può usare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi da una console ereditata o da una console creata da [**AllocConsole**](allocconsole.md).








