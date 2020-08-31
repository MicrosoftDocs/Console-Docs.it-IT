---
title: Modalità console legacy-desktop di Windows
description: La modalità console legacy è uno strumento di compatibilità che facilita l'esecuzione di applicazioni della riga di comando che potrebbero non funzionare con l'host della console di Windows 10
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, compatibilità
ms.openlocfilehash: a69e192426cc178ae98565db07c49f9ff2ce4961
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060036"
---
# <a name="legacy-console-mode"></a>Modalità console legacy

La modalità console legacy è uno strumento di compatibilità progettato per aiutare gli utenti di strumenti da riga di comando obsoleti in Windows 10. Per tutti gli strumenti da riga di comando che non vengono visualizzati o non funzionano correttamente nell'esperienza predefinita della console di Windows 10, questa modalità offre una soluzione con granularità grossolana per riportare il sistema a una versione precedente dell'esperienza di hosting della console.

## <a name="using-legacy-console-mode"></a>Uso della modalità console legacy

Per usare la modalità console legacy, aprire prima di tutto la finestra di hosting della console. Questa operazione viene in genere eseguita avviando uno degli interpreti dei comandi [cmd](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) o [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Fare clic con il pulsante destro del mouse sulla barra del titolo dell'applicazione e scegliere l' `Properties` opzione di menu. Scegliere la prima scheda `Options` . Quindi selezionare la casella nella parte inferiore della pagina che descrive `Use legacy console` . Premere il `OK` pulsante per applicare.

È possibile ripristinare l'impostazione tornando allo stesso menu della finestra delle proprietà e deselezionando la casella, quindi premendo `OK` .

**Nota:** Questa impostazione viene applicata globalmente a tutte le sessioni che si avviano dopo la modifica delle preferenze. Le sessioni già aperte non verranno modificate.

## <a name="differences-between-modes"></a>Differenze tra le modalità

Il team host della console tenta di ridurre al minimo le differenze tra le modalità legacy e corrente della console di per garantire che il maggior numero possibile di clienti possa eseguire la versione più aggiornata. Se si verifica un problema che richiede l'uso della console legacy che non è documentata in questo articolo, contattare il team nel repository GitHub [Microsoft/Terminal](https://github.com/microsoft/terminal/) o tramite l' [Hub feedback](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) per assistenza.

### <a name="16-bit-applications-on-32-bit-windows"></a>applicazioni a 16 bit in Windows a 32 bit

Alcune applicazioni a 16 bit in Windows a 32 bit utilizzano una tecnologia di macchina virtuale per il funzionamento di [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). Spesso queste applicazioni usano la modalità di buffering dello schermo grafico in combinazione con l'ambiente di hosting della console di per funzionare. Solo l'esperienza console legacy supporta queste modalità di buffering grafico e il supporto dell'API console aggiuntivo necessario per potenziare le applicazioni. Il sistema seleziona automaticamente l'ambiente console legacy quando viene avviata una di queste applicazioni.

### <a name="ime-embedding"></a>Incorporamento IME

L'host della console legacy incorporate la parte relativa ai suggerimenti dell'IME all'interno della finestra di hosting riservando una riga nella parte inferiore della schermata per i suggerimenti. L'ambiente host della console corrente delega invece questa attività al sottosistema IME per visualizzare una finestra sovrapposta sopra l'host della console con suggerimenti. In un ambiente in cui le finestre sovrapposte non sono possibili, ad esempio con determinati strumenti di comunicazione remota, potrebbe essere necessario l'host della console legacy.

### <a name="api-differences"></a>Differenze tra API

La differenza nota principale tra legacy e Current è l'implementazione di UTF-8. L'host legacy ha un supporto estremamente rudimentale e spesso non corretto di UTF-8 con [tabella codici 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). L'host della console corrente contiene miglioramenti incrementali per la versione finale di Windows 10 per migliorare questo supporto. Le applicazioni che tentano di basarsi sulla stima delle interpretazioni "note non corrette" di UTF-8 dalla console legacy si troveranno a ricevere risposte diverse a seconda del miglioramento del supporto. 

Altre differenze riscontrate con le API devono essere segnalate al repository GitHub [Microsoft/Terminal](https://github.com/microsoft/terminal/) o tramite l' [Hub feedback](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) per la valutazione e la possibile correzione.