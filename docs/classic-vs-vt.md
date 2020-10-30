---
title: API console classiche rispetto alle sequenze di terminali virtuali
description: Viene descritto il contrasto tra la superficie dell'API console Win32 classica e il concetto di sequenze di terminali virtuali, talvolta note anche come sequenze di escape, per la scrittura di applicazioni della riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Console, terminale, terminale virtuale, sequenze di escape, VT, VT100, API console
ms.prod: console
ms.openlocfilehash: 0fdd39cab5b8f6ca5cc1602c8e68ec7f2a2303ad
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039594"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>API console classiche rispetto alle sequenze di terminali virtuali

Si consiglia di sostituire l' **API console di Windows** classica con le **sequenze di terminali virtuali** . In questo articolo viene illustrata la differenza tra i due e vengono illustrati i motivi della nostra raccomandazione.

## <a name="definitions"></a>Definizioni

La superficie dell' **[API console di Windows](console-functions.md)** classica è definita come la serie di interfacce funzionali del linguaggio C in `kernel32.dll` con "console" nel nome.

Le **[sequenze di terminali virtuali](console-virtual-terminal-sequences.md)** sono definite come linguaggio di comandi incorporato nei flussi di input standard e di output standard. Le sequenze di terminali virtuali usano caratteri di escape non stampabili per i comandi di segnalazione Interleaved con testo stampabile normale.

## <a name="history"></a>Cronologia

La **console di Windows** fornisce un'ampia superficie API per le applicazioni da riga di comando client per modificare sia il buffer di visualizzazione dell'output che il buffer di input dell'utente. Tuttavia, altre piattaforme non Windows non hanno mai concesso questo approccio specifico basato su API ai propri ambienti da riga di comando, scegliendo invece di usare sequenze di terminali virtuali incorporate nei flussi di output standard e standard. *(Per un periodo di tempo, Microsoft supportava questo comportamento anche nelle prime edizioni di DOS e Windows tramite un driver denominato ANSI.SYS).*

Al contrario, le **sequenze di terminali virtuali** (in diversi dialetti) guidano le operazioni dell'ambiente della riga di comando per tutte le altre piattaforme. Queste sequenze sono radicate in uno [standard ECMA](https://www.ecma-international.org/publications/standards/Ecma-048.htm) e una serie di estensioni da parte di molti fornitori che eseguono il ritracciamento dei terminali di Digital Equipment Corporation e Tektronix, fino a terminali software più moderni e comuni, come [xterm](https://invisible-island.net/xterm/). Molte estensioni sono disponibili all'interno del dominio di sequenza dei terminali virtuali e alcune sequenze sono più diffuse rispetto ad altre, ma è sicuro affermare che il mondo si è standardizzato come linguaggio di comando per le esperienze da riga di comando con un subset noto supportato da praticamente ogni terminale e applicazione client da riga di comando.

## <a name="cross-platform-support"></a>Supporto multipiattaforma

Le **sequenze di terminali virtuali** sono supportate in modalità nativa tra piattaforme, rendendo le applicazioni Terminal e le utilità della riga di comando facilmente portabili tra le versioni e le varianti dei sistemi operativi, ad eccezione di Windows.

Al contrario, le **API della console di Windows** sono supportate solo in Windows. Quando si tenta di trasferire le utilità della riga di comando da una piattaforma o un'altra, è necessario scrivere una libreria di traduzione o un adattatore completo tra Windows e Virtual Terminal, o viceversa.

### <a name="remote-access"></a>Accesso remoto

Le **sequenze di terminali virtuali** contengono un vantaggio principale per l'accesso remoto. Non richiedono alcun lavoro aggiuntivo per il trasporto o l'esecuzione di chiamate di procedure remote, oltre a quanto richiesto per configurare una connessione da riga di comando standard remota. La semplice connessione di un canale di trasporto in uscita e in uscita (o un canale bidirezionale singolo) su una pipe, un socket, un file, una porta seriale o qualsiasi altro dispositivo è sufficiente per portare completamente tutte le informazioni necessarie per un'applicazione che parla queste sequenze a un host remoto.

Al contrario, le **API della console di Windows** sono state accessibili solo sul computer locale e tutti gli sforzi per eseguirne la modalità remota richiederebbero la creazione di un intero livello di interfaccia di chiamata e trasporto remoto oltre a un semplice canale.

### <a name="separation-of-concerns"></a>Separazione delle problematiche

Alcune **API della console di Windows** forniscono accesso di basso livello ai buffer di input e di output o alle funzioni di convenienza per le righe di comando interattive. Questo potrebbe includere gli alias e la cronologia dei comandi programmati nel sottosistema della console e nell'ambiente host, anziché all'interno dell'applicazione client da riga di comando.

Al contrario, **altre piattaforme** rendono la memoria dello stato corrente dell'applicazione e la praticità di questa funzionalità è responsabilità dell'utilità da riga di comando o della shell stessa.

Il modo in cui la **console di Windows** gestisce questa responsabilità nell'host e nell'API della console rende più veloce e semplice la scrittura di un'applicazione da riga di comando con queste funzionalità, eliminando la responsabilità di ricordare lo stato del disegno o la gestione delle funzionalità di modifica. In questo modo, tuttavia, è quasi impossibile connettere le attività in modalità remota tra piattaforme, versioni o scenari, a causa delle variazioni delle implementazioni e della disponibilità. Questo metodo di gestione della responsabilità rende anche l'esperienza interattiva finale di queste applicazioni da riga di comando di Windows completamente dipendenti dall'implementazione, dalle priorità e dal ciclo di rilascio dell'host della console.

Ad esempio, le funzionalità avanzate di modifica della linea, come l'evidenziazione della sintassi e la selezione complessa, sono possibili solo quando un'applicazione della riga di comando gestisce i problemi di modifica. La console non può mai avere un contesto sufficiente per comprendere completamente questi scenari in modo ampio, come l'applicazione client.

Al contrario, altre piattaforme usano le **sequenze di terminali virtuali** per gestire queste attività e la comunicazione di terminali virtuali con librerie lato client riutilizzabili, ad esempio [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) e [ncurses](https://invisible-island.net/ncurses/ncurses.html). Il terminale finale è responsabile solo della visualizzazione delle informazioni e della ricezione dell'input tramite il canale di comunicazione bidirezionale.

### <a name="wrong-way-verbs"></a>Verbi Wrong-Way

Con la **console di Windows** , alcune azioni possono essere eseguite nella direzione opposta a quella naturale sui flussi di input e di output. Questo consente alle applicazioni della riga di comando di Windows di evitare il problema di gestire i propri buffer. Consente inoltre alle app della riga di comando di Windows di eseguire operazioni avanzate, ad esempio simulando/inserendo input per conto di un utente o leggendo parte della cronologia degli elementi scritti.

Sebbene in questo modo si forniscano ulteriore potenza alle applicazioni Windows che operano in un contesto utente specifico in un singolo computer, fornisce anche un vettore per incrociare livelli di sicurezza e privilegi o domini se usati in determinati scenari. Questi scenari includono il funzionamento tra contesti nello stesso computer o tra contesti in un altro computer o ambiente.

Altre piattaforme, che usano **sequenze di terminali virtuali** , non consentono questa attività. Lo scopo della nostra raccomandazione di eseguire la transizione dalla console classica di Windows alla sequenza di terminali virtuali consiste nel convergere con questa strategia sia per motivi di interoperabilità che di sicurezza.

### <a name="direct-window-access"></a>Accesso diretto alla finestra

La **superficie dell'API della console di Windows** fornisce l'handle di finestra esatto per la finestra di hosting. Questo consente a un'utilità della riga di comando di eseguire operazioni di finestra avanzate raggiungendo l'ampia gamma di API Win32 consentite in un handle di finestra. Queste API Win32 possono modificare lo stato della finestra, il frame, l'icona o altre proprietà della finestra.

Al contrario, su altre piattaforme con **sequenze di terminali virtuali** , è possibile eseguire una serie di comandi limitati sulla finestra. Questi comandi possono eseguire operazioni quali la modifica delle dimensioni della finestra o del titolo visualizzato, ma devono essere eseguite nella stessa banda e sotto lo stesso controllo del resto del flusso.

Man mano che Windows si è evoluto, i controlli di sicurezza e le restrizioni sugli handle di finestra sono aumentati. Inoltre, la natura e l'esistenza di un handle di finestra indirizzabile all'applicazione su qualsiasi elemento dell'interfaccia utente specifico si sono evolute, soprattutto con l'aumento del supporto di piattaforme e fattori di forma del dispositivo. In questo modo, l'accesso diretto alla finestra alle applicazioni da riga di comando diventa fragile come la piattaforma e le esperienze si evolvono.

### <a name="unicode"></a>Unicode

UTF-8 è la codifica accettata per i dati Unicode in quasi tutte le piattaforme moderne, in quanto rappresenta il giusto equilibrio tra portabilità, dimensioni di archiviazione e tempo di elaborazione. Tuttavia, Windows ha scelto in passato UTF-16 come codifica primaria per i dati Unicode. Il supporto per UTF-8 aumenta in Windows e l'utilizzo di questi formati Unicode non impedisce l'utilizzo di altre codifiche.

La piattaforma **console Windows** è supportata e continuerà a supportare tutte le codifiche e le tabelle codici esistenti. Usare la codifica UTF-16 per la massima compatibilità tra le versioni di Windows ed eseguire la conversione algoritmica con UTF-8, se necessario. È in corso un miglioramento del supporto di UTF-8 per il sistema di console.

Il supporto UTF-16 nella console di può essere utilizzato senza alcuna configurazione aggiuntiva tramite la variante _W_ di tutte le API della console ed è una scelta più probabile per le applicazioni già in formato UTF-16 attraverso la comunicazione con la `wchar_t` variante e _W_ di altri prodotti e funzioni della piattaforma Microsoft e Windows.

Il supporto UTF-8 nella console di può essere usato tramite _una_ variante delle API della console per gli handle della console dopo aver impostato la tabella codici su `65001` o `CP_UTF8` con i metodi [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**SetConsoleCP**](setconsolecp.md) , a seconda dei casi. L'impostazione delle tabelle codici in anticipo è necessaria solo se il computer non ha scelto "USA Unicode UTF-8 per il supporto del linguaggio globale" nelle impostazioni per le applicazioni non Unicode nella sezione Region del pannello di controllo.

>[!NOTE]
> Al momento, UTF-8 è supportato completamente nel flusso di output standard con i metodi [**WriteConsole**](writeconsole.md) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) . Il supporto per il flusso di input varia a seconda della modalità di input e continuerà a migliorare nel tempo. In particolare, le modalità **["cotte"](high-level-console-modes.md)** predefinite sull'input non supportano ancora completamente UTF-8. Lo stato corrente di questo lavoro si trova in [**Microsoft/Terminal # 7777**](https://github.com/microsoft/terminal/issues/7777) su GitHub. La soluzione alternativa consiste nell'usare il formato UTF-16 traducibile da algoritmicamente per leggere l'input tramite [**ReadConsoleW**](readconsole.md) o [**ReadConsoleInputW**](readconsoleinput.md) fino a quando non vengono risolti i problemi in attesa.

## <a name="recommendations"></a>Consigli

Per lo sviluppo nuovo e continuo in Windows, le **sequenze di terminali virtuali sono consigliate** come modalità di interazione con il terminale. In questo modo si convergeranno le applicazioni client da riga di comando di Windows con lo stile di programmazione dell'applicazione in tutte le altre piattaforme.

### <a name="exceptions-for-using-windows-console-apis"></a>Eccezioni per l'utilizzo delle API della console di Windows

Un **subset limitato di API console Windows è ancora necessario** per stabilire l'ambiente iniziale. La piattaforma Windows è ancora diversa da altre in fase di elaborazione, segnalazione, dispositivo e gestione della codifica:

- Gli handle standard per un processo verranno comunque controllati con **[GetStdHandle](getstdhandle.md)** e **[SetStdHandle](setstdhandle.md)** .

- La configurazione delle modalità console su un handle per acconsentire esplicitamente al supporto della sequenza di terminali virtuali verrà gestita con **[GetConsoleMode](getconsolemode.md)** e **[SetConsoleMode](setconsolemode.md)** .

- La dichiarazione di tabella codici o il supporto UTF-8 viene eseguita con i metodi [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**SetConsoleCP**](setconsolecp.md) .

- Potrebbe essere necessario un certo livello di gestione complessiva dei processi con [**AllocConsole**](allocconsole.md), [**AttachConsole**](attachconsole.md) e [**FreeConsole**](freeconsole.md) per partecipare o uscire da una sessione del dispositivo console.

- I segnali e la gestione del segnale continueranno a essere eseguiti con [**SetConsoleCtrlHandler**](setconsolectrlhandler.md), [**HandlerRoutine**](handlerroutine.md)e [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md).

- La comunicazione con gli handle del dispositivo console può essere eseguita con [**WriteConsole**](writeconsole.md) e [**ReadConsole**](readconsole.md). Questi possono essere usati anche tramite i runtime del linguaggio di programmazione in formati:-C Runtime (CRT): [i/O di flusso](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) come **printf** , **scanf** , **putc** , **GETC** o [altri livelli di funzioni di I/o](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output).
        -Libreria standard C++ (STL): [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) come **cout** e **cin** .
        -Runtime .NET: [System. console](https://docs.microsoft.com/dotnet/api/system.console) come **Console. WriteLine** .

- Le applicazioni che devono essere a conoscenza delle modifiche alle dimensioni della finestra dovranno comunque usare [**ReadConsoleInput**](readconsoleinput.md) per riceverle Interleaved con gli eventi chiave, perché solo **ReadConsole** li eliminerà.

- La ricerca delle dimensioni della finestra deve comunque essere eseguita con [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione. Le dimensioni della finestra e del buffer corrisponderanno in una sessione [pseudoconsole](pseudoconsoles.md) .

## <a name="future-planning-and-pseudoconsole"></a>Pianificazione futura e pseudoconsole

Non sono previsti piani per la rimozione delle API della console di Windows dalla piattaforma.

Al contrario, l'host della console di Windows ha fornito la tecnologia **[pseudoconsole](pseudoconsoles.md)** per tradurre le chiamate dell'applicazione da riga di comando di Windows esistenti in sequenze di terminali virtuali e per trasmetterle a un altro ambiente host in modalità remota o tra piattaforme diverse.

Questa traduzione non è perfetta. Richiede che la finestra host della console mantenga un ambiente simulato delle finestre visualizzate dall'utente. Quindi proietta una replica di questo ambiente simulato nell'host **pseudoconsole** . Tutte le chiamate all'API della console di Windows vengono gestite all'interno dell'ambiente simulato per soddisfare le esigenze dell'applicazione client della riga di comando legacy. Solo gli effetti vengono propagati nell'host finale.

Un'applicazione della riga di comando che desidera la compatibilità completa tra le piattaforme e il supporto completo di tutte le nuove funzionalità e scenari sia in Windows che altrove è quindi consigliabile passare a sequenze di terminali virtuali e modificare l'architettura delle applicazioni da riga di comando per allinearle a tutte le piattaforme.

Altre informazioni su questa transizione di Windows per le applicazioni da riga di comando sono disponibili nella Guida di [orientamento ecosistema](ecosystem-roadmap.md).
