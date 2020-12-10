---
title: Modalità console legacy - Windows Desktop
description: La modalità console legacy è uno strumento di compatibilità che facilita l'esecuzione di applicazioni da riga di comando che potrebbero non funzionare con l'host della console di Windows 10
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console, compatibilità
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037709"
---
# <a name="legacy-console-mode"></a>Modalità console legacy

La modalità console legacy è uno strumento di compatibilità progettato per aiutare gli utenti degli strumenti da riga di comando meno recenti in Windows 10. Per qualsiasi strumento da riga di comando che non viene visualizzato o non funziona correttamente nell'esperienza predefinita della console di Windows 10, questa modalità offre una soluzione grossolana per riportare il sistema a una versione precedente dell'esperienza di hosting della console.

## <a name="using-legacy-console-mode"></a>Uso della modalità console legacy

Per usare la modalità console legacy, aprire prima di tutto la finestra di hosting della console. Questa operazione viene in genere eseguita avviando uno degli interpreti dei comandi [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) o [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Fare clic con il pulsante destro del mouse sulla barra del titolo dell'applicazione e scegliere l'opzione di menu `Properties`. Scegliere la prima scheda, `Options`. Quindi selezionare la casella `Use legacy console` nella parte inferiore della pagina. Premere il pulsante `OK` per applicare l'impostazione.

Per ripristinare l'impostazione precedente, è possibile tornare allo stesso menu della finestra delle proprietà, deselezionare la casella e scegliere `OK`.

> [!NOTE]
>Questa impostazione viene applicata a livello globale a tutte le sessioni avviate dopo la modifica della preferenza. Le sessioni già aperte non verranno modificate.

## <a name="differences-between-modes"></a>Differenze tra le modalità

Il team dell'host della console si adopera per ridurre al minimo le differenze tra la modalità legacy e quella corrente della console per assicurare che la versione più recente possa essere utilizzata dal maggior numero possibile di clienti. Se si verifica un problema che richiede l'uso della console legacy e che non è documentato in questo articolo, contattare il team sul repository GitHub [microsoft/terminal](https://github.com/microsoft/terminal/) oppure tramite [Hub di Feedback](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) per ricevere assistenza.

### <a name="16-bit-applications-on-32-bit-windows"></a>Applicazioni a 16 bit in Windows a 32 bit

Per il funzionamento di alcune applicazioni a 16 bit in Windows a 32 è previsto l'uso di una tecnologia di macchina virtuale denominata [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). Spesso queste applicazioni usano una modalità di buffering dello schermo grafico in combinazione con l'ambiente di hosting della console per funzionare. Solo l'esperienza della console legacy supporta queste modalità di buffering grafico e il supporto dell'API della console aggiuntivo necessario per queste applicazioni. Il sistema selezionerà automaticamente l'ambiente console legacy all'avvio di una di queste applicazioni.

### <a name="ime-embedding"></a>Incorporamento IME

L'host della console legacy incorpora la parte relativa ai suggerimenti dell'IME all'interno della finestra di hosting riservando una riga nella parte inferiore della schermata per i suggerimenti. L'ambiente host della console corrente delega invece questa attività al sottosistema IME per visualizzare una finestra sovrapposta sopra l'host della console con i suggerimenti. In un ambiente in cui le finestre sovrapposte non sono possibili, ad esempio con determinati strumenti di comunicazione remota, potrebbe essere necessario usare l'host della console legacy.

### <a name="api-differences"></a>Differenze relative alle API

La principale differenza nota tra la versione legacy e quella corrente è l'implementazione di UTF-8. L'host legacy ha un supporto estremamente rudimentale e spesso non corretto di UTF-8 con la [tabella codici 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). L'host della console corrente include miglioramenti incrementali a ogni versione di Windows 10 per migliorare questo supporto. Le applicazioni che tentano di affidarsi alla stima delle interpretazioni "non corrette note" di UTF-8 dalla console legacy si troveranno a ricevere risposte diverse man mano che viene migliorato il supporto.

Altre differenze riscontrate in relazione alle API possono essere segnalate al [repository GitHub microsoft/terminal](https://github.com/microsoft/terminal/) oppure tramite [Hub di Feedback](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) perché vengano valutate e possibilmente corrette.
