---
title: Funzioni di input della console di basso livello
description: Un buffer di funzioni di input della console di basso livello contiene record di input che possono includere informazioni su tastiera, mouse, ridimensionamento del buffer, stato attivo e eventi di menu.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- base.low\_level\_console\_input\_functions
- consoles.low\_level\_console\_input\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
ms.openlocfilehash: 9e9e576b244e978dad1dd2018a194e7a05fbce85
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060033"
---
# <a name="low-level-console-input-functions"></a>Funzioni di input della console di basso livello


Un buffer di funzioni di input della console di basso livello contiene record di input che possono includere informazioni su tastiera, mouse, ridimensionamento del buffer, stato attivo e eventi di menu. Le funzioni di basso livello forniscono accesso diretto al buffer di input, a differenza delle funzioni di alto livello che filtrano ed elaborano i dati del buffer di input, ignorando tutti gli input tranne quelli da tastiera.

Sono disponibili cinque funzioni di basso livello per l'accesso al buffer di input di una console:

- [**ReadConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

Le funzioni [**ReadConsoleInput**](readconsoleinput.md), [**PeekConsoleInput**](peekconsoleinput.md)e [**WriteConsoleInput**](writeconsoleinput.md) utilizzano la struttura [**del \_ record di input**](input-record-str.md) per leggere o scrivere in un buffer di input.

Di seguito sono riportate le descrizioni delle funzioni di input della console di basso livello.


| Funzione                                                               | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleInput**](readconsoleinput.md)                           | Legge e rimuove i record di input da un buffer di input. La funzione non restituisce un risultato fino a quando non è disponibile almeno un record da leggere. Quindi, tutti i record disponibili vengono trasferiti nel buffer del processo chiamante fino a quando non sono disponibili altri record o il numero di record specificato è stato letto. I record non letti rimangono nel buffer di input per la successiva operazione di lettura. La funzione indica il numero totale di record che sono stati letti. Per un esempio in cui viene usato [**ReadConsoleInput**](readconsoleinput.md), vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md). |
| [**PeekConsoleInput**](peekconsoleinput.md)                           | Legge senza rimuovere i record di input in sospeso in un buffer di input. Tutti i record disponibili fino al numero specificato vengono copiati nel buffer del processo chiamante. Se non sono disponibili record, la funzione restituisce immediatamente il risultato. La funzione indica il numero totale di record che sono stati letti.                                                                                                                                                                                                                                                                                              |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Determina il numero di record di input non letti in un buffer di input.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [**WriteConsoleInput**](writeconsoleinput.md)                         | Inserisce i record di input nel buffer di input dietro tutti i record in sospeso nel buffer. Il buffer di input aumenta in modo dinamico, se necessario, per mantenere il numero di record scritti. Per usare questa funzione, l'handle del buffer di input specificato deve avere il \_ diritto di accesso in lettura generico.                                                                                                                                                                                                                                                                                                                           |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)             | Elimina tutti gli eventi non letti nel buffer di input. Per usare questa funzione, l'handle del buffer di input specificato deve avere il \_ diritto di accesso in lettura generico.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |




Un thread del processo di un'applicazione può eseguire un'operazione di attesa per attendere che l'input sia disponibile in un buffer di input. Per avviare un'operazione di attesa, specificare un handle per il buffer di input in una chiamata a una delle [funzioni di attesa](https://msdn.microsoft.com/library/windows/desktop/ms687069). Queste funzioni possono restituire quando viene segnalato lo stato di uno o più oggetti. Lo stato di un handle di input della console diventa segnalato quando sono presenti record non letti nel buffer di input. Lo stato viene reimpostato su non segnalato quando il buffer di input diventa vuoto. Se non è disponibile alcun input, il thread chiamante entra in uno stato di attesa efficiente, consumando pochissimo tempo del processore mentre è in attesa che le condizioni dell'operazione di attesa vengano soddisfatte.








