---
title: Sequenze del terminale virtuale della console
description: Le sequenze di terminale virtuale sono sequenze di caratteri di controllo in grado di controllare lo spostamento del cursore, la modalità colore/tipo di carattere e altre operazioni quando vengono scritte nel flusso di output.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "93039149"
---
# <a name="console-virtual-terminal-sequences"></a>Sequenze del terminale virtuale della console


Le sequenze di terminale virtuale sono sequenze di caratteri di controllo in grado di controllare lo spostamento del cursore, la modalità colore/tipo di carattere e altre operazioni quando vengono scritte nel flusso di output. Le sequenze possono anche essere ricevute nel flusso di input in risposta a una sequenza di informazioni di query del flusso di output o come codifica dell'input utente quando viene impostata la modalità appropriata.

Per configurare questo comportamento, è possibile usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md). Alla fine di questo documento è incluso un esempio della modalità consigliata per abilitare i comportamenti del terminale virtuale.

Il comportamento delle sequenze seguenti si basa su VT100 e sulle tecnologie dell'emulatore di terminale derivate, in particolare sull'emulatore di terminale xterm. Per altre informazioni sulle sequenze di terminale, visitare i siti Web agli indirizzi <http://vt100.net> e <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Sequenze di output


Le sequenze di terminale seguenti vengono intercettate dall'host della console quando vengono scritte nel flusso di output se il flag ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING viene impostato sull'handle del buffer dello schermo usando la funzione [**SetConsoleMode**](setconsolemode.md). Si noti che il flag DISABLE\_NEWLINE\_AUTO\_RETURN può essere utile anche per emulare il posizionamento del cursore e il comportamento di scorrimento di altri emulatori di terminale in relazione ai caratteri scritti nella colonna finale di qualsiasi riga.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posizionamento semplice del cursore


In tutte le descrizioni seguenti ESC è sempre rappresentato dal valore esadecimale 0x1B. Non è necessario includere spazi nelle sequenze di terminale. Per informazioni su come vengono usate in pratica le sequenze, vedere l'[esempio](#example) alla fine di questo argomento.

Nella tabella seguente vengono descritte le sequenze di escape semplici con un solo comando di azione subito dopo il carattere ESC. Queste sequenze non hanno parametri e hanno effetto immediato.

Tutti i comandi inclusi in questa tabella sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) per posizionare il cursore.

Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer. Lo scorrimento, se disponibile, non si verificherà.


| Sequenza | Sintassi abbreviata | Comportamento |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | Cursore su di 1 |
| ESC B | CUD | Cursore giù di 1 |
| ESC C | CUF | Cursore avanti (verso destra) di 1 |
| ESC D | CUB | Cursore indietro (verso sinistra) di 1 |
| ESC M | RI | Indice inverso: esegue l'operazione inversa di \\n, sposta il cursore verso l'alto di una riga, mantiene la posizione orizzontale, scorre il buffer se necessario\* |
| ESC 7 | DECSC | Salva la posizione del cursore in memoria\*\* |
| ESC 8 | DECSR | Ripristina la posizione del cursore dalla memoria\*\* |



> [!NOTE]
>\* Se sono impostati i margini di scorrimento, RI all'interno dei margini scorrerà solo il contenuto dei margini e lascerà invariato il riquadro di visualizzazione (vedere Margini di scorrimento).
>
>\*\*Non sarà presente alcun valore salvato in memoria fino al primo utilizzo del comando di salvataggop. L'unico modo per accedere al valore salvato è tramite il comando di ripristino.

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posizionamento del cursore


Le tabelle seguenti includono le sequenze di tipo CSI (Control Sequence Introducer). Tutte le sequenze CSI iniziano con ESC (0x1B) seguito da \[ (parentesi quadra aperta, 0x5B) e possono contenere parametri di lunghezza variabile per specificare altre informazioni per ogni operazione. Tali informazioni saranno rappresentate dalla sintassi abbreviata &lt;n&gt;. Ogni tabella riportata di seguito è raggruppata per funzionalità, con note sotto ogni tabella che illustrano il funzionamento del gruppo.

Se non diversamente specificato, le regole seguenti si applicano a tutti i parametri:

- &lt;n&gt; rappresenta la distanza di spostamento ed è un parametro facoltativo
- Se &lt;n&gt; viene omesso o è uguale a 0, verrà considerato come 1
- &lt;n&gt; non può essere maggiore di 32.767 (valore short massimo)
- &lt;n&gt; non può essere un valore negativo

Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md).

Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer. Lo scorrimento, se disponibile, non si verificherà.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; A | CUU | Cursore su | Cursore su di &lt;n&gt; |
| ESC \[ &lt;n&gt; B | CUD | Cursore giù | Cursore giù di &lt;n&gt; |
| ESC \[ &lt;n&gt; C | CUF | Cursore avanti | Cursore avanti (verso destra) di &lt;n&gt; |
| ESC \[ &lt;n&gt; D | CUB | Cursore indietro | Cursore indietro (verso sinistra) di &lt;n&gt; |
| ESC \[ &lt;n&gt; E | CNL | Cursore riga successiva | Cursore giù di &lt;n&gt; righe dalla posizione corrente |
| ESC \[ &lt;n&gt; F | CPL | Cursore riga precedente | Cursore su &lt;n&gt; righe dalla posizione corrente |
| ESC \[ &lt;n&gt; G | CHA | Cursore assoluto orizzontale | Il cursore si sposta orizzontalmente alla posizione &lt;n&gt; nella riga corrente |
| ESC \[ &lt;n&gt; d | VPA | Assoluto posizione riga verticale | Il cursore si sposta verticalmente alla posizione &lt;n&gt; nella colonna corrente |
| ESC \[ &lt;y&gt; ; &lt;x&gt; H | CUP | Posizione cursore | \*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt; |
| ESC \[ &lt;y&gt; ; &lt;x&gt; f | HVP | Posizione verticale orizzontale | \*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt; |
| ESC \[ s | ANSISYSSC | Salvataggio cursore - Emulazione Ansi.sys | \*\*Senza parametri, esegue un'operazione di salvataggio del cursore come DECSC |
| ESC \[ u | ANSISYSSC | Ripristino cursore - Emulazione Ansi.sys | \*\*Senza parametri, esegue un'operazione di ripristino del cursore come DECRC |



> [!NOTE]
>\*I parametri &lt;x&gt; e &lt;y&gt; hanno le stesse limitazioni del valore &lt;n&gt; sopraindicato. Se &lt;x&gt; e &lt;y&gt; vengono omessi, verranno impostati su 1;1.
>
>\*\*La documentazione cronologica relativa ad ANSI.sys è disponibile nel sito Web all'indirizzo <https://msdn.microsoft.com/library/cc722862.aspx> e viene implementata per praticità e/o compatibilità.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilità del cursore


I comandi seguenti controllano la visibilità del cursore e del relativo stato intermittente. Le sequenze DECTCEM sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) per attivare o disattivare la visibilità del cursore.


| Sequenza | Codice | Descrizione | Comportamento |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 h | ATT160 | Abilitazione cursore di testo intermittente | Avvia lo stato intermittente del cursore |
| ESC \[ ? 12 l | ATT160 | Disabilitazione cursore di testo intermittente | Interrompe lo stato intermittente del cursore |
| ESC \[ ? 25 h | DECTCEM | Abilitazione cursore di testo in modalità Mostra | Mostra il cursore |
| ESC \[ ? 25 l | DECTCEM | Abilitazione cursore di testo in modalità Nascondi | Nasconde il cursore |

> [!TIP]
> Le sequenze di abilitazione terminano con un carattere H minuscolo (`h`), mentre le sequenze di disabilitazione terminano con un carattere L minuscolo (`l`).

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posizionamento del riquadro di visualizzazione


Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per spostare il contenuto del buffer della console.

**Attenzione** I nomi dei comandi sono fuorvianti. Il termine "scorrere" si riferisce alla direzione di spostamento del testo durante l'operazione, non alla modalità di spostamento del riquadro di visualizzazione.




| Sequenza | Codice | Descrizione | Comportamento |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; S | Unità di streaming (SU) | Scorrimento verso l'alto | Scorrimento del testo verso l'alto di &lt;n&gt;. Operazione nota anche come "panoramica in basso", dove le nuove righe vengono compilate a partire dalla parte inferiore dello schermo |
| ESC \[ &lt;n&gt; T | DS | Scorrimento verso il basso | Scorrimento verso il basso di &lt;n&gt;. Operazione nota anche come "panoramica in alto", dove le nuove righe vengono compilate a partire dalla parte superiore dello schermo |



Il testo viene spostato a partire dalla riga in cui si trova il cursore. Se il cursore si trova nella riga centrale del riquadro di visualizzazione, lo scorrimento verso l'alto determinerà lo spostamento della metà inferiore del riquadro e l'inserimento di righe vuote in fondo. Lo scorrimento verso il basso determinerà lo spostamento della metà superiore delle righe del riquadro di visualizzazione e l'inserimento di nuove righe in cima.

È inoltre importante notare che lo scorrimento verso l'alto e lo scorrimento verso il basso dipendono anche dai margini di scorrimento. Lo scorrimento verso l'alto e lo scorrimento verso il basso non influiranno sulle righe esterne ai margini di scorrimento.

Il valore predefinito per &lt;n&gt; è 1 che facoltativamente può essere omesso.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modifica del testo


Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) e [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per modificare il contenuto del buffer di testo.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; @ | ICH | Inserimento carattere | Inserisce &lt;n&gt; spazi nella posizione corrente del cursore, spostando tutto il testo esistente verso destra. All'uscita dallo schermo, il testo a destra viene rimosso. |
| ESC \[ &lt;n&gt; P | DCH | Eliminazione carattere | Elimina &lt;n&gt; caratteri nella posizione corrente del cursore, scalando gli spazi dal bordo destro dello schermo. |
| ESC \[ &lt;n&gt; X | ECH | Cancellazione carattere | Cancella &lt;n&gt; caratteri dalla posizione corrente del cursore sovrascrivendoli con uno spazio. |
| ESC \[ &lt;n&gt; L | IL | Inserisci riga | Inserisce &lt;n&gt; righe nel buffer in corrispondenza della posizione del cursore. La riga in cui si trova il cursore e le righe sottostanti verranno spostate verso il basso. |
| ESC \[ &lt;n&gt; M | DL | Elimina riga | Elimina &lt;n&gt; righe dal buffer, a partire dalla riga in cui si trova il cursore. |



> [!NOTE]
>Per IL e DL sono interessate solo le righe incluse nei margini di scorrimento (vedere Margini di scorrimento). Se non è impostato alcun margine, i bordi predefiniti corrispondono al riquadro di visualizzazione corrente. Se le righe vengono spostate sotto i margini, vengono rimosse. Quando le righe vengono eliminate, vengono inserite righe vuote in fondo ai margini. Le linee esterne al riquadro di visualizzazione non sono mai interessate.

Per ognuna delle sequenze, il valore predefinito di &lt;n&gt;, se omesso, è 0.



Per i comandi seguenti il parametro &lt;n&gt; ha 3 valori validi:

- 0 cancella il contenuto dalla posizione corrente del cursore (inclusa) alla fine della riga o del display
- 1 cancella il contenuto dall'inizio della riga o del display fino alla posizione corrente del cursore inclusa
- 2 cancella il contenuto di tutta la riga o di tutto il display


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; J | ED | Cancellazione nel display | Sostituisce tutto il testo presente nel riquadro di visualizzazione o nello schermo, specificato da &lt;n&gt; con spazi |
| ESC \[ &lt;n&gt; K | EL | Cancellazione nella riga | Sostituisce tutto il testo presente nella riga con il cursore specificato da &lt;n&gt; con spazi |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formattazione del testo


Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**SetConsoleTextAttribute**](setconsoletextattribute.md) per regolare la formattazione di tutte le operazioni di scrittura future nel buffer di testo di output della console.

Questo comando è speciale in quanto la posizione &lt;n&gt; indicata di seguito può accettare da 0 a 16 parametri separati da punti e virgola.

Se non è specificato alcun parametro, si considera come se fosse specificato un singolo parametro 0.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt;n&gt; m | SGR | Impostazione rendering grafica | Imposta il formato dello schermo e del testo come specificato da &lt;n&gt; |



La seguente tabella di valori può essere usata in &lt;n&gt; per rappresentare modalità di formattazione diverse.

Le modalità di formattazione vengono applicate da sinistra a destra. Se si applicano opzioni di formattazione concorrenti, l'opzione più a destra avrà la precedenza.

Per le opzioni che specificano i colori, i colori verranno usati come definito nella tabella dei colori della console, che può essere modificata usando l'API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md). Se la tabella viene modificata in modo che la posizione "blu" visualizzi una sfumatura di rosso RGB, tutte le chiamate a **Blu primo piano** visualizzeranno il colore rosso fino a quando questa opzione non viene modificata.


| Valore | Descrizione | Comportamento |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | Predefinito | Ripristina lo stato predefinito di tutti gli attributi precedente alla modifica |
| 1 | Grassetto/Brillante | Applica il flag di luminosità/intensità al colore di primo piano |
| 4 | Sottolineato | Aggiunge la sottolineatura |
| 24 | Nessuna sottolineatura | Rimuove la sottolineatura |
| 7 | Negativo | Scambia i colori di primo piano e di sfondo |
| 27 | Positivo (non negativo) | Ripristina il valore normale di primo piano/sfondo |
| 30 | Nero primo piano | Applica il colore nero non grassetto/brillante in primo piano |
| 31 | Rosso primo piano | Applica il colore rosso non grassetto/brillante in primo piano |
| 32 | Verde primo piano | Applica il colore verde non grassetto/brillante in primo piano |
| 33 | Giallo primo piano | Applica il colore giallo non grassetto/brillante in primo piano |
| 34 | Blu primo piano | Applica il colore blu non grassetto/brillante in primo piano |
| 35 | Magenta primo piano | Applica il color magenta non grassetto/brillante in primo piano |
| 36 | Ciano primo piano | Applica il color ciano non grassetto/brillante in primo piano |
| 37 | Bianco primo piano | Applica il colore bianco non grassetto/brillante in primo piano |
| 38 | Valore esteso primo piano | Applica il valore di colore esteso al primo piano (vedere i dettagli di seguito) |
| 39 | Valore predefinito primo piano | Applica solo la parte in primo piano delle impostazioni predefinite (vedere 0) |
| 40 | Nero sfondo | Applica il colore nero non grassetto/brillante allo sfondo |
| 41 | Rosso sfondo | Applica il colore rosso non grassetto/brillante allo sfondo |
| 42 | Verde sfondo | Applica il colore verde non grassetto/brillante allo sfondo |
| 43 | Giallo sfondo | Applica il colore giallo non grassetto/brillante allo sfondo |
| 44 | Blu sfondo | Applica il colore blu non grassetto/brillante allo sfondo |
| 45 | Magenta sfondo | Applica il color magenta non grassetto/brillante allo sfondo |
| 46 | Ciano sfondo | Applica il color ciano non grassetto/brillante allo sfondo |
| 47 | Bianco sfondo | Applica il colore bianco non grassetto/brillante allo sfondo |
| 48 | Valore esteso sfondo | Applica il valore di colore esteso allo sfondo (vedere i dettagli di seguito) |
| 49 | Valore predefinito sfondo | Applica solo la parte dello sfondo delle impostazioni predefinite (vedere 0) |
| 90 | Nero primo piano brillante | Applica il colore nero grassetto/brillante in primo piano |
| 91 | Rosso primo piano brillante | Applica il colore rosso grassetto/brillante in primo piano |
| 92 | Verde primo piano brillante | Applica il colore verde grassetto/brillante in primo piano |
| 93 | Giallo primo piano brillante | Applica il colore giallo grassetto/brillante in primo piano |
| 94 | Blu primo piano brillante | Applica il colore blu grassetto/brillante in primo piano |
| 95 | Magenta primo piano brillante | Applica il color magenta grassetto/brillante in primo piano |
| 96 | Ciano primo piano brillante | Applica il color ciano grassetto/brillante in primo piano |
| 97 | Bianco primo piano brillante | Applica il colore bianco grassetto/brillante allo sfondo |
| 100 | Nero sfondo brillante | Applica il colore nero grassetto/brillante allo sfondo |
| 101 | Rosso sfondo brillante | Applica il colore rosso grassetto/brillante allo sfondo |
| 102 | Verde sfondo brillante | Applica il colore verde grassetto/brillante allo sfondo |
| 103 | Giallo sfondo brillante | Applica il colore giallo grassetto/brillante allo sfondo |
| 104 | Blu sfondo brillante | Applica il colore blu grassetto/brillante allo sfondo |
| 105 | Magenta sfondo brillante | Applica il color magenta grassetto/brillante allo sfondo |
| 106 | Ciano sfondo brillante | Applica il color ciano grassetto/brillante allo sfondo |
| 107 | Bianco sfondo brillante | Applica il colore bianco grassetto/brillante allo sfondo |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colori estesi

Alcuni emulatori di terminale virtuale supportano una tavolozza di colori più estesa dei 16 colori forniti dalla console di Windows. Per questi colori estesi, la console di Windows sceglierà il colore appropriato più vicino dalla tavola dei 16 colori esistente per la visualizzazione. Diversamente dai valori SGR tipici sopraindicati, i valori estesi utilizzano parametri aggiuntivi dopo l'indicatore iniziale, in base alle informazioni riportate nella tabella seguente.


| Sottosequenza SGR | Descrizione |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Imposta il colore di primo piano sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\* |
| 48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | Imposta il colore di sfondo sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\* |
| 38 ; 5 ; &lt;s&gt; | Imposta il colore di primo piano sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\* |
| 48 ; 5 ; &lt;s&gt; | Imposta il colore di sfondo sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\* |



\*Le tavolozze da 88 e 256 colori gestite internamente per il confronto sono basate sull'emulatore di terminale xterm. Non è possibile modificare le tabelle di confronto o di arrotondamento in questa fase.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colori dello schermo


Il comando seguente consente all'applicazione di impostare i valori della tavolozza dei colori dello schermo su qualsiasi valore RGB.

I valori RGB devono essere valori esadecimali compresi tra `0` e `ff` e separati dal carattere barra (ad esempio, `rgb:1/24/86`).

Si noti che questa sequenza è di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza inizia con "\\x1b\]", non con "\\x1b\[".


| Sequenza | Descrizione | Comportamento |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC | Modifica colori schermo | Imposta l'indice &lt;i&gt; della tavolozza dei colori dello schermo sui valori RGB specificati in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifiche della modalità


Si tratta di sequenze che controllano le modalità di input. Esistono due diversi set di modalità di input, ovvero la modalità tasti cursore e la modalità tasti del tastierino. La modalità tasti cursore controlla le sequenze generate dai tasti di direzione, nonché da Home e Fine, mentre la modalità tasti del tastierino controlla le sequenze generate principalmente dai tasti sul tastierino numerico, nonché dai tasti funzione.

Ognuna di queste modalità è una semplice impostazione booleana. La modalità tasti cursore è impostata su normale (impostazione predefinita) o applicazione e la modalità tasti del tastierino è impostata su numerica (impostazione predefinita) o applicazione.

Per le sequenze generate in queste modalità, vedere le sezioni Tasti cursore e Tastierino numerico.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | Abilitazione modalità applicazione tastierino | I tasti del tastierino generano le relative sequenze in modalità applicazione. |
| ESC &gt; | DECKPNM | Abilitazione modalità numerica tastierino | I tasti del tastierino genereranno le relative sequenze in modalità numerica. |
| ESC \[ ? 1 ora | DECCKM | Abilitazione modalità applicazione tasti cursore | I tasti del tastierino generano le relative sequenze in modalità applicazione. |
| ESC \[ ? 1 l | DECCKM | Disabilitazione modalità applicazione tasti cursore (usare la modalità normale) | I tasti del tastierino genereranno le relative sequenze in modalità numerica. |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Stato delle query


Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console Get\* per recuperare informazioni sullo stato corrente del buffer della console.

> [!NOTE]
>Queste query generano le risposte nel flusso di input della console subito dopo essere state riconosciute nel flusso di output durante l'impostazione di ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING. Il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT non si applica ai comandi di query perché si presuppone che un'applicazione che esegue la query voglia sempre ricevere la risposta.




| Sequenza | Codice | Descrizione | Comportamento |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Segnalazione posizione cursore | Genera la posizione del cursore come: ESC \[ &lt;r&gt; ; &lt;c&gt; R dove &lt;r&gt; = riga del cursore e &lt;c&gt; = colonna del cursore |
| ESC \[ 0 c | DA | Attributi dispositivo | Segnala l'identità del terminale. Genera "\\x1b\[?1;0c", per indicare "VT101 senza opzioni". |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabulazioni


Benché la console di Windows preveda tradizionalmente che la larghezza delle tabulazioni sia di otto caratteri, le applicazioni \*nix che utilizzano determinate sequenze possono modificare il punto in cui si trovano le tabulazioni nelle finestre della console per ottimizzare lo spostamento del cursore in base all'applicazione.

Le sequenze seguenti consentono a un'applicazione di impostare le posizioni delle tabulazioni nella finestra della console, rimuoverle e spostarsi da una posizione all'altra.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | Tabulazione orizzontale impostata | Imposta una tabulazione nella colonna corrente in cui si trova il cursore. |
| ESC \[ &lt;n&gt; I | CHT | Tabulazione orizzontale (in avanti) del cursore | Sposta il cursore nella colonna successiva (stessa riga) con una tabulazione. Se non sono presenti altre tabulazioni, il cursore si sposta nell'ultima colonna della riga. Se il cursore si trova nell'ultima colonna, passa alla prima colonna della riga successiva. |
| ESC \[ &lt;n&gt; Z | CBT | Tabulazione cursore indietro | Sposta il cursore nella colonna precedente (stessa riga) con una tabulazione. Se non sono presenti altre tabulazioni, sposta il cursore nella prima colonna. Se il cursore si trova nella prima colonna, non viene spostato. |
| ESC \[ 0 g | TBC | Cancellazione tabulazione (colonna corrente) | Cancella la tabulazione, se presente, nella colonna corrente. In caso contrario, non esegue alcuna operazione. |
| ESC \[ 3 g | TBC | Cancellazione tabulazione (tutte le colonne) | Cancella tutte le tabulazioni attualmente impostate. |



- Per CHT e CBT, &lt;n&gt; è un parametro facoltativo (valore predefinito = 1) che indica il numero di volte in cui spostare il cursore nella direzione specificata.
- Se non sono presenti tabulazioni impostate tramite HTS, CHT e CBT, la prima e l'ultima colonna della finestra verranno considerate come le uniche due tabulazioni.
- Se si usa HTS per impostare una tabulazione, la console passerà alla successiva tabulazione nell'output di un carattere di tabulazione (0x09,'\\t'), come avviene quando si usa CHT.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designare il set di caratteri


Le sequenze seguenti consentono a un programma di modificare il mapping del set di caratteri attivo. In questo modo un programma può generare caratteri ASCII a 7 bit, ma visualizzarli come altri glifi nello schermo del terminale. Attualmente gli unici due set di caratteri supportati sono ASCII (impostazione predefinita) e il set di caratteri grafici speciali DEC. Per un elenco di tutti i caratteri rappresentati dal set di caratteri grafici speciali DEC, visitare il sito Web all'indirizzo <http://vt100.net/docs/vt220-rm/table2-4.html>.


| Sequenza | Descrizione | Comportamento |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | Designazione set di caratteri DEC Line Drawing | Abilita la modalità DEC Line Drawing |
| ESC ( B | Designazione set di caratteri ASCII Stati Uniti | Abilita la modalità ASCII (impostazione predefinita) |



In particolare, la modalità DEC Line Drawing viene usata per disegnare i bordi nelle applicazioni console. La tabella seguente illustra il mapping tra caratteri ASCII e caratteri DEC Line Drawing.


| Hex | ASCII | DEC Line Drawing |
|------|-------|------------------|
| 0x6a | j | ┘ |
| 0x6b | k | ┐ |
| 0x6c | l | ┌ |
| 0x6d | m | └ |
| 0x6e | n | ┼ |
| 0x71 | q | ─ |
| 0x74 | u | ├ |
| 0x75 | u | ┤ |
| 0x76 | v | ┴ |
| 0x77 | w | ┬ |
| 0x78 | x | │ |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Margini di scorrimento


Le sequenze seguenti consentono a un programma di configurare l'"area di scorrimento" dello schermo interessata dalle operazioni di scorrimento. Si tratta di un subset di righe che vengono regolate quando altrimenti lo schermo scorrerebbe, ad esempio per una sequenza '\\n' o RI. Questi margini influiscono anche sulle righe modificate da Inserimento riga (IL) ed Eliminazione riga (DL), Scorrimento verso l'alto (SU) e Scorrimento verso il basso (SD).

I margini di scorrimento possono essere utili soprattutto per fare in modo che una parte dello schermo non scorra quando il resto dello schermo viene riempito, ad esempio con una barra del titolo nella parte superiore o una barra di stato nella parte inferiore dell'applicazione.

Per DECSTBM sono disponibili due parametri facoltativi, &lt;t&gt; e &lt;b&gt;, usati per specificare le righe che rappresentano la riga superiore e quella inferiore dell'area di scorrimento incluse. Se i parametri vengono omessi, &lt;t&gt; viene impostato automaticamente su 1 e &lt;b&gt; sull'altezza del riquadro di visualizzazione corrente.

I margini di scorrimento vanno considerati per buffer. È quindi importante che il buffer alternativo e il buffer principale mantengano impostazioni separate dei margini di scorrimento (di conseguenza, un'applicazione a schermo intero nel buffer alternativo non comprometterà i margini del buffer principale).


| Sequenza | Codice | Descrizione | Comportamento |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt;t&gt; ; &lt;b&gt; r | DECSTBM | Impostazione area di scorrimento | Imposta i margini di scorrimento VT del riquadro di visualizzazione. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titolo della finestra


I comandi seguenti consentono all'applicazione di impostare il titolo della finestra della console sul parametro &lt;stringa&gt; specificato. Per essere accettata, la stringa deve contenere meno di 255 caratteri. L'operazione è equivalente alla chiamata di SetConsoleTitle con la stringa specificata.

Si noti che queste sequenze sono di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza iniziano con "\\x1b\]", non con "\\x1b\[".


| Sequenza | Descrizione | Comportamento |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0 ; &lt;stringa&gt; BEL | Impostazione icona e titolo finestra | Imposta il titolo della finestra della console su &lt;stringa&gt;. |
| ESC \] 2 ; &lt;stringa&gt; BEL | Impostazione titolo finestra | Imposta il titolo della finestra della console su &lt;stringa&gt;. |



Il carattere finale in queste sequenze è il carattere "Bell", '\\x07'

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Buffer alternativo dello schermo


Le applicazioni di tipo \*nix utilizzano spesso un buffer alternativo dello schermo, in modo da poter modificare l'intero contenuto del buffer senza influire sull'applicazione che le ha avviate. Il buffer alternativo è esattamente delle dimensioni della finestra, senza area di scrollback.

Per un esempio di questo comportamento, si prenda in considerazione quando vim viene avviato da bash. Vim usa l'intero schermo per modificare il file e quindi, tornando a bash, lascia invariato il buffer originale.


| Sequenza | Descrizione | Comportamento |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Uso buffer alternativo dello schermo | Passa a un nuovo buffer alternativo dello schermo. |
| ESC \[ ? 1 0 4 9 l | Uso buffer principale dello schermo | Passa al buffer principale. |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Larghezza della finestra


Le sequenze seguenti possono essere usate per controllare la larghezza della finestra della console. Sono approssimativamente equivalenti alla chiamata dell'API della console SetConsoleScreenBufferInfoEx per impostare la larghezza della finestra.


| Sequenza | Codice | Descrizione | Comportamento |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | DECCOLM | Impostazione numero di colonne su 132 | Imposta la larghezza della console su una larghezza pari a 132 colonne. |
| ESC \[ ? 3 l | DECCOLM | Impostazione numero di colonne su 80 | Imposta la larghezza della console su una larghezza pari a 80 colonne. |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft reset


La sequenza seguente può essere usata per reimpostare i valori predefiniti di determinate proprietà. Le proprietà seguenti vengono reimpostate sui valori predefiniti indicati di seguito (sono elencate anche le sequenze che controllano tali proprietà):

- Visibilità cursore: visibile (DECTEM)
- Tastierino numerico: modalità numerica (DECNKM)
- Modalità tasti cursore: modalità normale (DECCKM)
- Margini superiore e inferiore: superiore = 1, inferiore = altezza console (DECSTBM)
- Set di caratteri: ASCII Stati Uniti
- Rendering grafica: predefinito/off (SGR)
- Salvataggio stato cursore: posizione Home (0,0) (DECSC)


| Sequenza | Codice | Descrizione | Comportamento |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Soft reset | Ripristina i valori predefiniti di determinate impostazioni del terminale. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Sequenze di input


Le sequenze di terminale seguenti vengono generate dall'host della console nel flusso di input se il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT viene impostato sull'handle del buffer di input usando il flag SetConsoleMode.

Sono disponibili due modalità interne che controllano le sequenze generate per i tasti di input specificati: la modalità tasti cursore e la modalità tasti del tastierino. Queste modalità sono descritte nella sezione Modifiche della modalità.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Tasti cursore


| Chiave | Modalità normale | Modalità applicazione |
|-------------|-------------|------------------|
| Freccia SU | ESC \[ A | ESC O A |
| Freccia GIÙ | ESC \[ B | ESC O B |
| Freccia DESTRA | ESC \[ C | ESC O C |
| Freccia SINISTRA | ESC \[ D | ESC O D |
| Home | ESC \[ H | ESC O H |
| Fine | ESC \[ F | ESC O F |



Inoltre, se si preme CTRL con uno qualsiasi di questi tasti, vengono generate le sequenze seguenti, indipendentemente dalla modalità tasti cursore:


| Chiave | Qualsiasi modalità |
|--------------------|----------------|
| CTRL + freccia SU | ESC \[ 1 ; 5 A |
| CTRL + freccia GIÙ | ESC \[ 1 ; 5 B |
| CTRL + freccia DESTRA | ESC \[ 1 ; 5 C |
| CTRL + freccia SINISTRA | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Tastierino numerico e tasti funzione


| Chiave | Sequenza |
|-----------|--------------|
| Backspace | 0x7f (DEL) |
| Sospendi | 0x1a (SUB) |
| Carattere speciale di escape | 0x1b (ESC) |
| Insert | ESC \[ 2 ~ |
| Elimina | ESC \[ 3 ~ |
| PGSU | ESC \[ 5 ~ |
| PGGIÙ | ESC \[ 6 ~ |
| F1 | ESC O P |
| F2 | ESC O Q |
| F3 | ESC O R |
| F4 | ESC O S |
| F5 | ESC \[ 1 5 ~ |
| F6 | ESC \[ 1 7 ~ |
| F7 | ESC \[ 1 8 ~ |
| F8 | ESC \[ 1 9 ~ |
| F9 | ESC \[ 2 0 ~ |
| F10 | ESC \[ 2 1 ~ |
| F11 | ESC \[ 2 3 ~ |
| F12 | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificatori

Il tasto ALT viene trattato anteponendo alla sequenza un carattere di escape: ESC &lt;c&gt; dove &lt;c&gt; è il carattere passato dal sistema operativo. La combinazione di tasti ALT + CTRL viene gestita allo stesso modo, tranne per il fatto che il sistema operativo avrà preliminarmente spostato il tasto &lt;c&gt; sul carattere di controllo appropriato che verrà inoltrato all'applicazione.

Il tasto CTRL viene in genere passato esattamente come viene ricevuto dal sistema. Si tratta in genere di un singolo carattere spostato nello spazio riservato al carattere di controllo (0x0-0x1f). Ad esempio, CTRL + @ (0x40) diventa NUL (0x00), CTRL + \[ (0x5b) diventa ESC (0x1b) e così via. Alcune combinazioni con il tasto CTRL vengono trattate in modo speciale in base alla tabella seguente:


| Chiave | Sequenza |
|--------------------|----------------|
| CTRL+BARRA SPAZIATRICE | 0x00 (NUL) |
| CTRL + freccia SU | ESC \[ 1 ; 5 A |
| CTRL + freccia GIÙ | ESC \[ 1 ; 5 B |
| CTRL + freccia DESTRA | ESC \[ 1 ; 5 C |
| CTRL + freccia SINISTRA | ESC \[ 1 ; 5 D |



> [!NOTE]
>La combinazione <kbd>CTRL</kbd> sinistra + <kbd>ALT</kbd> destra viene trattata come ALT GR. Quando entrambi gli elementi vengono visualizzati insieme, vengono rimossi e il valore Unicode del carattere presentato dal sistema viene passato nella destinazione. Il sistema eseguirà la conversione preliminare dei valori di ALT GR in base alle impostazioni di input di sistema correnti.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Esempi


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Esempio di sequenze di terminale SGR

Il codice seguente fornisce alcuni esempi di formattazione del testo.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return GetLastError();
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return GetLastError();
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return GetLastError();
 }

 // Try some Set Graphics Rendition (SGR) terminal escape sequences
 wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
 wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
 wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
 wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
 wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
 wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
 wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
 wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

 return 0;
}
```

> [!NOTE]
>Nell'esempio precedente la stringa '`\x1b[31m`' è l'implementazione di **ESC \[ &lt;n&gt; m** dove &lt;n&gt; è uguale a 31.



La figura seguente mostra l'output dell'esempio di codice precedente.

![output della console con il comando sgr](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Esempio di abilitazione dell'elaborazione del terminale virtuale

Il codice seguente fornisce un esempio della modalità consigliata per abilitare l'elaborazione del terminale virtuale per un'applicazione. Lo scopo dell'esempio è dimostrare quanto segue:

1. La modalità esistente deve sempre essere recuperata tramite GetConsoleMode e analizzata prima di essere impostata con SetConsoleMode.

2. Verificare se SetConsoleMode restituisce `0` e GetLastError restituisce STATUS\_INVALID\_PARAMETER è il meccanismo corrente per determinare l'esecuzione in un sistema di livello inferiore. Un'applicazione che riceve STATUS\_INVALID\_PARAMETER con uno dei flag di modalità della console più recenti nel campo bit dovrebbe scalare automaticamente il comportamento e riprovare.

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }
 HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
 if (hIn == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwOriginalOutMode = 0;
 DWORD dwOriginalInMode = 0;
 if (!GetConsoleMode(hOut, &dwOriginalOutMode))
 {
 return false;
 }
 if (!GetConsoleMode(hIn, &dwOriginalInMode))
 {
 return false;
 }

 DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
 DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

 DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // we failed to set both modes, try to step down mode gracefully.
 dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // Failed to set any VT mode, can't do anything here.
 return -1;
 }
 }

 DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
 if (!SetConsoleMode(hIn, dwInMode))
 {
 // Failed to set VT input mode, can't do anything here.
 return -1;
 }

 return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Esempio di alcune funzionalità dell'aggiornamento dell'anniversario

L'esempio seguente è destinato a essere un esempio di codice più affidabile che usa una serie di sequenze di escape per modificare il buffer, con particolare attenzione alle funzionalità aggiunte nell'aggiornamento dell'anniversario per Windows 10.

Questo esempio usa il buffer alternativo dello schermo, la modifica delle tabulazioni, l'impostazione dei margini di scorrimento e la modifica del set di caratteri.

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return false;
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return false;
 }
 return true;
}

void PrintVerticalBorder()
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // bright yellow on bright blue
 printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
 printf(CSI "0m"); // restore color
 printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // Make the border bright yellow on bright blue
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
{
 printf(CSI "%d;1H", Size.Y);
 printf(CSI "K"); // clear the line
 printf(pszMessage); 
}

int __cdecl wmain(int argc, WCHAR* argv[])
{ 
 argc; // unused
 argv; // unused
 //First, enable VT mode
 bool fSuccess = EnableVTMode();
 if (!fSuccess)
 {
 printf("Unable to enter VT processing mode. Quitting.\n");
 return -1;
 }
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 printf("Couldn't get the console handle. Quitting.\n");
 return -1;
 }

 CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
 GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
 COORD Size;
 Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
 Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

 // Enter the alternate buffer
 printf(CSI "?1049h");

 // Clear screen, tab stops, set, stop at columns 16, 32
 printf(CSI "1;1H");
 printf(CSI "2J"); // Clear screen

 int iNumTabStops = 4; // (0, 20, 40, width)
 printf(CSI "3g"); // clear all tab stops
 printf(CSI "1;20H"); // Move to column 20
 printf(ESC "H"); // set a tab stop

 printf(CSI "1;40H"); // Move to column 40
 printf(ESC "H"); // set a tab stop

 // Set scrolling margins to 3, h-2
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
 PrintHorizontalBorder(Size, false);

 wchar_t wch;

 // draw columns
 printf(CSI "3;1H"); 
 int line = 0;
 for (line = 0; line < iNumLines * iNumTabStops; line++)
 {
 PrintVerticalBorder();
 if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
 printf("\t"); // advance to next tab stop

 }

 PrintStatusLine("Press any key to see text printed between tab stops.", Size);
 wch = _getwch();

 // Fill columns with output
 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines; line++)
 {
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
 {
 printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
 printf("\r"); //return to first col in buffer
 }
 }

 PrintStatusLine("Press any key to exit", Size);
 wch = _getwch();

 // Exit the alternate buffer
 printf(CSI "?1049l");

}
```








