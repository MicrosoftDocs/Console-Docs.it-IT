---
title: Guida di orientamento per la console Windows e l'ecosistema Terminal
description: Fornisce una visualizzazione di alto livello delle interazioni tra e piani per l'host della console di Windows, le API console, il sottosistema della console e il prodotto terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Console, terminale, terminale virtuale, host console, riga di comando, sottosistema, roadmap, ecosistema
ms.prod: console
ms.openlocfilehash: e47b72a6f66e54b5f2904770f7c1a87e08d927e2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039611"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Guida di orientamento per la console Windows e l'ecosistema Terminal

Questo documento è una roadmap di alto livello dei prodotti Windows Console e Windows Terminal. Vengono illustrate le operazioni seguenti:


- In che modo Windows Console e Windows Terminal rientrano nell'ecosistema di applicazioni da riga di comando in Windows e in altri sistemi operativi.

- Una cronologia e una roadmap futura dei prodotti, delle funzionalità e delle strategie che fanno parte della creazione della piattaforma, nonché della creazione di questa piattaforma.

Il punto centrale dell'era attuale della console o del terminale in Microsoft è quello di fornire un'esperienza terminale di prima classe direttamente agli sviluppatori della piattaforma Windows e di eseguire il [Phase out](classic-vs-vt.md) delle API della console di Windows classica, sostituendo le stesse con le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) che usano [pseudoconsole](pseudoconsoles.md). Il **[terminale di Windows](/terminal/get-started)** presenta questa transizione in un'esperienza di prima classe, invitando la [collaborazione open source](https://github.com/microsoft/terminal) dalla community degli sviluppatori, supportando una gamma completa di combinazioni e abbinamenti di applicazioni client da riga di comando e host Terminal e unificando l'ecosistema Windows con tutte le altre piattaforme.

## <a name="definitions"></a>Definizioni

Prima di procedere, è consigliabile acquisire familiarità con le [definizioni](definitions.md) della terminologia comune utilizzata in questo spazio. La terminologia comune include: [applicazioni da riga di comando (o console)](definitions.md#command-line-applications), [handle standard ( `STDIN` , `STDOUT` , `STDERR` )](definitions.md#standard-handles), [dispositivi TTY e PTY](definitions.md#ttypty), [client e server](definitions.md#clients-and-servers), [sottosistema console](definitions.md#console-subsystem), [host console](definitions.md#console-host), [pseudoconsole](definitions.md#pseudoconsole)e [terminale](definitions.md#terminal).

## <a name="architecture"></a>Architettura

L'architettura generale del sistema è costituita da quattro parti: client, dispositivo, server e terminale.

![Origine del grafico del flusso di comunicazione da riga di comando a destinazione in esecuzione da client a dispositivo a server a terminale](images/command-line-communication.png)

### <a name="client"></a>Client

Il client è un'applicazione della riga di comando che usa un'interfaccia basata su testo per consentire all'utente di immettere comandi, anziché un'interfaccia utente basata su mouse, restituendo una rappresentazione testuale del risultato. In Windows, l'API della console fornisce un livello di comunicazione tra il client e il dispositivo. Può anche trattarsi di un handle della console standard con le API di controllo dei dispositivi.

### <a name="device"></a>Dispositivo

Il dispositivo è un livello di comunicazione intermedia per la gestione dei messaggi tra due processi, il client e il server. In Windows, si tratta del driver della console. Su altre piattaforme, è il dispositivo TTY o PTY. Altri dispositivi come file, pipe e socket possono essere usati come questo canale di comunicazione se l'intera transazione è in testo normale o contiene [sequenze di terminali virtuali](console-virtual-terminal-sequences.md), ma non con le [API della console di Windows](console-functions.md).

### <a name="server"></a>Server

Il server interpreta le chiamate API o i messaggi richiesti dal client. In Windows con la modalità operativa classica, il server crea anche un'interfaccia utente per presentare l'output sullo schermo. Il server raccoglie inoltre l'input per inviare i messaggi di risposta al client, tramite il driver, come un terminale in bundle nello stesso modulo. Utilizzando la modalità [pseudoconsole](pseudoconsoles.md) , è invece solo un traduttore a presentare queste informazioni in [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) a un terminale collegato.

### <a name="terminal"></a>Terminale

Il terminale è il livello finale che fornisce all'utente servizi di visualizzazione e interattività grafici. È responsabile dell'acquisizione e della codifica dell'input come [sequenze di terminali virtuali](console-virtual-terminal-sequences.md), che raggiungono la fine del client `STDIN` . Riceverà e decodifica anche le sequenze di *terminali virtuali* ricevute dal client `STDOUT` per la presentazione sullo schermo.

#### <a name="further-connections"></a>Ulteriori connessioni

Come supplemento, è possibile eseguire ulteriori connessioni concatenando le applicazioni che svolgono più ruoli in uno degli endpoint. Ad esempio, una sessione SSH ha due ruoli: è un **terminale** per l'applicazione della riga di comando in esecuzione su un dispositivo, ma invia tutte le informazioni ricevute a un ruolo **client** in un altro dispositivo. Questo concatenamento può verificarsi a tempo indefinito tra i dispositivi e i contesti che offrono una grande flessibilità dello scenario.

Sulle piattaforme non Windows, i ruoli **Server** e **Terminal** sono una singola unità perché non è necessario un livello di compatibilità della traduzione tra un set di API e le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Prodotti Microsoft

Tutti i prodotti da riga di comando di Microsoft Windows sono ora disponibili in GitHub in un repository open source, [Microsoft/Terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Host console Windows

Si tratta dell'interfaccia utente tradizionale di Windows per le applicazioni da riga di comando. Gestisce tutti i servizi API della console chiamati da qualsiasi applicazione della riga di comando collegata. La console di Windows gestisce inoltre la rappresentazione dell'interfaccia utente grafica (GUI) per conto di tutte le applicazioni. Si trova nella directory di sistema come `conhost.exe` o `openconsole.exe` nel modulo Open Source. Viene fornita con il sistema operativo Windows. È disponibile anche in altri prodotti Microsoft creati dal repository open source per un'implementazione più aggiornata dell'infrastruttura [pseudoconsole](pseudoconsoles.md) . Secondo le definizioni riportate sopra, viene eseguito in un ruolo di server e Terminal combinato tradizionalmente o in un ruolo solo server tramite l'infrastruttura _pseudoconsole_ preferita.

### <a name="windows-terminal"></a>Terminale Windows

Questa è la nuova interfaccia Windows per le applicazioni da riga di comando. Il terminale di Windows funge da esempio per la prima parte dell'uso di [pseudoconsole](pseudoconsoles.md) per separare i problemi tra la manutenzione delle API e l'interfaccia dell'applicazione basata su testo, così come tutte le piattaforme non Windows.


Il terminale di Windows è l'interfaccia utente in modalità testo principale per Windows. Illustra le funzionalità dell'ecosistema e guida lo sviluppo di Windows verso l'unificazione con altre piattaforme. Il terminale di Windows è anche un esempio di come creare un'applicazione moderna solida e complessa che copre la cronologia e la gamma di Framework e API Windows. In base alle definizioni precedenti, il prodotto opera in un ruolo di terminale.

## <a name="major-historical-milestones"></a>Attività cardine storiche principali

Le attività cardine storiche principali per il sottosistema della console sono suddivise nell'implementazione precedente alla 2014 e quindi si spostano in una panoramica delle operazioni eseguite a partire da 2014, quando il rinnovato stato attivo sulla riga di comando è stato creato nell'era di Windows 10.

### <a name="initial-implementation"></a>Implementazione iniziale

**\[ 1989-1990]** il sistema host della console iniziale è stato implementato come emulazione dell'ambiente DOS all'interno del sistema operativo Windows. Il codice è correlato e collaborato con il [prompt dei comandi](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd), `cmd.exe` , che è una rappresentazione dell'ambiente DOS. Il codice di sistema host della console condivide responsabilità e privilegi con l'interprete o la shell del prompt dei comandi. Fornisce inoltre un livello base di servizi per altre utilità della riga di comando per l'esecuzione di servizi in un modo simile a CMD.

### <a name="dbcs-for-cjk"></a>DBCS per CJK

**\[ 1997-1999 \]** in questo momento, è stato introdotto il supporto [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) ("set di caratteri a doppio byte") per supportare i mercati CJK (cinese, giapponese e coreano). Questo sforzo comporta una biforcazione di molti dei metodi di scrittura e lettura nella console di per fornire entrambe le versioni "occidentali" per gestire i caratteri a byte singolo, nonché una rappresentazione alternativa per le versioni "Eastern", in cui sono necessari due byte per rappresentare la matrice di caratteri ampia. Questa biforcazione includeva la rappresentazione di espansione di una cella nell'ambiente console in modo da avere una o due celle di larghezza, dove 1 cella è ristretta (maggiore di quella di larghezza) e 2 celle sono larghe, a larghezza intera o in altro modo in cui è possibile inserire ideogrammi tipici in cinese, giapponese e coreano.

### <a name="securityisolation"></a>Sicurezza/isolamento

**\[ 2005-2009 \]** con l'esperienza del sottosistema della console in esecuzione all'interno del processo critico di sistema, `csrss.exe` , la connessione di applicazioni client assorte, a livelli di accesso variabili, a un singolo processo estremamente critico e con privilegi è stato notato come particolarmente pericoloso. In questa era, il sottosistema della console era suddiviso in applicazioni client, driver e server. Ogni applicazione può essere eseguita nel proprio contesto, riducendo le responsabilità e i privilegi in ognuno di essi. Questo isolamento aumenta l'affidabilità generale del sistema, poiché tutti gli errori nel sottosistema della console non influiscono più sulle altre funzionalità di processo critiche.

### <a name="user-experience-improvements"></a>Miglioramenti dell'esperienza utente

**\[ 2014-2016 \]** dopo un lungo periodo di manutenzione generale del sottosistema della console da parte di Team assortiti nell'intera organizzazione, un nuovo team incentrato sugli sviluppatori è stato creato in modo da gestire i miglioramenti della console. Miglioramenti durante questo periodo di tempo inclusi: selezione di righe, ridimensionamento di finestre smussate, testo di propagazione, copia e incolla, supporto di valori DPI alti e attenzione su Unicode, inclusa la convergenza della divisione tra gli algoritmi di manipolazione di flussi "occidentali" e "Eastern".

### <a name="virtual-terminal-client"></a>Client terminal virtuale

**\[ 2015-2017 \]** con l'arrivo del [sottosistema Windows per Linux](https://docs.microsoft.com/windows/wsl/), Microsoft si impegna a migliorare l'esperienza di [Docker in Windows](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined)e l'adozione di [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) come tecnologia di esecuzione remota della riga di comando principale, le implementazioni iniziali delle [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) sono state introdotte nell'host della console. In questo modo la console esistente fungerebbe da terminale, collegata direttamente alle applicazioni Linux native nei rispettivi ambienti, eseguendo il rendering degli attributi grafici e di testo nella visualizzazione e restituendo l'input dell'utente nel dialetto appropriato.

### <a name="virtual-terminal-server"></a>Server terminal virtuale

**\[ 2018 \]** negli ultimi vent'anni, sono state create alternative di terze parti per l'host della console della posta in arrivo per offrire una maggiore produttività per gli sviluppatori, centrata in modo significativo nelle personalizzazioni avanzate e nelle interfacce a schede. Queste applicazioni hanno ancora bisogno di eseguire e nascondere la finestra host della console. Si collegano come un'applicazione client secondaria per eliminare le informazioni del buffer nei cicli di polling come l'applicazione client della riga di comando principale gestita. Il loro obiettivo era costituito da un terminale, ad esempio su altre piattaforme, ma nel mondo Windows in cui i terminali non erano sostituibili.

In questo periodo di tempo, è stata introdotta l'infrastruttura [pseudoconsole](pseudoconsoles.md) . Pseudoconsole consente a qualsiasi applicazione di avviare l'host della console in modalità non interattiva e diventare l'interfaccia terminale finale per l'utente. La limitazione principale di questo sforzo è stata la promessa di compatibilità continua di Windows per la manutenzione di tutte le [API della console di Windows](console-functions.md) pubblicate per il futuro indefinito, offrendo al tempo stesso un'interfaccia di hosting server sostitutiva che corrisponda a quanto previsto in tutte le altre piattaforme: sequenze di [terminali virtuali](console-virtual-terminal-sequences.md). Di conseguenza, questo sforzo ha eseguito l'immagine speculare della fase client: il _pseudoconsole_ proietta gli elementi visualizzati sullo schermo come _sequenze di terminali virtuali_ per un host delegato e interpreta le risposte nelle sequenze di input in formato Windows per l'utilizzo delle applicazioni client.

## <a name="roadmap-for-the-future"></a>Guida di orientamento per il futuro

### <a name="terminal-applications"></a>Applicazioni Terminal

**\[ 2019: ora \]** si tratta dell'era open source per il sottosistema della console, con particolare attenzione al nuovo terminale di Windows. Annunciato durante la conferenza di Microsoft Build nel maggio 2019, il terminale di Windows è interamente su GitHub in [Microsoft/Terminal](https://github.com/microsoft/terminal). La creazione di un'applicazione Windows Terminal basata sulla piattaforma avanzata per [pseudoconsole](pseudoconsoles.md) sarà il fulcro di questa era, offrendo un'esperienza Terminal di prima classe direttamente agli sviluppatori della piattaforma Windows.

Il **[terminale di Windows](/terminal/get-started)** prevede non solo la presentazione della piattaforma, tra cui la tecnologia dell'interfaccia [WinUI](/apps/winui/) , il modello di packaging [MSIX](/msix/) e l'architettura del componente [/WinRT C++](/uwp/cpp-and-winrt-apis/) , ma anche come convalida della piattaforma stessa. Windows Terminal consente all'organizzazione di Windows di aprire e sviluppare la piattaforma dell'app in base alle esigenze per continuare a migliorare la produttività degli sviluppatori. Il set di terminali Windows Unique per gli utenti e i requisiti per gli sviluppatori Guida i requisiti della piattaforma Windows moderna per i mercati effettivamente necessari da Windows.

All'interno del sistema operativo Windows, questo include la disattivazione dell' [interfaccia utente dell'host della console classica](./classic-vs-vt.md) dalla posizione predefinita, a favore delle sequenze di terminali [virtuali](console-virtual-terminal-sequences.md), [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)e terminali di [Windows](/terminal/get-started).

Infine, questa era la tendenza a offrire la scelta completa rispetto all'esperienza predefinita, a prescindere che si tratti di un prodotto terminale Windows o di eventuali terminali alternativi.

### <a name="client-support-library"></a>Libreria di supporto client

In **\[ futuro \]** con il supporto e la documentazione delle [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) sul lato client, invitiamo gli sviluppatori di utilità della riga di comando di Windows a usare prima le sequenze di terminali virtuali sulle API Windows classiche per sfruttare i vantaggi di un ecosistema unificato con tutte le piattaforme. Tuttavia, un elemento mancante significativo è che altre piattaforme hanno un'ampia gamma di librerie Helper sul lato client per la gestione di input come [ReadLine](https://tiswww.case.edu/php/chet/readline/rltop.html) e la visualizzazione grafica, ad esempio [ncurses](https://invisible-island.net/ncurses/ncurses.html). Questo particolare elemento della mappa stradale rappresenta l'esplorazione dei vantaggi offerti dall'ecosistema e il modo in cui è possibile accelerare l'adozione di sequenze di terminali virtuali nelle applicazioni della riga di comando di Windows tramite l'API console classica.

### <a name="sequence-passthrough"></a>Pass-through sequenza

In **\[ futuro \]** la combinazione di implementazioni di client e server di terminali virtuali consente di combinare e combinare in modo completo le applicazioni per la riga di comando e l'hosting di terminal client. Questa combinazione può comunicare con le API della [console di Windows](console-functions.md) classica o con le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md), ma comporta un costo in termini di overhead per tradurlo nel metodo Windows compatibile con la versione classica e quindi di nuovo nel metodo terminale virtuale più universale.

Una volta che il mercato ha sufficientemente adottato le _sequenze di terminali virtuali_ e UTF-8 in Windows, è possibile disabilitare facoltativamente il processo di conversione/interpretazione dell'host della console. L'host della console diventerebbe quindi un semplice servizio di chiamata API e inoltro dalle chiamate del dispositivo all'applicazione host tramite il [pseudoconsole](pseudoconsoles.md). Questa modifica consente di migliorare le prestazioni e massimizzare il dialetto delle sequenze che possono essere pronunciate tra l'applicazione client e il terminale. Grazie a questa modifica, è possibile abilitare scenari di interattività aggiuntivi e, *infine,* portare il mondo di Windows in linea con la famiglia di tutte le altre piattaforme nello spazio dell'applicazione della riga di comando.
