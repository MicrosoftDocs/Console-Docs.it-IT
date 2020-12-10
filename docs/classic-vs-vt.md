---
title: Confronto tra API di console classica e sequenze di terminale virtuale
description: Confronta la superficie dell'API della console Win32 classica e il concetto di sequenze di terminale virtuale, talvolta note anche come sequenze di escape, per la scrittura di applicazioni da riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminale, terminale virtuale, sequenze di escape, vt, vt100, api della console
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420180"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>Confronto tra API di console classica e sequenze di terminale virtuale

Si consiglia di sostituire l'**API della console di Windows** classica con le **sequenze di terminale virtuale**. Questo articolo illustra la differenza tra i due elementi e i motivi del consiglio proposto.

## <a name="definitions"></a>Definizioni

La superficie dell' **[API della console di Windows classica](console-functions.md)** è definita come serie di interfacce funzionali del linguaggio C in `kernel32.dll` con il termine "console" nel nome.

Le **[sequenze di terminale virtuale](console-virtual-terminal-sequences.md)** sono definite come linguaggio di comandi incorporati nei flussi di input e output standard. Le sequenze di terminale virtuale usano caratteri di escape non stampabili per i comandi di segnalazione interfogliati con testo stampabile normale.

## <a name="history"></a>Cronologia

La **console di Windows** fornisce un'ampia superficie di API per le applicazioni da riga di comando client per modificare sia il buffer di visualizzazione dell'output che il buffer di input dell'utente. Altre piattaforme non Windows, tuttavia, non hanno mai concesso questo approccio specifico basato su API ai propri ambienti da riga di comando, optando invece per sequenze di terminale virtuale incorporate nei flussi di input e output standard. *Per un certo periodo, Microsoft ha supportato questo comportamento anche nelle prime edizioni di DOS e Windows tramite un driver denominato ANSI.SYS.*

Le **sequenze di terminale virtuale** (in un'ampia gamma di dialetti) supportano invece le operazioni dell'ambiente da riga di comando per tutte le altre piattaforme. Queste sequenze sono radicate in uno [standard ECMA](https://www.ecma-international.org/publications/standards/Ecma-048.htm) e in una serie di estensioni di molti fornitori che eseguono il tracciamento dei terminali di Digital Equipment Corporation e Tektronix, fino a terminali software più moderni e comuni, come [xterm](https://invisible-island.net/xterm/). Molte estensioni sono disponibili nel dominio della sequenza di terminale virtuale e alcune sequenze sono più diffuse rispetto ad altre, ma è possibile affermare che questo è il linguaggio di comando standard a livello globale per le esperienze da riga di comando con un subset noto supportato praticamente da qualsiasi terminale e applicazione client da riga di comando.

## <a name="cross-platform-support"></a>Supporto multipiattaforma

Le **sequenze di terminale virtuale** sono supportate in modalità nativa tra piattaforme, rendendo le applicazioni di terminale e le utilità da riga di comando facilmente portabili tra le versioni e le varianti dei sistemi operativi, ad eccezione di Windows.

Le **API della console di Windows**, invece, sono supportate solo in Windows. Quando si tenta di trasferire le utilità da riga di comando da una piattaforma a un'altra, è necessario scrivere una libreria di traduzione o un adattatore completo tra Windows e il terminale virtuale, o viceversa.

### <a name="remote-access"></a>Accesso remoto

Le **sequenze di terminale virtuale** contengono un vantaggio importante per l'accesso remoto. Non richiedono operazioni aggiuntive per il trasporto o l'esecuzione di Remote Procedure Call oltre a quelle richieste per configurare una connessione remota standard da riga di comando. La semplice connessione di un canale di trasporto in uscita e in entrata (o un canale bidirezionale singolo) su una pipe, un socket, un file, una porta seriale o qualsiasi altro dispositivo è sufficiente per trasferire completamente tutte le informazioni necessarie per un'applicazione che comunica queste sequenze a un host remoto.

Le **API della console di Windows**, invece, risultano accessibili solo sul computer locale e qualsiasi tentativo di eseguirne la modalità remota comporta la necessità di creare un intero livello di interfaccia di chiamata e trasporto remoto oltre a un semplice canale.

### <a name="separation-of-concerns"></a>Separazione delle problematiche

Alcune **API della console di Windows** forniscono accesso di basso livello ai buffer di input e output o alle funzioni di convenienza per le righe di comando interattive. Questo potrebbe includere gli alias e la cronologia dei comandi programmati nel sottosistema della console e nell'ambiente host, anziché all'interno dell'applicazione client da riga di comando.

In **altre piattaforme**, invece, la memorizzazione dello stato corrente dell'applicazione e della funzionalità di convenienza è responsabilità dell'utilità da riga di comando o della shell stessa.

Poiché la **console di Windows** gestisce questa responsabilità nell'host e nell'API della console la scrittura di un'applicazione da riga di comando con queste funzionalità risulta più semplice e veloce ed elimina il problema di dover ricordare lo stato del disegno o la gestione delle funzionalità di convenienza per la modifica. In questo modo, tuttavia, è quasi impossibile connettere le attività in modalità remota tra piattaforme, versioni o scenari, a causa delle variazioni delle implementazioni e della disponibilità. Questo metodo di gestione della responsabilità rende anche l'esperienza interattiva finale di queste applicazioni da riga di comando di Windows completamente dipendente dall'implementazione, dalle priorità e dal ciclo di rilascio dell'host della console.

Ad esempio, le funzionalità avanzate di modifica della linea, come l'evidenziazione della sintassi e la selezione complessa, sono possibili solo quando un'applicazione da riga di comando gestisce i problemi di modifica. La console non può disporre di un contesto sufficiente alla comprensione completa di questi scenari. Capacità invece propria dell'applicazione client.

Altre piattaforme usano, invece, le **sequenze di terminale virtuale** per gestire queste attività e la comunicazione del terminale virtuale tramite librerie lato client riutilizzabili, ad esempio [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) e [ncurses](https://invisible-island.net/ncurses/ncurses.html). Il terminale finale è responsabile solo della visualizzazione delle informazioni e della ricezione dell'input tramite il canale di comunicazione bidirezionale.

### <a name="wrong-way-verbs"></a>Verbi in modo errato

Con la **console di Windows**, alcune azioni possono essere eseguite nella direzione opposta a quella naturale sui flussi di input e output. Questo consente alle applicazioni da riga di comando di Windows di evitare il problema di gestire i propri buffer. Consente inoltre alle app da riga di comando di Windows di eseguire operazioni avanzate, ad esempio simulando/inserendo input per conto di un utente o leggendo parte della cronologia degli elementi scritti.

Sebbene in questo modo si fornisca ulteriore potenziale alle applicazioni Windows che operano in un contesto utente specifico in un singolo computer, si fornisce anche un vettore per valicare livelli di sicurezza e privilegi o domini se usati in determinati scenari. Questi scenari includono il funzionamento tra contesti nello stesso computer o tra contesti in un altro computer o ambiente.

Altre piattaforme, che usano le **sequenze di terminale virtuale**, non consentono questa attività. Pertanto, il consiglio di eseguire la transizione dalla console di Windows classica alle sequenze di terminale virtuale è finalizzato a convergere con questa strategia sia per motivi di interoperabilità che di sicurezza.

### <a name="direct-window-access"></a>Accesso diretto alla finestra

La **superficie dell'API della console di Windows** fornisce l'handle della finestra specifico per la finestra di hosting. Questo consente a un'utilità da riga di comando di eseguire operazioni di finestra avanzate raggiungendo l'ampia gamma di API Win32 consentite in un handle della finestra. Queste API Win32 possono modificare lo stato della finestra, il frame, l'icona o altre proprietà della finestra.

Su altre piattaforme, invece, con le **sequenze di terminale virtuale**, è possibile eseguire una serie di comandi limitati sulla finestra. Questi comandi possono eseguire operazioni quali la modifica delle dimensioni della finestra o del titolo visualizzato, ma devono essere eseguite nella stessa banda e sotto lo stesso controllo del resto del flusso.

Man mano che Windows si è evoluto, i controlli di sicurezza e le restrizioni sugli handle della finestra sono aumentati. Inoltre, la natura e l'esistenza di un handle della finestra indirizzabile all'applicazione su qualsiasi elemento dell'interfaccia utente specifico si sono evolute, soprattutto con l'aumento del supporto di piattaforme e fattori di forma del dispositivo. In questo modo, l'accesso diretto alla finestra per le applicazioni da riga di comando diventa fragile nel momento in cui la piattaforma e le esperienze mutano.

### <a name="unicode"></a>Unicode

UTF-8 è la codifica accettata per i dati Unicode in quasi tutte le piattaforme moderne, in quanto rappresenta il giusto equilibrio tra portabilità, dimensioni di archiviazione e tempo di elaborazione. Tuttavia, Windows ha scelto in passato UTF-16 come codifica primaria per i dati Unicode. Il supporto per UTF-8 è in aumento in Windows e l'uso di questi formati Unicode non impedisce l'utilizzo di altre codifiche.

La piattaforma della **console di Windows** è supportata e continuerà a supportare tutte le tabelle codici e le codifiche esistenti. Se necessario, usare la codifica UTF-16 per la massima compatibilità tra le versioni di Windows ed eseguire la conversione algoritmica con UTF-8. È in corso un miglioramento del supporto di UTF-8 per il sistema della console.

Il supporto UTF-16 nella console può essere usato senza alcuna configurazione aggiuntiva tramite la variante _W_ di tutte le API della console ed è una scelta più probabile per le applicazioni già in formato UTF-16 attraverso la comunicazione con `wchar_t` e la variante _W_ di altri prodotti e funzioni della piattaforma Microsoft e Windows.

Il supporto UTF-8 nella console può essere usato tramite la variante _A_ delle API della console per gli handle della console, dopo aver impostato la tabella codici su `65001` o `CP_UTF8` con i metodi [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**SetConsoleCP**](setconsolecp.md), a seconda dei casi. L'impostazione delle tabelle codici in anticipo è necessaria solo se il computer non ha scelto "Use Unicode UTF-8 for worldwide language support" (Usa Unicode UTF-8 per il supporto linguistico internazionale) nelle impostazioni per le applicazioni non Unicode nella sezione Area geografica del pannello di controllo.

>[!NOTE]
> Al momento, UTF-8 è supportato completamente nel flusso di output standard con i metodi [**WriteConsole**](writeconsole.md) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747). Il supporto per il flusso di input varia a seconda della modalità di input e continuerà a migliorare nel tempo. In particolare, le modalità **["cooked"](high-level-console-modes.md)** predefinite nell'input non supportano ancora completamente UTF-8. Lo stato corrente di questa attività è disponibile in [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) su GitHub. La soluzione alternativa consiste nell'usare il formato UTF-16 traducibile algoritmicamente per leggere l'input tramite [**ReadConsoleW**](readconsole.md) o [**ReadConsoleInputW**](readconsoleinput.md) fino a quando non vengono risolti i problemi in attesa.

## <a name="recommendations"></a>Consigli

Per le attività di sviluppo nuove e in corso in Windows, **si consiglia l'uso delle sequenze di terminale virtuale** come modalità di interazione con il terminale. In questo modo, le applicazioni client da riga di comando di Windows convergeranno con lo stile di programmazione dell'applicazione in tutte le altre piattaforme.

### <a name="exceptions-for-using-windows-console-apis"></a>Eccezioni per l'uso delle API della console di Windows

Per stabilire l'ambiente iniziale, **è ancora necessario un subset limitato di API della console di Windows**. La piattaforma Windows è ancora diversa dalle altre in termini di elaborazione, segnalazione, dispositivo e gestione della codifica:

- Gli handle standard per un processo verranno comunque controllati con **[GetStdHandle](getstdhandle.md)** e **[SetStdHandle](setstdhandle.md)** .

- La configurazione delle modalità della console su un handle per acconsentire esplicitamente al supporto della sequenza di terminale virtuale verrà gestita con **[GetConsoleMode](getconsolemode.md)** e **[SetConsoleMode](setconsolemode.md)** .

- La dichiarazione di supporto della tabella codici o della codifica UTF-8 viene eseguita con i metodi [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**SetConsoleCP**](setconsolecp.md).

- Può essere necessario un certo livello di gestione complessiva dei processi con [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) e [**FreeConsole**](freeconsole.md) per partecipare o uscire da una sessione del dispositivo console.

- I segnali e la gestione dei segnali continueranno a essere eseguiti con [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md) e [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La comunicazione con gli handle del dispositivo console può essere eseguita con [**WriteConsole**](writeconsole.md) e [**ReadConsole**](readconsole.md). Queste funzioni possono essere usate anche tramite i runtime del linguaggio di programmazione nei formati: - Runtime C (CRT): [I/O di flusso](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) come **printf**, **scanf**, **putc**, **getc** o [altri livelli di funzioni di I/O](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        - Libreria standard C++ (STL): [I/O di flusso](https://docs.microsoft.com/cpp/standard-library/iostream) come **cout** e **cin**.
        - Runtime .NET: [System.Console](https://docs.microsoft.com/dotnet/api/system.console) come **Console.WriteLine**.

- Le applicazioni che devono essere a conoscenza delle modifiche alle dimensioni della finestra dovranno comunque usare [**ReadConsoleInput**](readconsoleinput.md) per riceverle interfogliate con gli eventi principali, in quanto la sola funzione **ReadConsole** le eliminerà.

- La ricerca delle dimensioni della finestra deve comunque essere eseguita con [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione. Le dimensioni della finestra e del buffer corrisponderanno in una sessione di [pseudoconsole](pseudoconsoles.md).

## <a name="future-planning-and-pseudoconsole"></a>Pianificazione futura e pseudoconsole

Non è prevista la rimozione delle API della console di Windows dalla piattaforma.

Al contrario, l'host della console di Windows ha fornito la tecnologia **[pseudoconsole](pseudoconsoles.md)** per tradurre le chiamate di applicazioni da riga di comando di Windows esistenti in sequenze di terminale virtuale e inviarle a un altro ambiente host in modalità remota o tra piattaforme.

Questa procedura non è ottimale. Richiede che la finestra host della console mantenga un ambiente simulato degli elementi che Windows avrebbe mostrato all'utente. Proietta quindi una replica di questo ambiente simulato all'host della **pseudoconsole**. Tutte le chiamate all'API della console di Windows vengono gestite nell'ambiente simulato per soddisfare le esigenze dell'applicazione client da riga di comando legacy. Solo gli effetti vengono propagati nell'host finale.

Se un'applicazione da riga di comando desidera la compatibilità completa tra le piattaforme e il supporto completo di tutte le nuove funzionalità e degli scenari sia in Windows che altrove è quindi consigliabile passare alle sequenze di terminale virtuale e modificare l'architettura delle applicazioni da riga di comando per allinearle a tutte le piattaforme.

Altre informazioni su questa transizione di Windows per le applicazioni da riga di comando sono disponibili nella [roadmap dell'ecosistema](ecosystem-roadmap.md).
