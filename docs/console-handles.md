---
title: Handle della console
description: Un processo della console usa gli handle per accedere ai buffer di input e dello schermo della relativa console, incluse le funzioni GetStdHandle, CreateFile o CreateConsoleScreenBuffer.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.localizationpriority: high
ms.openlocfilehash: acc7d65e15451fc2804dc1782644c1ccbaa30e28
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420240"
---
# <a name="console-handles"></a>Handle della console

Un processo console usa gli handle per accedere ai buffer di input e dello schermo della relativa console. Un processo può utilizzare la funzione [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) per aprire uno di questi handle.

La funzione [**GetStdHandle**](getstdhandle.md) fornisce un meccanismo per il recupero dell'input standard ( `STDIN` ), dell'output standard ( `STDOUT` ) e degli handle di errore standard ( `STDERR` ) associati a un processo. Durante la creazione della console, il sistema crea questi handle. Inizialmente, `STDIN` è un handle per il buffer di input della console e `STDOUT` e `STDERR` sono handle del buffer dello schermo attivo della console. Tuttavia, la funzione [**SetStdHandle**](setstdhandle.md) può reindirizzare gli handle standard modificando l'handle associato a `STDIN` , `STDOUT` o `STDERR` . Poiché gli handle standard del padre vengono ereditati da qualsiasi processo figlio, le chiamate successive a **GetStdHandle** restituiscono l'handle reindirizzato. Un handle restituito da **GetStdHandle** può, pertanto, fare riferimento a un elemento diverso da I/O della console. Prima di creare un processo figlio, ad esempio, un processo padre può usare **SetStdHandle** per impostare un handle di pipe come `STDIN` handle ereditato dal processo figlio. Quando il processo figlio chiama **GetStdHandle**, ottiene l'handle della pipe. Questo significa che il processo padre può controllare gli handle standard del processo figlio. Gli handle restituiti da **GetStdHandle** hanno `GENERIC_READ | GENERIC_WRITE` accesso a meno che non sia stato usato **SetStdHandle** per impostare l'handle standard in modo che disponga di un accesso minore.

Il valore degli handle restituiti da [**GetStdHandle**](getstdhandle.md) non è 0, 1 e 2, pertanto le costanti di flusso predefinite standard in stdio. h ( `STDIN` , `STDOUT` e `STDERR` ) non possono essere usate in funzioni che richiedono un handle della console.

La funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) consente a un processo di ottenere un handle per il buffer di input della console e il buffer dello schermo attivo, anche se `STDIN` e `STDOUT` sono stati reindirizzati. Per aprire un handle per il buffer di input di una console, specificare il `CONIN$` valore in una chiamata a **CreateFile**. Specificare il `CONOUT$` valore in una chiamata a **CreateFile** per aprire un handle per il buffer dello schermo attivo di una console. **CreateFile** consente di specificare l'accesso in lettura/scrittura dell'handle restituito.

La funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crea un nuovo buffer dello schermo e restituisce un handle. Questo handle può essere usato in qualsiasi funzione che accetta un handle per l'output della console. Il nuovo buffer dello schermo non è attivo (visualizzato) finché non viene specificato il relativo handle in una chiamata alla funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Si noti che la modifica del buffer dello schermo attivo non influisce sull'handle restituito da [**GetStdHandle**](getstdhandle.md). Analogamente, l'utilizzo di [**SetStdHandle**](setstdhandle.md) per modificare l' `STDOUT` handle non influisce sul buffer dello schermo attivo.

Gli handle della console restituiti da [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) e [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) possono essere usati in qualsiasi funzione console che richiede un handle per il buffer di input di una console o di un buffer dello schermo della console. Gli handle restituiti da [**GetStdHandle**](getstdhandle.md) possono essere usati dalle funzioni della console se non sono stati reindirizzati per fare riferimento a elementi diversi dall'I/O della console. Se un handle standard è stato reindirizzato per fare riferimento a un file o a una pipe, tuttavia, l'handle può essere usato solo dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . [**FileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) può contribuire a determinare a quale tipo di dispositivo fa riferimento l'handle. Un handle della console presenta come `FILE_TYPE_CHAR` .

Un processo può utilizzare la funzione [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) per creare un handle console duplicato con accesso o ereditarietà diversi dall'handle originale. Si noti, tuttavia, che un processo può creare un handle di console duplicato solo per uso personale. Questo comportamento è diverso da quello degli altri tipi di handle (ad esempio, file, pipe o oggetti mutex), per i quali **DuplicateHandle** può creare un duplicato valido per un processo diverso.
L'accesso a una console deve essere condiviso durante la [creazione](creation-of-a-console.md) dell'altro processo oppure può essere richiesto da un altro processo tramite il meccanismo [**AttachConsole**](attachconsole.md) .

Per chiudere un handle di console, un processo può usare la funzione [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .
