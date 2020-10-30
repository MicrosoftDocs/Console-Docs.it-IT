---
title: Buffer di input della console
description: Ogni console dispone di un buffer di input che contiene una coda di record di eventi di input.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: 9b210e07fd2531b2f58130f4b96ad31a374923f4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039209"
---
# <a name="console-input-buffer"></a>Buffer di input della console

Ogni console dispone di un buffer di input che contiene una coda di record di eventi di input. Quando la finestra di una console dispone dello stato attivo della tastiera, una console formatta ogni evento di input (ad esempio, una singola sequenza di tasti, un movimento del mouse o un clic del pulsante del mouse) come record di input che inserisce nel buffer di input della console.

Le applicazioni possono accedere indirettamente al buffer di input di una console usando le [funzioni di i/O della console di alto livello](high-level-console-input-and-output-functions.md)o direttamente usando le [funzioni di input della console di basso livello](low-level-console-input-functions.md). Le funzioni di input di alto livello filtrano ed elaborano i dati nel buffer di input, restituendo solo un flusso di caratteri di input. Le funzioni di input di basso livello consentono alle applicazioni di leggere i record di input direttamente dal buffer di input di una console o di inserire record di input nel buffer di input. Per aprire un handle per il buffer di input di una console, specificare il valore **CONIN $** in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) .

Un record di input è una struttura che contiene informazioni sul tipo di evento che si è verificato (tastiera, mouse, ridimensionamento della finestra, stato attivo o evento di menu), oltre a dettagli specifici sull'evento. Il membro **eventType** in una struttura di [**\_ record di input**](input-record-str.md) indica quale tipo di evento è contenuto nel record.

Gli eventi di menu e lo stato attivo vengono inseriti nel buffer di input di una console per l'uso interno da parte del sistema e devono essere ignorati dalle applicazioni.

## <a name="keyboard-events"></a>Eventi della tastiera

Gli eventi della tastiera vengono generati quando viene premuto o rilasciato un tasto; sono incluse le chiavi di controllo. Tuttavia, il tasto ALT ha un significato speciale per il sistema quando viene premuto e rilasciato senza essere combinato con un altro carattere e non viene passato all'applicazione. Inoltre, la combinazione di tasti CTRL + C non viene passata se l'handle di input è in modalità elaborata.

Se l'evento di input è una sequenza di tasti, il membro dell' **evento** nel [**\_ record di input**](input-record-str.md) è una struttura di [**\_ \_ record di eventi chiave**](key-event-record-str.md) che contiene le informazioni seguenti:

- Valore booleano che indica se il tasto è stato premuto o rilasciato.
- Numero di ripetizioni che può essere maggiore di uno quando si tiene premuto un tasto.
- Codice della chiave virtuale, che identifica la chiave specificata in modo indipendente dal dispositivo.
- Codice di analisi virtuale, che indica il valore dipendente dal dispositivo generato dall'hardware della tastiera.
- Il™ Unicode tradotto o il carattere ANSI.
- Variabile di flag che indica lo stato delle chiavi di controllo (ALT, CTRL, MAIUSC, BLOC NUM, BLOC SCORR e BLOC MAIUSC) e che indica se è stata premuta una chiave avanzata. Le chiavi avanzate per le tastiere IBM® 101-Key e 102-Key sono i INS, CANC, HOME, END, PGSU, PGGIÙ e i tasti di direzione nei cluster a sinistra del tastierino numerico e la divisione (/) e immettono le chiavi nel tastierino numerico.

## <a name="mouse-events"></a>Eventi del mouse

Gli eventi del mouse vengono generati ogni volta che l'utente sposta il mouse o preme o rilascia uno dei pulsanti del mouse. Gli eventi del mouse vengono inseriti nel buffer di input solo se vengono soddisfatte le condizioni seguenti:

- La modalità di input della console è impostata per **abilitare l' \_ \_ input del mouse** (modalità predefinita).
- La finestra della console dispone dello stato attivo della tastiera.
- Il puntatore del mouse si trova all'interno dei bordi della finestra della console.

Se l'evento di input è un evento del mouse, il membro dell' **evento** nel [**\_ record di input**](input-record-str.md) è una struttura di [**\_ \_ record di eventi del mouse**](mouse-event-record-str.md) che contiene le informazioni seguenti:

- Coordinate del puntatore del mouse in termini di riga della cella di caratteri e colonna nel sistema di coordinate del buffer dello schermo della console.
- Variabile di flag che indica lo stato dei pulsanti del mouse.
- Variabile di flag che indica lo stato delle chiavi di controllo (ALT, CTRL, MAIUSC, BLOC NUM, SCROLL LOCK e CAPS LOCK) e che indica se è stato premuto un tasto avanzato. Le chiavi avanzate per le tastiere IBM 101-Key e 102-Key sono i valori INS, CANC, HOME, END, PGSU, PGGIÙ e i tasti di direzione nei cluster a sinistra del tastierino numerico e la divisione (/) e immettono le chiavi nel tastierino numerico.
- Variabile di flag che indica se si tratta di un evento normale di pressione o di un pulsante, un evento di spostamento del mouse o il secondo clic di un evento di doppio clic.

> [!NOTE]
>Le coordinate della posizione del mouse sono espresse in termini di buffer dello schermo della console, non della finestra della console. È possibile che sia stato eseguito lo scorrimento del buffer dello schermo rispetto alla finestra, in modo che l'angolo superiore sinistro della finestra non sia necessariamente la coordinata (0, 0) del buffer dello schermo della console. Per determinare le coordinate del mouse rispetto al sistema di coordinate della finestra, sottrarre le coordinate di origine della finestra dalle coordinate della posizione del mouse. Utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per determinare le coordinate di origine della finestra.

Il membro **dwButtonState** della struttura [**del \_ \_ record dell'evento del mouse**](mouse-event-record-str.md) presenta un bit corrispondente a ogni pulsante del mouse. Il bit è 1 se il pulsante è inattivo e 0 se il pulsante è attivo. Un evento di rilascio del pulsante viene rilevato da un valore 0 per il membro **dwEventFlags** del **record dell' \_ evento \_ del mouse** e da una modifica del bit di un pulsante da 1 a 0. La funzione [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) Recupera il numero di pulsanti del mouse.

## <a name="buffer-resizing-events"></a>Eventi Buffer-Resizing

Il menu di una finestra della console consente all'utente di modificare le dimensioni del buffer dello schermo attivo; Questa modifica genera un evento di ridimensionamento del buffer. Gli eventi di ridimensionamento del buffer vengono inseriti nel buffer di input se la modalità di input della console è impostata su **Abilita \_ \_ input finestra** (ovvero la modalità predefinita è disabilitata).

Se l'evento di input è un evento di ridimensionamento del buffer, il membro dell' **evento** del [**\_ record di input**](input-record-str.md) è una struttura di [**\_ \_ \_ record delle dimensioni del buffer della finestra**](window-buffer-size-record-str.md) contenente la nuova dimensione del buffer dello schermo della console, espressa in righe e colonne della cella di tipo carattere.

Se l'utente riduce le dimensioni del buffer dello schermo della console, tutti i dati nella parte scartata del buffer vengono persi.

Le modifiche apportate alle dimensioni del buffer dello schermo della console in seguito alle chiamate dell'applicazione alla funzione [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) non vengono generate come eventi di ridimensionamento del buffer.
