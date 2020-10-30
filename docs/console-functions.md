---
title: Funzioni console
description: Viene descritto un elenco completo di tutte le funzioni utilizzate per accedere a una console.
author: miniksa
ms.author: miniksa
ms.topic: hub-page
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 0ee2dde2c14a3d827aa2bc5e14f3cc65cf5fdc0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039239"
---
# <a name="console-functions"></a>Funzioni console

Per accedere a una console vengono usate le funzioni seguenti.

| Funzione | Descrizione |
|-|-|
| [**AddConsoleAlias**](addconsolealias.md) | Definisce un alias di console per il file eseguibile specificato. |
| [**AllocConsole**](allocconsole.md) | Alloca una nuova console per il processo chiamante. |
| [**AttachConsole**](attachconsole.md) | Connette il processo chiamante alla console del processo specificato. |
| [**ClosePseudoConsole**](closepseudoconsole.md) | Chiude un pseudoconsole dall'handle specificato. |
| [**CreatePseudoConsole**](createpseudoconsole.md) | Alloca un nuovo pseudoconsole per il processo chiamante. |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) | Crea un buffer dello schermo della console. |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | Imposta gli attributi del colore di sfondo e di testo per un numero specificato di celle di caratteri. |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | Scrive un carattere nel buffer dello schermo della console per un numero di volte specificato. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Svuota il buffer di input della console. |
| [**FreeConsole**](freeconsole.md) | Scollega il processo chiamante dalla relativa console. |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) | Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante. |
| [**GetConsoleAlias**](getconsolealias.md) | Recupera l'alias specificato per il file eseguibile specificato. |
| [**GetConsoleAliases**](getconsolealiases.md) | Recupera tutti gli alias della console definiti per il file eseguibile specificato. |
| [**GetConsoleAliasesLength**](getconsolealiaseslength.md) | Restituisce le dimensioni, in byte, del buffer necessarie per archiviare tutti gli alias della console per il file eseguibile specificato. |
| [**GetConsoleAliasExes**](getconsolealiasexes.md) | Recupera i nomi di tutti i file eseguibili con alias di console definiti. |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) | Restituisce la dimensione, in byte, del buffer necessario per archiviare i nomi di tutti i file eseguibili con alias di console definiti. |
| [**GetConsoleCP**](getconsolecp.md) | Recupera la tabella codici di input utilizzata dalla console di associata al processo chiamante. |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md) | Recupera le informazioni sulle dimensioni e sulla visibilità del cursore per il buffer dello schermo della console specificato. |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md) | Recupera la modalità di visualizzazione della console corrente. |
| [**GetConsoleFontSize**](getconsolefontsize.md) | Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato. |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md) | Recupera le impostazioni della cronologia per la console del processo chiamante. |
| [**GetConsoleMode**](getconsolemode.md) | Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console. |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) | Recupera il titolo originale per la finestra della console corrente. |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md) | Recupera la tabella codici di output utilizzata dalla console di associata al processo chiamante. |
| [**GetConsoleProcessList**](getconsoleprocesslist.md) | Recupera un elenco dei processi collegati alla console corrente. |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera le informazioni sul buffer dello schermo della console specificato. |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) | Recupera le informazioni estese sul buffer dello schermo della console specificato. |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) | Recupera le informazioni sulla selezione corrente della console. |
| [**GetConsoleTitle**](getconsoletitle.md) | Recupera il titolo per la finestra della console corrente. |
| [**GetConsoleWindow**](getconsolewindow.md) | Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante. |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md) | Recupera le informazioni sul tipo di carattere della console corrente. |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) | Recupera le informazioni estese sul tipo di carattere della console corrente. |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) | Recupera la dimensione della finestra della console più grande possibile. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Recupera il numero di record di input non letti nel buffer di input della console. |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente. |
| [**GetStdHandle**](getstdhandle.md) | Recupera un handle per l'input standard, l'output standard o il dispositivo di errore standard. |
| [**HandlerRoutine**](handlerroutine.md) | Funzione definita dall'applicazione utilizzata con la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . |
| [**PeekConsoleInput**](peekconsoleinput.md) | Legge i dati dal buffer di input della console specificato senza rimuoverlo dal buffer. |
| [**ReadConsole**](readconsole.md) | Legge l'input di caratteri dal buffer di input della console e lo rimuove dal buffer. |
| [**ReadConsoleInput**](readconsoleinput.md) | Legge i dati da un buffer di input della console e li rimuove dal buffer. |
| [**ReadConsoleOutput**](readconsoleoutput.md) | Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console. |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | Copia un numero specificato di attributi di colore di primo piano e di sfondo da celle consecutive di un buffer dello schermo della console. |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | Copia un numero di caratteri dalle celle consecutive di un buffer dello schermo della console. |
| [**ResizePseudoConsole**](resizepseudoconsole.md) | Ridimensiona i buffer interni per un pseudoconsole alla dimensione specificata. |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) | Sposta un blocco di dati in un buffer dello schermo. |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) | Imposta il buffer dello schermo specificato come il buffer dello schermo della console attualmente visualizzato. |
| [**SetConsoleCP**](setconsolecp.md) | Imposta la tabella codici di input utilizzata dalla console di associata al processo chiamante. |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) | Aggiunge o rimuove un [**HandlerRoutine**](handlerroutine.md) definito dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante. |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md) | Imposta la dimensione e la visibilità del cursore per il buffer dello schermo della console specificato. |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md) | Imposta la posizione del cursore nel buffer dello schermo della console specificato. |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md) | Imposta la modalità di visualizzazione del buffer dello schermo della console specificato. |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md) | Imposta le impostazioni della cronologia per la console del processo chiamante. |
| [**SetConsoleMode**](setconsolemode.md) | Imposta la modalità di input del buffer di input di una console o la modalità di output di un buffer dello schermo della console. |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md) | Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante. |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) | Imposta le informazioni estese sul buffer dello schermo della console specificato. |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Modifica la dimensione del buffer dello schermo della console specificato. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Imposta gli attributi di colore in primo piano (testo) e sfondo dei caratteri scritti nel buffer dello schermo della console. |
| [**SetConsoleTitle**](setconsoletitle.md) | Imposta il titolo per la finestra della console corrente. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md) | Imposta la dimensione e la posizione correnti della finestra di un buffer dello schermo della console. |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md) | Imposta le informazioni estese sul tipo di carattere della console corrente. |
| [**SetStdHandle**](setstdhandle.md) | Imposta l'handle per l'input standard, l'output standard o il dispositivo di errore standard. |
| [**WriteConsole**](writeconsole.md) | Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Scrive i dati direttamente nel buffer di input della console. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console. |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Copia un numero di attributi di colore di primo piano e di sfondo in celle consecutive di un buffer dello schermo della console. |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Copia un numero di caratteri in celle consecutive di un buffer dello schermo della console. |
