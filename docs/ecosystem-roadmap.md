---
title: Roadmap per l'ecosistema di console e Terminale Windows
description: Fornisce una panoramica di alto livello sulle interazioni e i piani per l'host della console di Windows, le API della console, il sottosistema della console e il prodotto Terminale.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, terminale, terminale virtuale, host della console, riga di comando, sottosistema, roadmap, ecosistema
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 3db266b761d4a8ee1fd8ec24d640bb277ab76edb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357901"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Roadmap per l'ecosistema di console e Terminale Windows

Questo documento è una roadmap di alto livello dei prodotti console di Windows e Terminale Windows. Illustra gli aspetti seguenti:


- La modalità in cui la console di Windows e Terminale Windows rientrano nell'ecosistema di applicazioni da riga di comando in Windows e altri sistemi operativi.

- Una cronologia e una roadmap futura relativa ai prodotti, alle funzionalità e alle strategie che fanno parte della creazione della piattaforma e relativa anche alla creazione della piattaforma stessa.

Il punto centrale della fase operativa attuale della console e del terminale in Microsoft è quello di fornire un'esperienza terminale di primo livello direttamente agli sviluppatori della piattaforma Windows e di [eliminare gradualmente](classic-vs-vt.md) le API della console di Windows classica, sostituendole con le [sequenze di terminale virtuale](console-virtual-terminal-sequences.md) usando la tecnologia [pseudoconsole](pseudoconsoles.md). **[Terminale Windows](/terminal/get-started)** incarna questa transizione in un'esperienza di primo livello, invitando la community degli sviluppatori a una [collaborazione open source](https://github.com/microsoft/terminal), supportando una gamma completa di combinazioni e abbinamenti di applicazioni client da riga di comando e di hosting del terminale e unificando l'ecosistema Windows con tutte le altre piattaforme.

## <a name="definitions"></a>Definizioni

Prima di procedere, è consigliabile acquisire familiarità con le [definizioni](definitions.md) della terminologia comune usata in questo articolo. La terminologia comune include: [applicazioni da riga di comando (o console)](definitions.md#command-line-applications) [handle standard (`STDIN`, `STDOUT` `STDERR`)](definitions.md#standard-handles), [dispositivi TTY e PTY](definitions.md#ttypty), [client e server](definitions.md#clients-and-servers), [sottosistema della console](definitions.md#console-subsystem), [host della console](definitions.md#console-host), [pseudoconsole](definitions.md#pseudoconsole) e [terminale](definitions.md#terminal).

## <a name="architecture"></a>Architecture

L'architettura generale del sistema è costituita da quattro parti: client, dispositivo, server e terminale.

![Grafico del flusso di comunicazione da riga di comando, da origine a destinazione, che procede da client a dispositivo a server a terminale](images/command-line-communication.png)

### <a name="client"></a>Client

Il client è un'applicazione da riga di comando che usa un'interfaccia basata su testo per consentire all'utente di immettere comandi (diversamente da un'interfaccia utente basata su mouse), restituendo una rappresentazione testuale del risultato. In Windows, l'API della console fornisce un livello di comunicazione tra il client e il dispositivo. Può anche trattarsi di un handle della console standard con le API dei controlli dei dispositivi.

### <a name="device"></a>Dispositivo

Il dispositivo è un livello di comunicazione intermedia per la gestione dei messaggi tra due processi: il client e il server. In Windows, si tratta del driver della console. Su altre piattaforme, è il dispositivo TTY o PTY. Altri dispositivi come file, pipe e socket possono essere usati con questa funzione di canale di comunicazione se l'intera transazione è in testo normale o contiene [sequenze di terminale virtuale](console-virtual-terminal-sequences.md), ma non con le [API della console di Windows](console-functions.md).

### <a name="server"></a>Server

Il server interpreta le chiamate API o i messaggi richiesti dal client. In Windows con la modalità operativa classica, il server crea anche un'interfaccia utente per presentare l'output sullo schermo. Il server raccoglie inoltre l'input per inviare i messaggi di risposta al client, tramite il driver, come un terminale in bundle nello stesso modulo. Usando la modalità [pseudoconsole](pseudoconsoles.md), agisce invece solo come un traduttore che presenta queste informazioni in [sequenze di terminale virtuale](console-virtual-terminal-sequences.md) a un terminale collegato.

### <a name="terminal"></a>Terminale

Il terminale è il livello finale, che fornisce all'utente servizi di visualizzazione e interattività grafici. Si occupa di acquisire l'input e di codificarlo come [sequenze di terminale virtuale](console-virtual-terminal-sequences.md), che possono raggiungere la funzione `STDIN` del client. Inoltre, riceve e decodifica le *sequenze di terminale virtuale* ricevute dalla funzione `STDOUT` del client per la presentazione sullo schermo.

#### <a name="further-connections"></a>Ulteriori connessioni

Come supplemento, è possibile eseguire ulteriori connessioni concatenando le applicazioni che svolgono più ruoli in uno degli endpoint. Una sessione SSH, ad esempio, è costituita da due ruoli: è un **terminale** per l'applicazione da riga di comando in esecuzione in un dispositivo, ma trasmette tutte le informazioni ricevute a un ruolo **client** in un altro dispositivo. Questo concatenamento può verificarsi a tempo indefinito tra i dispositivi e i contesti che offrono una grande flessibilità dello scenario.

Sulle piattaforme non Windows, i ruoli **server** e **terminale** costituiscono una singola unità perché non è necessario un livello di compatibilità della traduzione tra un set di API e le [sequenze di terminale virtuale](console-virtual-terminal-sequences.md).

## <a name="microsoft-products"></a>Prodotti Microsoft

Tutti i prodotti da riga di comando di Microsoft Windows sono ora disponibili in GitHub in un repository open source, [microsoft/terminal](https://github.com/microsoft/terminal).

### <a name="windows-console-host"></a>Host della console di Windows

Si tratta dell'interfaccia utente tradizionale di Windows per le applicazioni da riga di comando. Gestisce la manutenzione delle API della console chiamata da qualsiasi applicazione da riga di comando collegata. La console di Windows gestisce anche la rappresentazione dell'interfaccia utente grafica per conto di tutte le applicazioni. Si trova nella directory di sistema come `conhost.exe`o `openconsole.exe` nel modulo open source. È integrata nel sistema operativo Windows. È disponibile anche in altri prodotti Microsoft creati dal repository open source per un'implementazione più aggiornata dell'infrastruttura [pseudoconsole](pseudoconsoles.md). In base alle definizioni precedenti, la console agisce in genere in un ruolo combinato tra server e terminale o in un ruolo solo server tramite l'infrastruttura _pseudoconsole_ preferita.

### <a name="windows-terminal"></a>Terminale Windows

Si tratta della nuova interfaccia utente di Windows per le applicazioni da riga di comando. Terminale Windows funge da esempio di primo livello per l'uso dell'infrastruttura [pseudoconsole](pseudoconsoles.md) per separare le problematiche tra la manutenzione dell'API e l'interfaccia dell'applicazione basata su testo, così come tutte le piattaforme non Windows.


Terminale Windows è la principale interfaccia utente in modalità testo di Windows. Rappresenta le potenzialità dell'ecosistema e guida lo sviluppo di Windows verso l'unificazione con altre piattaforme. Terminale Windows funge anche da esempio per la creazione di un'applicazione moderna solida e complessa che abbraccia la cronologia e la gamma di framework e API Windows. In base alle definizioni precedenti, il prodotto agisce come ruolo terminale.

## <a name="major-historical-milestones"></a>Principali tappe cronologiche

Le principali tappe cronologiche del sottosistema della console si suddividono in implementazioni precedenti al 2014 e quindi passano a una panoramica delle attività eseguite a partire dal 2014, epoca di un rinnovato interesse alla riga di comando corrispondente al lancio di Windows 10.

### <a name="initial-implementation"></a>Implementazione iniziale

**\[1989-1990]** Il sistema host della console iniziale è stato implementato come emulazione dell'ambiente DOS all'interno del sistema operativo Windows. Il codice è legato e collabora con il [prompt dei comandi](/windows-server/administration/windows-commands/cmd), `cmd.exe`, che è una rappresentazione dell'ambiente DOS. Il codice del sistema host della console condivide responsabilità e privilegi con l'interprete o la shell del prompt dei comandi. Fornisce inoltre un livello base di servizi per altre utilità da riga di comando per l'esecuzione di servizi in modo analogo alla riga di comando.

### <a name="dbcs-for-cjk"></a>Supporto DBCS per il mercato CJK

**\[1997-1999\]** In questo periodo, è stato introdotto il supporto [DBCS](/windows/win32/intl/double-byte-character-sets) (Double Byte Character Set) per i mercati CJK (cinese, giapponese e coreano). Questo lavoro ha comportato una biforcazione dei vari metodi di scrittura e lettura nella console al fine di fornire le versioni "occidentali", che gestiscono i caratteri a byte singolo, nonché una rappresentazione alternativa per le versioni "orientali", in cui sono necessari due byte per rappresentare l'ampia gamma di caratteri. Questa biforcazione riguardava anche l'espansione nella rappresentazione delle celle nell'ambiente della console, che può avere l'ampiezza di una o due celle. Una cella è stretta (più alta che larga) e due celle sono larghe, a larghezza intera o di forma quadrata, in modo da potere inserire gli ideogrammi tipici della lingua cinese, giapponese e coreana.

### <a name="securityisolation"></a>Sicurezza/Isolamento

**\[2005-2009\]** Con l'esperienza del sottosistema della console in esecuzione all'interno del processo critico del sistema, `csrss.exe`, la connessione di applicazioni client assortite, a diversi livelli di accesso, a un singolo processo estremamente critico e con privilegi è stata evidenziata come particolarmente pericolosa. In questa fase, il sottosistema della console era suddiviso in applicazioni client, driver e server. Ogni applicazione poteva essere eseguita nel proprio contesto, riducendo le responsabilità e i privilegi di ognuna. Questo isolamento ha aumentato l'affidabilità generale del sistema, poiché tutti gli errori nel sottosistema della console non influivano più sulle altre funzionalità critiche del processo.

### <a name="user-experience-improvements"></a>Miglioramento dell'esperienza utente

**\[2014-2016\]** Dopo un lungo periodo di manutenzione generale del sottosistema della console da parte di vari team all'interno dell'organizzazione, è stato messo a punto un nuovo team di sviluppatori, che potesse occuparsi dei miglioramenti della console. I miglioramenti durante questo periodo hanno riguardato: selezione di righe, ridimensionamento di finestre smussate, propagazione del testo, operazioni di copia e incolla, supporto di valori DPI elevati e attenzione alla codifica Unicode, nonché la convergenza della divisione tra gli algoritmi di manipolazione dei flussi e dell'archiviazione per i paesi "occidentali" e "orientali".

### <a name="virtual-terminal-client"></a>Client del terminale virtuale

**\[2015-2017\]** Con l'arrivo del [sottosistema Windows per Linux](/windows/wsl/), Microsoft si impegna a migliorare l'esperienza di [Docker in Windows](/dotnet/architecture/microservices/container-docker-introduction/docker-defined) e ad adottare [OpenSSH](/windows-server/administration/openssh/openssh_overview) come principale tecnologia di esecuzione remota da riga di comando, le implementazioni iniziali delle [sequenze di terminale virtuale](console-virtual-terminal-sequences.md) vengono introdotte nell'host della console. In questo modo, la console esistente può agire da terminale, collegata direttamente alle applicazioni Linux native nei rispettivi ambienti, eseguendo il rendering degli attributi grafici e di testo nella visualizzazione e restituendo l'input dell'utente nel dialetto appropriato.

### <a name="virtual-terminal-server"></a>Server del terminale virtuale

**\[2018\]** Negli ultimi vent'anni, sono state create alternative di terze parti per l'host della console integrato, in modo da offrire una maggiore produttività degli sviluppatori, incentrate principalmente in personalizzazioni avanzate e interfacce a schede. Queste applicazioni hanno ancora bisogno di eseguire e nascondere la finestra dell'host della console. Si collegano come applicazione "client" secondaria per eliminare le informazioni del buffer nei cicli di polling, allo stesso modo dell'applicazione client da riga di comando principale. Il loro obiettivo era quello di agire come terminale, come su altre piattaforme, ma all'interno del sistema Windows dove i terminali non erano sostituibili.

In questo periodo, è stata introdotta l'infrastruttura [pseudoconsole](pseudoconsoles.md). Pseudoconsole consente a qualsiasi applicazione di avviare l'host della console in modalità non interattiva e diventare l'interfaccia terminale finale per l'utente. La limitazione principale di questo lavoro è stata cercare di garantire, per un periodo indefinito, una compatibilità continua delle [API della console di Windows](console-functions.md) pubblicate e offrire, al tempo stesso, un'interfaccia di hosting del server sostitutiva corrispondente a quanto previsto in tutte le altre piattaforme: le [sequenze di terminale virtuale](console-virtual-terminal-sequences.md). Di conseguenza, questo lavoro è stato speculare alla fase client: l'infrastruttura _pseudoconsole_ proietta ciò che dovrebbe essere visualizzato sullo schermo come le _sequenze di terminale virtuale_ per un host delegato e interpreta le risposte in sequenze di input in formato Windows per l'utilizzo da parte delle applicazioni client.

## <a name="roadmap-for-the-future"></a>Roadmap per il futuro

### <a name="terminal-applications"></a>Applicazioni di Terminale

**\[Dal 2019 a oggi\]** Si tratta dell'era open source per il sottosistema della console, con particolare attenzione al nuovo Terminale Windows. Annunciato durante la conferenza Microsoft Build nel maggio 2019, Terminale Windows è interamente su GitHub nella sezione [microsoft/terminal](https://github.com/microsoft/terminal). La creazione dell'applicazione Terminale Windows basata sulla piattaforma avanzata per [pseudoconsole](pseudoconsoles.md) sarà l'obiettivo di questa era, grazie alla quale è possibile offrire un'esperienza di terminale di primo livello direttamente agli sviluppatori della piattaforma Windows.

**[Terminale Windows](/terminal/get-started)** è volto non solo a mostrare la piattaforma, inclusa la tecnologia dell'interfaccia [WinUI](/apps/winui/), il modello di creazione pacchetti [MSIX](/msix/) e l'architettura del componente [C++/WinRT](/uwp/cpp-and-winrt-apis/), ma ad agire anche come convalida della piattaforma stessa. Terminale Windows sta consentendo all'organizzazione di Windows di aprire e sviluppare la piattaforma dell'app in base alle esigenze, per continuare a migliorare la produttività degli sviluppatori. L'insieme unico delle esigenze di utenti esperti e sviluppatori di Terminale Windows guida i requisiti della moderna piattaforma Windows verso la reale richiesta del mercato.

Nell'ambito del sistema operativo Windows, ciò comporta la [disattivazione dell'interfaccia utente dell'host della console classica](./classic-vs-vt.md) dalla relativa posizione predefinita, a favore di [Terminale Windows](/terminal/get-started), [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/) e le [sequenze di terminale virtuale](console-virtual-terminal-sequences.md).

Infine, in questa era si intende offrire una possibilità di scelta completa rispetto all'esperienza predefinita, indipendentemente dal fatto che si tratti di un prodotto Terminale Windows o di eventuali terminali alternativi.

### <a name="client-support-library"></a>Libreria di supporto client

**\[Futuro\]** Con il supporto e la documentazione delle [sequenze di terminale virtuale](console-virtual-terminal-sequences.md) sul lato client, è consigliabile incoraggiare gli sviluppatori di utilità da riga di comando di Windows a usare le sequenze di terminale virtuale rispetto alle API Windows classiche, per sfruttare i vantaggi di un ecosistema unificato con tutte le piattaforme. Tuttavia, un significativo elemento mancante è rappresentato dal fatto che altre piattaforme hanno un'ampia gamma di librerie helper sul lato client per la gestione di input, come [readline](https://tiswww.case.edu/php/chet/readline/rltop.html), e la visualizzazione grafica, come [ncurses](https://invisible-island.net/ncurses/ncurses.html). Questo particolare elemento della roadmap per il futuro rappresenta l'offerta dell'ecosistema e il modo in cui è possibile accelerare l'adozione delle sequenze di terminale virtuale nelle applicazioni da riga di comando di Windows rispetto all'API della console classica.

### <a name="sequence-passthrough"></a>Passaggio alla sequenza

**\[Futuro\]** La combinazione di implementazioni di client e server del terminale virtuale consente di combinare in modo completo le applicazioni client da riga di comando e l'host del terminale. Questa combinazione può comunicare con le [API della console di Windows classica](console-functions.md) o con le [sequenze di terminale virtuale](console-virtual-terminal-sequences.md). È, tuttavia, previsto un costo in termini di overhead per la traduzione nel metodo Windows classico compatibile e quindi di nuovo nel metodo di terminale virtuale più universale.

Una volta che il mercato adotta le _sequenze di terminale virtuale_ e UTF-8 in Windows in maniera sufficiente, è possibile disabilitare facoltativamente il processo di conversione/interpretazione dell'host della console. L'host della console diventa quindi un semplice servizio di chiamata API e di inoltro dalle chiamate del dispositivo all'applicazione host tramite l'infrastruttura [pseudoconsole](pseudoconsoles.md). Questa modifica consente di migliorare le prestazioni e massimizzare il dialetto delle sequenze che possono essere pronunciate tra l'applicazione client e il terminale. Grazie a questa modifica è possibile abilitare scenari di interattività aggiuntivi e *(finalmente)* allineare il sistema Windows con tutte le altre piattaforme nell'ambito delle applicazioni da riga di comando.