---
title: Creazione di una console
description: Il sistema crea una nuova console quando avvia un processo della console, un processo in modalità carattere il cui punto di ingresso è la funzione principale.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.localizationpriority: high
ms.openlocfilehash: bf7993874c4f7c7031dbbcc9ce53a0610157eb75
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357921"
---
# <a name="creation-of-a-console"></a>Creazione di una console

Il sistema crea una nuova console quando avvia un *processo della console*, un processo in modalità carattere il cui punto di ingresso è la funzione **principale**. Ad esempio, il sistema crea una nuova console quando avvia il processore dei comandi `cmd.exe`. Quando il processore dei comandi avvia un nuovo processo della console, l'utente può specificare se il sistema crea una nuova console per il nuovo processo o se eredita la console del processore dei comandi.

Un processo può creare una console usando uno dei metodi seguenti:

- Un processo dell'interfaccia utente grafica o della console può usare la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con **CREATE\_NEW\_CONSOLE** per creare un processo della console con una nuova console. Per impostazione predefinita, un processo della console eredita la console padre e non vi è alcuna garanzia che l'input venga ricevuto dal processo per cui è stato progettato.
- Un processo dell'interfaccia utente grafica o della console che non è attualmente collegato a una console può usare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console. Quando vengono creati, i processi dell'interfaccia utente grafica non sono collegati a una console. I processi della console non sono collegati a una console se vengono creati usando [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) con **DETACHED\_PROCESS**.

In genere, un processo usa [**AllocConsole**](allocconsole.md) per creare una console quando si verifica un errore che richiede l'interazione con l'utente. Un processo dell'interfaccia utente grafica, ad esempio, può creare una console quando si verifica un errore che impedisce di usare l'interfaccia grafica normale oppure un processo della console, che in genere non interagisce con l'utente, può creare una console per visualizzare un errore.

Un processo può creare una console anche specificando il contrassegno **CREATE\_NEW\_CONSOLE** in una chiamata a [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa). Questo metodo crea una nuova console accessibile al processo figlio, ma non al processo padre. Console separate consentono ai processi padre e figlio di interagire con l'utente senza conflitti. Se questo contrassegno non viene specificato al momento della creazione di un processo della console, entrambi i processi vengono collegati alla stessa console e non è garantito che il processo corretto riceva l'input previsto. Le applicazioni possono impedire che si generi confusione creando processi figlio che non ereditano gli handle del buffer di input o abilitando solo un processo figlio alla volta per ereditare un handle del buffer di input, impedendo al processo padre di leggere l'input della console fino al completamento dell'elemento figlio.

La creazione di una nuova console comporta la creazione di una nuova finestra della console, nonché buffer dello schermo di I/O separati. Il processo associato alla nuova console usa la funzione [**GetStdHandle**](getstdhandle.md) per ottenere gli handle dei buffer di input e dello schermo della nuova console. Questi handle consentono al processo di accedere alla console.

Quando un processo usa [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), può specificare una struttura [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa), i cui membri controllano le caratteristiche della prima nuova console (se presente) creata per il processo figlio. La struttura **STARTUPINFO**, specificata nella chiamata a **CreateProcess**, influisce su una console creata se è stato specificato il contrassegno **CREATE\_NEW\_CONSOLE**. Influisce, inoltre, su una console creata se il processo figlio usa successivamente [**AllocConsole**](allocconsole.md). È possibile specificare le caratteristiche della console seguenti:

- Dimensioni della nuova finestra della console, in celle di tipo carattere
- Posizione della nuova finestra della console, in coordinate pixel dello schermo
- Dimensioni del buffer dello schermo della console, in celle di tipo carattere
- Attributi del colore di sfondo e di testo del buffer dello schermo della nuova console
- Nome visualizzato per la barra del titolo della finestra della nuova console

Il sistema usa valori predefiniti se non vengono specificati i valori di [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa). Un processo figlio può usare la funzione [**GetStartupInfo**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getstartupinfow) per determinare i valori nella relativa struttura **STARTUPINFO**.

Un processo non può modificare la posizione della finestra della console sullo schermo, ma sono disponibili le funzioni della console seguenti per impostare o recuperare le altre proprietà specificate nella struttura [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

| Funzione | Descrizione |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera le dimensioni della finestra, le dimensioni del buffer dello schermo e gli attributi del colore. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Modifica le dimensioni della finestra della console.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Modifica le dimensioni del buffer dello schermo della console. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Imposta gli attributi del colore.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Imposta il titolo della finestra della console. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Recupera il titolo della finestra della console.  |

Un processo può usare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi da una console ereditata o da una console creata da [**AllocConsole**](allocconsole.md).

Un processo può usare la funzione [**AttachConsole**](attachconsole.md) per collegarsi a un'altra sessione della console esistente dopo aver usato [**FreeConsole**](freeconsole.md) per scollegarsi dalla propria sessione (o se non è presente alcuna sessione collegata).