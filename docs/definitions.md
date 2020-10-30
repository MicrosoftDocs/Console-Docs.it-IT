---
title: Windows Console e definizioni terminali
description: Fornisce le definizioni di parole e frasi utilizzate comunemente in questo spazio e set di documenti correlati alla console e al sistema Terminal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Console, terminale, terminale virtuale, host console, riga di comando, sottosistema, definizioni
ms.prod: console
ms.openlocfilehash: 763421a25d5ecaa2291b68b0370644af152622a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039621"
---
# <a name="definitions"></a>Definizioni

In questo documento vengono fornite le definizioni di parole e frasi specifiche in questo spazio e vengono utilizzate come riferimento in questo set di documenti.

## <a name="command-line-applications"></a>Applicazioni della riga di comando

Le applicazioni della riga di comando, o talvolta denominate "applicazioni console" e/o denominate "client" del sottosistema della console, sono programmi che operano principalmente su un flusso di informazioni su testo o caratteri. In genere non contengono elementi dell'interfaccia utente e delegano i ruoli di output/visualizzazione e di input/interazione a un'applicazione host. Le applicazioni della riga di comando ricevono un flusso di testo sul rispettivo handle di input standard `STDIN` che rappresenta l'input da tastiera di un utente, elabora tali informazioni, quindi risponde con un flusso di testo nell'output standard `STDOUT` per la visualizzazione al monitoraggio dell'utente. Naturalmente, ciò si è evoluto nel tempo per altri dispositivi di input e scenari remoti, ma la stessa filosofia di base rimane la stessa: i client della riga di comando operano sul testo e un altro utente gestisce la visualizzazione/input.

## <a name="standard-handles"></a>Handle standard

Gli handle standard sono una serie, `STDIN` , `STDOUT` e `STDERR` , introdotta come parte di uno spazio di processo all'avvio. Rappresentano una posizione in cui le informazioni devono essere accettate nel modo in cui vengono riportate in uscita (incluso un posto speciale per segnalare gli errori). Per le applicazioni della riga di comando, è necessario che siano sempre presenti all'avvio dell'applicazione. Vengono ereditati automaticamente dall'elemento padre, impostati in modo esplicito dall'elemento padre o creati automaticamente dal sistema operativo, se nessuno dei due è specificato/consentito. Per le applicazioni di Windows classiche, possono essere vuote all'avvio. Tuttavia, possono essere ereditate in modo implicito o esplicito dall'elemento padre o allocato, collegato e liberato durante il runtime dall'applicazione stessa.

Gli handle standard non implicano un tipo specifico di dispositivo collegato. Nel caso di applicazioni della riga di comando, tuttavia, il dispositivo è più comunemente un dispositivo console, un file (dal reindirizzamento in una Shell) o una pipe (da una shell che connette l'output di un'utilità all'input della successiva). Può anche essere un socket o qualsiasi altro tipo di dispositivo.

## <a name="ttypty"></a>TTY/PTY

Nelle piattaforme non Windows, i dispositivi TTY e PTY rappresentano rispettivamente un vero dispositivo fisico o uno pseudo-dispositivo creato dal software che è lo stesso concetto di sessione della console di Windows: un canale in cui la comunicazione tra un'applicazione client da riga di comando e un'applicazione di interattività host server o un dispositivo di tastiera/visualizzazione fisico può scambiare informazioni basate su testo.

## <a name="clients-and-servers"></a>Client e server

All'interno di questo spazio, si fa riferimento a "client" come applicazioni che eseguono le operazioni di elaborazione delle informazioni e dei comandi in esecuzione. Le applicazioni "Server" sono quelle responsabili dell'interfaccia utente e i ruoli di lavoro per tradurre l'input e l'output in moduli standard per conto dei client.

## <a name="console-subsystem"></a>Sottosistema console

Si tratta di un termine catch-all che rappresenta tutti i moduli che interessano le operazioni della console e della riga di comando. Si riferisce in particolare a un flag che fa parte dell'intestazione eseguibile portabile che specifica se l'applicazione iniziale è una riga di comando o un'applicazione console (e deve avere handle standard per avviare) o un'applicazione Windows (e non le necessita).

L'host console, le applicazioni client dalla riga di comando, il driver della console, la superficie dell'API console, l'infrastruttura pseudoconsole, i terminali, le finestre delle proprietà di configurazione, i meccanismi e gli stub all'interno del caricatore del processo e tutte le utilità correlate ai lavori di queste forme di applicazioni sono considerati appartenenti a questo gruppo.

## <a name="console-host"></a>Host console

L'host della console di Windows o `conhost.exe` è sia l'applicazione server per tutte le API della console di Windows che l'interfaccia utente di Windows classica per l'utilizzo di applicazioni della riga di comando. Il contenuto completo di questo file binario, sia il server API che l'interfaccia utente, appartiene storicamente a Windows `csrss.exe` , un processo di sistema critico ed è stato divergente per motivi di sicurezza e isolamento. In futuro `conhost.exe` continuerà a essere responsabile della manutenzione e della traduzione delle chiamate API, ma i componenti dell'interfaccia utente devono essere delegati tramite un pseudoconsole a un terminale.

## <a name="pseudoconsole"></a>Pseudoconsole

Si tratta della simulazione di Windows di un pseudoterminal o di "PTY" da altre piattaforme. Tenta di trovare una corrispondenza con la filosofia di interfaccia generale di PTY, offrendo un canale bidirezionale semplice di comunicazione basata su testo, ma lo integra in Windows con un livello di compatibilità elevato per tradurre la vasta gamma di applicazioni Windows scritte prima di questo cambiamento di filosofia di progettazione dalla superficie dell'API console classica al modulo di comunicazione del canale di testo semplice. I terminali possono usare il pseudoconsole per assumere la proprietà degli elementi dell'interfaccia utente all'interno dell'host della console, `conhost.exe` lasciandolo incaricato delle attività di manutenzione, traduzione e compatibilità dell'API.

## <a name="terminal"></a>Terminale

Un terminale è l'interfaccia utente e il modulo di interazione per un'applicazione della riga di comando. Attualmente si tratta di una rappresentazione software di un dispositivo fisico con un monitor di visualizzazione, una tastiera e un canale di comunicazione seriale bidirezionale. È responsabile della raccolta di input da parte dell'utente in un'ampia gamma di moduli, della sua conversione e della relativa codifica e di eventuali informazioni speciali sui comandi in un unico flusso di testo e della relativa trasmissione al FTP per la trasmissione al `STDIN` canale dell'applicazione client dalla riga di comando. È inoltre responsabile della ricezione di informazioni, tramite il PTY, provenienti dal canale di un'applicazione client `STDOUT` , la decodifica di eventuali informazioni speciali nel payload, il layout di tutto il testo e altri comandi e la presentazione grafica dell'utente finale.
