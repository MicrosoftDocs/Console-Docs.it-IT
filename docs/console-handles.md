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
ms.openlocfilehash: 817c902426ac09fdd246f8d1281528ee5dfcab06
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358071"
---
# <a name="console-handles"></a>Handle della console

Un processo della console usa gli handle per accedere ai buffer di input e dello schermo della relativa console. Un processo può usare la funzione [**GetStdHandle**](getstdhandle.md), [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) per aprire uno di questi handle.

La funzione [**GetStdHandle**](getstdhandle.md) offre un meccanismo per recuperare gli handle di input standard (`STDIN`), di output standard (`STDOUT`) e di errore standard (`STDERR`) associati a un processo. Durante la creazione della console, il sistema crea questi handle. Inizialmente, `STDIN` è un handle per il buffer di input della console e `STDOUT` e `STDERR` sono handle del buffer dello schermo attivo della console. Tuttavia, la funzione [**SetStdHandle**](setstdhandle.md) può reindirizzare gli handle standard modificando l'handle associato a `STDIN`, `STDOUT` o `STDERR`. Poiché gli handle standard del padre vengono ereditati da qualsiasi processo figlio, le chiamate successive a **GetStdHandle** restituiscono l'handle reindirizzato. Un handle restituito da **GetStdHandle** può pertanto fare riferimento a un elemento diverso dall'I/O della console. Prima di creare un processo figlio, ad esempio, un processo padre può usare **SetStdHandle** per impostare un handle di pipe in modo che sia l'handle `STDIN` ereditato dal processo figlio. Quando il processo figlio chiama **GetStdHandle**, ottiene l'handle di pipe. Questo significa che il processo padre può controllare gli handle standard del processo figlio. Gli handle restituiti da **GetStdHandle** dispongono dell'accesso `GENERIC_READ | GENERIC_WRITE`, a meno che non sia stato usato **SetStdHandle** per impostare un livello di accesso inferiore per l'handle standard.

I valori degli handle restituiti da [**GetStdHandle**](getstdhandle.md) non sono 0, 1 e 2, pertanto le costanti di flusso predefinite standard in Stdio.h (`STDIN`, `STDOUT` e `STDERR`) non possono essere usate in funzioni che richiedono un handle della console.

La funzione [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) consente a un processo di ottenere un handle per il buffer di input e il buffer dello schermo attivo della relativa console, anche se `STDIN` e `STDOUT` sono stati reindirizzati. Per aprire un handle per il buffer di input di una console, specificare il valore `CONIN$` in una chiamata a **CreateFile**. Per aprire un handle per il buffer dello schermo attivo di una console, specificare il valore `CONOUT$` in una chiamata a **CreateFile**. **CreateFile** consente di specificare l'accesso in lettura/scrittura dell'handle restituito.

La funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) crea un nuovo buffer dello schermo e restituisce un handle. Questo handle può essere usato in qualsiasi funzione che accetta un handle per l'output della console. Il nuovo buffer dello schermo non è attivo (visualizzato) fino a quando non viene specificato il relativo handle in una chiamata alla funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). Si noti che la modifica del buffer dello schermo attivo non influisce sull'handle restituito da [**GetStdHandle**](getstdhandle.md). Analogamente, l'uso di [**SetStdHandle**](setstdhandle.md) per modificare l'handle `STDOUT` non influisce sul buffer dello schermo attivo.

Gli handle della console restituiti da [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) e [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) possono essere usati in qualsiasi funzione della console che richiede un handle per il buffer di input o il buffer dello schermo di una console. Gli handle restituiti da [**GetStdHandle**](getstdhandle.md) possono essere utilizzati dalle funzioni della console se non sono stati reindirizzati per fare riferimento a elementi diversi dall'I/O della console. Se invece un handle standard è stato reindirizzato per fare riferimento a un file o a una pipe, può essere usato solo dalle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile). [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) può essere utile per determinare il tipo di dispositivo a cui fa riferimento l'handle. Un handle della console si presenta come `FILE_TYPE_CHAR`.

Un processo può usare la funzione [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) per creare un handle della console duplicato con accesso o ereditarietà differente rispetto all'handle originale. Si noti, tuttavia, che un processo può creare un handle della console duplicato solo a proprio uso. Questo comportamento è diverso da quello degli altri tipi di handle, ad esempio file, pipe o oggetti mutex, per i quali **DuplicateHandle** può creare un duplicato valido per un processo diverso.
L'accesso a una console deve essere condiviso durante la [creazione](creation-of-a-console.md) dell'altro processo o può essere richiesto dall'altro processo tramite il meccanismo [**AttachConsole**](attachconsole.md).

Per chiudere un handle della console, un processo può usare la funzione [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle).