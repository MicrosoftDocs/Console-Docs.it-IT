---
title: Sequenze di terminali virtuali console
description: Le sequenze di terminali virtuali sono sequenze di caratteri di controllo che possono controllare lo spostamento del cursore, la modalità colore/carattere e altre operazioni quando vengono scritte nel flusso di output.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: d05aa6f44cc97478d4eb2aba25587b2506e84a98
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059969"
---
# <a name="console-virtual-terminal-sequences"></a>Sequenze di terminali virtuali console


Le sequenze di terminali virtuali sono sequenze di caratteri di controllo che possono controllare lo spostamento del cursore, la modalità colore/carattere e altre operazioni quando vengono scritte nel flusso di output. Le sequenze possono anche essere ricevute nel flusso di input in risposta a una sequenza di informazioni di query del flusso di output o come codifica dell'input utente quando viene impostata la modalità appropriata.

Per configurare questo comportamento, è possibile usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) . Alla fine di questo documento è incluso un esempio della modalità consigliata per abilitare i comportamenti dei terminali virtuali.

Il comportamento delle sequenze seguenti si basa sulle tecnologie dell'emulatore di terminale VT100 e derivato, in particolare l'emulatore di terminale xterm. Altre informazioni sulle sequenze di terminali sono disponibili in <http://vt100.net> e in <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Sequenze di output


Le sequenze terminali seguenti vengono intercettate dall'host della console quando vengono scritte nel flusso di output, se il flag di ABILITAzione del \_ \_ terminale virtuale \_ è impostato sull'handle del buffer dello schermo mediante la funzione [**SetConsoleMode**](setconsolemode.md) . Si noti che il \_ \_ \_ flag di restituzione automatica della nuova riga può essere utile anche per emulare il posizionamento del cursore e il comportamento di scorrimento di altri emulatori terminali in relazione ai caratteri scritti nella colonna finale in una riga.

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posizionamento semplice del cursore


In tutte le descrizioni seguenti, ESC è sempre il valore esadecimale 0x1B. Non è necessario includere spazi nelle sequenze di terminali. Per un esempio di come queste sequenze vengono usate in pratica, vedere l' [esempio](#example) alla fine di questo argomento.

Nella tabella seguente vengono descritte le sequenze di escape semplici con un solo comando di azione subito dopo il carattere ESC. Queste sequenze non hanno parametri e hanno effetto immediato.

Tutti i comandi in questa tabella sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) per posizionare il cursore.

Lo spostamento del cursore verrà limitato dal viewport corrente nel buffer. Lo scorrimento, se disponibile, non si verificherà.


| Sequenza | Sintassi abbreviata | Comportamento                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A    | CUU       | Cursore su 1                                                                                                                                |
| ESC B    | CUD       | Cursore in basso di 1                                                                                                                              |
| ESC C    | CUF       | Cursore in poi (destra) di 1                                                                                                                   |
| ESC D    | CUB       | Cursore indietro (sinistra) di 1                                                                                                                   |
| ESC M    | RI        | Indice inverso: esegue l'operazione inversa di \\ n, sposta il cursore verso l'alto di una riga, mantiene la posizione orizzontale, scorre il buffer se necessario\* |
| ESC 7    | DECSC     | Salva posizione cursore in memoria\*\*                                                                                                            |
| ESC 8    | DECSR     | Ripristina posizione cursore dalla memoria\*\*                                                                                                       |



**Nota**  
\* Se sono impostati margini di scorrimento, il RI all'interno dei margini scorrerà solo il contenuto dei margini e rimarrà invariato il viewport. (Vedere margini di scorrimento)

\*\*Non verrà salvato alcun valore in memoria fino al primo utilizzo del comando Save. L'unico modo per accedere al valore salvato è con il comando Restore.



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posizionamento del cursore


Le tabelle seguenti comprendono le sequenze di tipo CSI (Control Sequence Introducr). Tutte le sequenze CSI iniziano con ESC (0x1B) seguito da \[ (parentesi quadra aperta, 0x5b) e possono contenere parametri di lunghezza variabile per specificare altre informazioni per ogni operazione. Questa operazione sarà rappresentata dall'abbreviazione &lt; n &gt; . Ogni tabella riportata di seguito è raggruppata per funzionalità con note sotto ogni tabella che illustra il funzionamento del gruppo.

Per tutti i parametri, le regole seguenti si applicano se non diversamente specificato:

- &lt;n &gt; rappresenta la distanza da spostare ed è un parametro facoltativo
- Se &lt; n &gt; viene omesso o è uguale a 0, verrà considerato come 1
- &lt;n &gt; non può essere maggiore di 32.767 (valore short massimo)
- &lt;n &gt; non può essere negativo

Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) .

Lo spostamento del cursore verrà limitato dal viewport corrente nel buffer. Lo scorrimento, se disponibile, non si verificherà.


| Sequenza                       | Codice      | Descrizione                         | Comportamento                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; A             | CUU       | Cursore su                           | Cursore per &lt; n&gt;                                                                                                     |
| ESC \[ &lt; n &gt; B             | CUD       | Cursore in basso                         | Cursore verso il basso per &lt; n&gt;                                                                                                   |
| ESC \[ &lt; n &gt; C             | CUF       | Cursore in su                      | Cursore in poi (destra) per &lt; n&gt;                                                                                        |
| ESC \[ &lt; n &gt; D             | CUB       | Cursore indietro                     | Cursore indietro (a sinistra) per &lt; n&gt;                                                                                        |
| ESC \[ &lt; n &gt; E             | CNL       | Riga successiva cursore                    | Cursore verso il basso fino all'inizio della &lt; n &gt; riga nel viewport                                                               |
| ESC \[ &lt; n &gt; F             | CPL       | Riga precedente cursore                | Cursore fino all'inizio della &lt; n &gt; riga nel viewport                                                                 |
| ESC \[ &lt; n &gt; G             | CHA       | Assoluto cursore orizzontale          | Il cursore passa &lt; alla &gt; Posizione n orizzontalmente nella riga corrente                                                      |
| ESC \[ &lt; n &gt; d             | VPA       | Posizione assoluta linea verticale     | Il cursore passa alla &lt; &gt; Posizione n verticalmente nella colonna corrente                                                  |
| ESC \[ &lt; y &gt; ; &lt; x &gt; H | CUP       | Posizione cursore                     | \*Il cursore passa a &lt; x &gt; ; &lt; &gt; coordinata y all'interno del viewport, dove &lt; x &gt; è la colonna della &lt; &gt; linea y |
| ESC \[ &lt; y &gt; ; &lt; x &gt; f | HVP       | Posizione verticale orizzontale        | \*Il cursore passa a &lt; x &gt; ; &lt; &gt; coordinata y all'interno del viewport, dove &lt; x &gt; è la colonna della &lt; &gt; linea y |
| ESC \[ s                       | ANSISYSSC | Salva cursore-emulazione Ansi.sys    | \*\*Senza parametri, esegue un'operazione di salvataggio del cursore, ad esempio DECSC                                                        |
| \[U ESC                       | ANSISYSSC | Restore Cursor-Ansi.sys emulazione | \*\*Senza parametri, esegue un'operazione di ripristino del cursore, ad esempio DECRC                                                     |



**Nota**  
\*&lt;&gt; &lt; i parametri x e y &gt; hanno le stesse limitazioni di &lt; n &gt; sopra. Se &lt; &gt; le x e &lt; y &gt; vengono omesse, verranno impostate su 1; 1.

\*\*ANSI.sys documentazione cronologica è reperibile in <https://msdn.microsoft.com/library/cc722862.aspx> ed è implementata per praticità/compatibilità.



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilità del cursore


I comandi seguenti consentono di controllare la visibilità del cursore e del relativo stato intermittente. Le sequenze DECTCEM sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) per impostare la visibilità del cursore.


| Sequenza      | Codice    | Descrizione                  | Comportamento                  |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 ore | ATT160  | Abilitazione del cursore di testo  | Avvia il cursore lampeggiante |
| ESC \[ ? 12 l | ATT160  | Disabilitazione del cursore di testo  | Interrompi l'intermittenza del cursore  |
| ESC \[ ? 25 ore | DECTCEM | Mostra modalità di abilitazione cursore testo | Mostra cursore           |
| ESC \[ ? 25 l | DECTCEM | Nascondi modalità di abilitazione cursore testo | Nascondi cursore           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posizionamento del viewport


Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata dell'API della console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per spostare il contenuto del buffer della console.

**Attenzione**  I nomi dei comandi sono fuorvianti. Scroll si riferisce alla direzione di spostamento del testo durante l'operazione, non alla modalità di spostamento del viewport.




| Sequenza           | Codice | Descrizione | Comportamento                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; S | Unità di streaming (SU)   | Scorrimento verso l'alto   | Scorrere il testo per &lt; n &gt; . Noto anche come Pan Down, le nuove righe si riempiono dalla parte inferiore dello schermo |
| ESC \[ &lt; n &gt; T | DS   | Scorrimento verso il basso | Scorri verso il basso per &lt; n &gt; . Noto anche come Pan up, le nuove righe vengono inserite nella parte superiore della schermata         |



Il testo viene spostato a partire dalla riga in cui si trova il cursore. Se il cursore si trova nella riga centrale del viewport, scorrere verso l'alto sposta la metà inferiore del viewport e inserisce righe vuote nella parte inferiore. Scorri verso il basso sposta la metà superiore delle righe del viewport e inserisce nuove righe nella parte superiore.

Inoltre, è importante notare che lo scorrimento verso l'alto e verso il basso è influenzato anche dai margini di scorrimento. Lo scorrimento verso l'alto e verso il basso non influirà su alcuna riga al di fuori dei margini di scorrimento.

Il valore predefinito per &lt; n &gt; è 1 e il valore può essere omesso facoltativamente.

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modifica del testo


Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata delle API della console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)e [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per modificare il contenuto del buffer di testo.


| Sequenza           | Codice | Descrizione      | Comportamento                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n&gt; @ | ICH  | Inserisci carattere | Inserisce &lt; n &gt; spazi nella posizione corrente del cursore, spostando tutto il testo esistente a destra. Il testo che esce dalla schermata a destra viene rimosso. |
| ESC \[ &lt; n &gt; P | DCH  | Elimina carattere | Eliminare &lt; n &gt; caratteri nella posizione corrente del cursore, spostando i caratteri di spazio dal bordo destro dello schermo.                       |
| ESC \[ &lt; n &gt; X | ECH  | Carattere di cancellazione  | &lt; &gt; Consente di cancellare n caratteri dalla posizione corrente del cursore sovrascrivendo gli elementi con uno spazio.                                           |
| ESC \[ &lt; n &gt; L | IL   | Inserisci riga      | Inserisce &lt; n &gt; righe nel buffer in corrispondenza della posizione del cursore. La riga in cui si trova il cursore e le linee sotto di essa verranno spostate verso il basso.         |
| ESC \[ &lt; n &gt; M | DL   | Elimina riga      | Elimina &lt; n &gt; righe dal buffer, a partire dalla riga in cui si trova il cursore.                                                                  |



**Nota**  
Per IL e DL, sono interessate solo le righe dei margini di scorrimento (vedere i margini di scorrimento). Se non sono impostati margini, i bordi dei margini predefiniti corrispondono al viewport corrente. Se le righe vengono spostate al di sotto dei margini, vengono scartate. Quando le righe vengono eliminate, le righe vuote vengono inserite nella parte inferiore dei margini, non vengono mai interessate le linee esterne al viewport.

Per ogni sequenza, il valore predefinito di &lt; n &gt; se viene omesso è 0.



Per i comandi seguenti, il parametro &lt; n &gt; presenta 3 valori validi:

- 0 cancella dalla posizione corrente del cursore (inclusivo) alla fine della riga/visualizzazione
- 1 Cancella dall'inizio della riga/visualizza fino alla posizione corrente del cursore e inclusa
- 2 Cancella l'intera riga/visualizzazione


| Sequenza           | Codice | Descrizione      | Comportamento                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; J | ED   | Cancella nella visualizzazione | Sostituisci tutto il testo nel viewport/schermata corrente specificato da &lt; n &gt; con caratteri di spazio |
| ESC \[ &lt; n &gt; K | EL   | Cancella riga    | Sostituisce tutto il testo della riga con il cursore specificato da &lt; n &gt; con caratteri di spazio    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formattazione del testo


Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata delle API della console [**SetConsoleTextAttribute**](setconsoletextattribute.md) per modificare la formattazione di tutte le scritture future nel buffer di testo di output della console.

Questo comando è speciale in quanto la &lt; &gt; Posizione n seguente può accettare tra 0 e 16 parametri separati da punti e virgola.

Quando non viene specificato alcun parametro, questo viene considerato come un singolo parametro 0.


| Sequenza           | Codice | Descrizione            | Comportamento                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt; n &gt; m | SGR  | Imposta rendering grafica | Imposta il formato dello schermo e del testo come specificato da &lt; n&gt; |



La seguente tabella di valori può essere usata in &lt; n &gt; per rappresentare diverse modalità di formattazione.

Le modalità di formattazione vengono applicate da sinistra a destra. Se si applicano opzioni di formattazione in competizione, l'opzione più a destra avrà la precedenza.

Per le opzioni che specificano i colori, i colori verranno usati come definito nella tabella dei colori della console, che può essere modificata tramite l'API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) . Se la tabella viene modificata per fare in modo che la posizione "blu" della tabella visualizzi una sfumatura di rosso RGB, tutte le chiamate al **blu in primo piano** visualizzeranno il colore rosso fino a quando non viene modificato.


| valore | Descrizione               | Comportamento                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| 0     | Predefinito                   | Restituisce tutti gli attributi allo stato predefinito prima della modifica  |
| 1     | Grassetto/chiaro               | Applica il flag di luminosità/intensità al colore di primo piano              |
| 4     | Sottolineato                 | Aggiunge la sottolineatura                                                     |
| 24    | Nessun sottolineatura              | Rimuove la sottolineatura                                                  |
| 7     | Negativo                  | Scambia i colori di primo piano e sfondo                             |
| 27    | Positivo (nessun valore negativo)    | Restituisce il primo piano/sfondo al normale                            |
| 30    | Nero in primo piano          | Applica il nero in primo piano non in grassetto/chiaro                        |
| 31    | Rosso in primo piano            | Applica il colore rosso in primo piano a quello non grassetto/chiaro                          |
| 32    | Verde primo piano          | Applica il verde in primo piano non grassetto/chiaro                        |
| 33    | Giallo in primo piano         | Applica il giallo non grassetto/chiaro a in primo piano                       |
| 34    | Blu in primo piano           | Applica in primo piano non grassetto o blu brillante                         |
| 35    | Magenta in primo piano        | Applica il magenta non grassetto/luminoso a primo piano                      |
| 36    | Ciano in primo piano           | Applica il cyan non grassetto/luminoso a in primo piano                         |
| 37    | Bianco in primo piano          | Applica in primo piano un bianco non grassetto/chiaro                        |
| 38    | Primo piano esteso       | Applica il valore di colore esteso al primo piano (vedere i dettagli di seguito) |
| 39    | Valore predefinito primo piano        | Applica solo la parte in primo piano delle impostazioni predefinite (vedere 0)        |
| 40    | Sfondo nero          | Applica il nero a sfondo non grassetto/chiaro                        |
| 41    | Rosso sfondo            | Applica lo sfondo al rosso non in grassetto/chiaro                          |
| 42    | Verde sfondo          | Applica il verde a sfondo non grassetto/chiaro                        |
| 43    | Sfondo giallo         | Applica lo sfondo al giallo non in grassetto/chiaro                       |
| 44    | Blu sfondo           | Applica lo sfondo al blu non grassetto/luminoso                         |
| 45    | Sfondo Magenta        | Applica il magenta non grassetto/luminoso a sfondo                      |
| 46    | Ciano sfondo           | Applica lo sfondo al ciano non grassetto/luminoso                         |
| 47    | Sfondo bianco          | Applica lo sfondo al bianco non grassetto/chiaro                        |
| 48    | Sfondo esteso       | Applica il valore di colore esteso allo sfondo (vedere i dettagli di seguito) |
| 49    | Impostazione predefinita sfondo        | Applica solo la parte in background delle impostazioni predefinite (vedere 0)        |
| 90    | Lucido nero in primo piano   | Applica grassetto/nero brillante a primo piano                            |
| 91    | Rosso in primo piano     | Applica grassetto/rosso chiaro a primo piano                              |
| 92    | Verde chiaro in primo piano   | Applica grassetto/verde chiaro a primo piano                            |
| 93    | Giallo chiaro in primo piano  | Viene applicato in grassetto/giallo chiaro a primo piano                           |
| 94    | Blu lucido in primo piano    | Applica grassetto/blu chiaro a primo piano                             |
| 95    | Magenta chiaro in primo piano | Applica il magenta in grassetto o luminoso a primo piano                          |
| 96    | Ciano in primo piano    | Applica in primo piano grassetto/chiaro ciano                             |
| 97    | Bianco in primo piano   | Applica in grassetto/chiaro bianco a primo piano                            |
| 100   | Sfondo luminoso nero   | Applica il nero in grassetto/chiaro a sfondo                            |
| 101   | Rosso sfondo chiaro     | Applica lo sfondo al rosso grassetto/chiaro                              |
| 102   | Verde sfondo luminoso   | Applica in grassetto/chiaro verde a sfondo                            |
| 103   | Sfondo luminoso giallo  | Applica in grassetto/giallo chiaro a sfondo                           |
| 104   | Blu sfondo chiaro    | Applica lo sfondo al blu grassetto/chiaro                             |
| 105   | Sfondo chiaro magenta | Applica il magenta in grassetto/chiaro a sfondo                          |
| 106   | Ciano sfondo chiaro    | Applica in grassetto/chiaro ciano a sfondo                             |
| 107   | Bianco sfondo chiaro   | Applica in grassetto/chiaro bianco a sfondo                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colori estesi

Alcuni emulatori di terminali virtuali supportano una tavolozza di colori maggiore dei 16 colori forniti dalla console di Windows. Per questi colori estesi, la console di Windows sceglierà il colore appropriato più vicino dalla tabella 16 colori esistente per la visualizzazione. A differenza dei valori di SGR tipici precedenti, i valori estesi utilizzeranno parametri aggiuntivi dopo l'indicatore iniziale in base alla tabella seguente.


| Sottosequenza SGR                            | Descrizione                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Imposta il colore di primo piano sul valore RGB specificato nei &lt; &gt; parametri r, &lt; g &gt; , &lt; b &gt;\* |
| 48; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | Imposta il colore di sfondo sul valore RGB specificato nei &lt; &gt; parametri r, &lt; g &gt; , &lt; b &gt;\* |
| 38; 5 &lt;s&gt;                         | Imposta il colore di primo piano sull' &lt; &gt; Indice s nella tabella colori 88 o 256\*                          |
| 48; 5 &lt;s&gt;                         | Imposta il colore di sfondo sull' &lt; &gt; Indice s nella tabella colori 88 o 256\*                          |



\*Le tavolozze dei colori 88 e 256 gestite internamente per il confronto sono basate sull'emulatore di terminale xterm. Impossibile modificare le tabelle di confronto o di arrotondamento in questo momento.


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colori dello schermo


Il comando seguente consente all'applicazione di impostare i valori della tavolozza dei colori dello schermo su qualsiasi valore RGB.

I valori RGB devono essere valori esadecimali compresi tra `0` e `ff` e separati dal carattere barra rovesciata (ad esempio `rgb:1/24/86` ).

Si noti che questa sequenza è una sequenza di "comando del sistema operativo" OSC, non un CSI come molte delle altre sequenze elencate e che inizia con " \\ X1B \] ", non con " \\ X1B \[ ".


| Sequenza                                                           | Descrizione          | Comportamento                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC | Modificare i colori della schermata | Imposta l'indice della tavolozza dei colori della schermata sui &lt; &gt; valori RGB specificati in &lt; r &gt; , &lt; g &gt; , &lt; b&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifiche della modalità


Si tratta di sequenze che controllano le modalità di input. Esistono due diversi set di modalità di input, ovvero la modalità dei tasti di cursore e la modalità dei tasti della tastiera. La modalità dei tasti cursore controlla le sequenze generate dai tasti di direzione, nonché da Home e da fine, mentre la modalità tasti di tastiera controlla le sequenze emesse dalle chiavi del tastierino numerico principalmente, nonché i tasti funzione.

Ognuna di queste modalità è una semplice impostazione booleana: la modalità di tasti cursore è normale (impostazione predefinita) o applicazione e la modalità tasti di tastiera è numerica (impostazione predefinita) o applicazione.

Vedere le sezioni tasti di cursore e tastierino numerico & tasti funzione per le sequenze emesse in queste modalità.


| Sequenza     | Codice    | Descrizione                                            | Comportamento                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC =        | DECKPAM | Abilitare la modalità applicazione del tastierino                         | I tasti del tastierino emetteranno le relative sequenze in modalità applicazione. |
| ESC &gt;     | DECKPNM | Abilita modalità numerica tastierino                             | I tasti della tastiera emetteranno le sequenze in modalità numerica.     |
| ESC \[ ? 1 ora | DECCKM  | Abilitare la modalità di applicazione delle chiavi del cursore                    | I tasti del tastierino emetteranno le relative sequenze in modalità applicazione. |
| ESC \[ ? 1 l | DECCKM  | Disabilitare la modalità di applicazione delle chiavi del cursore (usare la modalità normale) | I tasti della tastiera emetteranno le sequenze in modalità numerica.     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Stato query


Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata di Get \* console API per recuperare informazioni sullo stato corrente del buffer della console.

**Nota**  Queste query emetteranno le risposte nel flusso di input della console immediatamente dopo essere state riconosciute nel flusso di output mentre è stata ABILITAta l' \_ \_ elaborazione del terminale virtuale \_ . Il \_ flag Enable virtual \_ Terminal input non \_ si applica ai comandi di query perché si presuppone che un'applicazione che esegue la query desideri ricevere sempre la risposta.




| Sequenza   | Codice    | Descrizione            | Comportamento                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | Posizione del cursore del report | Creare la posizione del cursore come: ESC \[ &lt; r &gt; ; &lt; c &gt; r dove &lt; R &gt; = riga cursore e &lt; c &gt; = colonna cursore |
| ESC \[ 0 c | DA      | Attributi del dispositivo      | Segnala l'identità del terminale. Emetterà " \\ X1B \[ ? 1; 0C", che indica "VT101 senza opzioni".                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Schede


Sebbene la console di Windows usi tradizionalmente le schede in modo da avere una larghezza esclusiva di otto caratteri, le \* applicazioni nix che usano determinate sequenze possono modificare il punto in cui si trovano le tabulazioni all'interno delle finestre della console per ottimizzare lo spostamento del cursore da parte dell'applicazione.

Le sequenze seguenti consentono a un'applicazione di impostare i percorsi di tabulazione nella finestra della console, rimuoverli e spostarsi tra di essi.


| Sequenza           | Codice | Descrizione                     | Comportamento                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H              | HTS  | Set di schede orizzontali              | Imposta un punto di tabulazione nella colonna corrente in cui si trova il cursore.                                                                                                                                                                     |
| ESC \[ &lt; n &gt; I | CHT  | Scheda cursore orizzontale (in poi) | Spostare il cursore sulla colonna successiva (nella stessa riga) con una tabulazione. Se non sono presenti altre tabulazioni, passare all'ultima colonna della riga. Se il cursore si trova nell'ultima colonna, passare alla prima colonna della riga successiva. |
| ESC \[ &lt; n &gt; Z | CBT  | Scheda cursore indietro            | Spostare il cursore sulla colonna precedente (nella stessa riga) con una tabulazione. Se non sono presenti altre tabulazioni, sposta il cursore sulla prima colonna. Se il cursore si trova nella prima colonna, il cursore non viene spostato.              |
| ESC \[ 0 g         | TBC  | Tabulazione cancellata (colonna corrente)      | Cancella la tabulazione nella colonna corrente, se presente. In caso contrario, non esegue alcuna operazione.                                                                                                                                         |
| ESC \[ 3 g         | TBC  | Cancellazione tabulazione (tutte le colonne)         | Cancella tutte le tabulazioni attualmente impostate.                                                                                                                                                                                         |



- Per CHT e CBT, &lt; n &gt; è un parametro facoltativo che (valore predefinito = 1) indica il numero di volte in cui avanzare il cursore nella direzione specificata.
- Se non sono presenti interruzioni di tabulazioni impostate tramite HTS, CHT e CBT tratteranno la prima e l'ultima colonna della finestra come le uniche due schede arrestate.
- Se si usa HTS per impostare una tabulazione, la console passa alla successiva tabulazione nell'output di un carattere di TABULAzione (0x09, " \\ t"), nello stesso modo in cui si configura cht.

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designare il set di caratteri


Le sequenze seguenti consentono a un programma di modificare il mapping del set di caratteri attivo. In questo modo un programma può emettere caratteri ASCII a 7 bit, ma è possibile visualizzarli come altri glifi nella schermata finale. Attualmente, gli unici due set di caratteri supportati sono ASCII (impostazione predefinita) e il set di caratteri grafici DEC Special. <http://vt100.net/docs/vt220-rm/table2-4.html>Per un elenco di tutti i caratteri rappresentati dal set di caratteri grafici Dec speciale, vedere.


| Sequenza | Descrizione                                | Comportamento                      |
|----------|--------------------------------------------|-------------------------------|
| ESC (0  | Designare il set di caratteri – disegno linea DEC | Abilita la modalità di disegno linea DEC |
| ESC (B  | Designare set di caratteri – US ASCII         | Abilita la modalità ASCII (impostazione predefinita)  |



In particolare, la modalità di disegno linea DEC viene utilizzata per disegnare i bordi nelle applicazioni console. Nella tabella seguente viene illustrato il mapping di caratteri ASCII a cui è associato il carattere di disegno a linee.


| Hex  | ASCII | Disegno linea DEC |
|------|-------|------------------|
| 0x6A | j     | ┘                |
| 0x6b | k     | ┐                |
| 0x6C | l     | ┌                |
| 0x6d | m     | └                |
| 0x6e | n     | ┼                |
| 0x71 | q     | ─                |
| 0x74 | t     | ├                |
| 0x75 | u     | ┤                |
| 0x76 | v     | ┴                |
| 0x77 | w     | ┬                |
| 0x78 | x     | │                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scorrimento di margini


Le sequenze seguenti consentono a un programma di configurare la "regione di scorrimento" della schermata interessata dalle operazioni di scorrimento. Si tratta di un subset delle righe che vengono modificate quando lo scorrimento dello schermo viene eseguito, ad esempio, in un' \\ n'o un ri. Questi margini influiscono anche sulle righe modificate da Inserisci riga (IL) e Elimina riga (DL), scorri verso l'alto (SU) e scorri verso il basso (SD).

I margini di scorrimento possono essere particolarmente utili per avere una parte dello schermo che non scorre quando il resto dello schermo viene riempito, ad esempio con una barra del titolo nella parte superiore o una barra di stato nella parte inferiore dell'applicazione.

Per DECSTBM sono disponibili due parametri facoltativi, &lt; t &gt; e &lt; b &gt; , che vengono usati per specificare le righe che rappresentano le righe superiore e inferiore dell'area di scorrimento, incluse. Se i parametri vengono omessi, per impostazione predefinita viene impostato su &lt; &gt; 1 e &lt; b &gt; l'altezza del viewport corrente.

I margini di scorrimento sono per buffer, quindi è importante che il buffer alternativo e il buffer principale gestiscano le impostazioni dei margini di scorrimento separati (pertanto un'applicazione a schermo intero nel buffer alternativo non avvelena i margini del buffer principale).


| Sequenza                       | Codice    | Descrizione          | Comportamento                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt; t &gt; ; &lt; b &gt; r | DECSTBM | Imposta area di scorrimento | Imposta i margini di scorrimento del VT del viewport. |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titolo della finestra


I comandi seguenti consentono all'applicazione di impostare il titolo della finestra della console sul parametro di &lt; stringa specificato &gt; . Per essere accettata, la stringa deve contenere meno di 255 caratteri. Equivale a chiamare SetConsoleTitle con la stringa specificata.

Si noti che queste sequenze sono "Command del sistema operativo" e non un CSI come molte delle altre sequenze elencate e che inizia con " \\ X1B \] ", non con " \\ X1B \[ ".


| Sequenza                      | Descrizione               | Comportamento                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0; &lt; stringa &gt; bel | Imposta icona e titolo finestra | Imposta il titolo della finestra della console su &lt; stringa &gt; . |
| ESC \] 2; &lt; stringa &gt; bel | Imposta titolo finestra          | Imposta il titolo della finestra della console su &lt; stringa &gt; . |



Il carattere di terminazione qui è il carattere "campanello", " \\ x07"

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Buffer dello schermo alternativo


\*Le applicazioni in stile nix spesso utilizzano un buffer dello schermo alternativo, in modo che possano modificare l'intero contenuto del buffer, senza influire sull'applicazione che l'ha avviata. Il buffer alternativo è esattamente le dimensioni della finestra, senza alcuna area scrollback.

Per un esempio di questo comportamento, si prenda in considerazione quando VIM viene avviato da bash. Vim usa l'intero schermo per modificare il file e quindi il ritorno a bash lascia invariato il buffer originale.


| Sequenza           | Descrizione                 | Comportamento                                   |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | Usa buffer schermato alternativo | Passa a un nuovo buffer dello schermo alternativo. |
| ESC \[ ? 1 0 4 9 l | Usa buffer dello schermo principale      | Passa al buffer principale.               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Larghezza finestra


Le sequenze seguenti possono essere utilizzate per controllare la larghezza della finestra della console. Sono approssimativamente equivalenti al chiamante dell'API della console SetConsoleScreenBufferInfoEx per impostare la larghezza della finestra.


| Sequenza     | Codice    | Descrizione                  | Comportamento                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 ore | DECCOLM | Imposta il numero di colonne su 132 | Imposta la larghezza della console su una larghezza di 132 colonne. |
| ESC \[ ? 3 l | DECCOLM | Imposta il numero di colonne su 80  | Imposta la larghezza della console su una larghezza di 80 colonne.  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Ripristino soft


La sequenza seguente può essere utilizzata per reimpostare i valori predefiniti di determinate proprietà. Le proprietà seguenti vengono reimpostate sui valori predefiniti seguenti (sono elencate anche le sequenze che controllano tali proprietà):

- Visibilità cursore: visibile (DECTEM)
- Tastierino numerico: modalità numerica (DECNKM)
- Modalità tasti di cursore: modalità normale (DECCKM)
- Margini superiore e inferiore: superiore = 1, inferiore = altezza Console (DECSTBM)
- Set di caratteri: US ASCII
- Rendering della grafica: default/off (SGR)
- Salva stato cursore: posizione Home (0,0) (DECSC)


| Sequenza   | Codice   | Descrizione | Comportamento                                           |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | Ripristino soft  | Ripristinare le impostazioni predefinite di determinate impostazioni del terminale. |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Sequenze di input


Le sequenze di terminali seguenti vengono emesse dall'host della console nel flusso di input se il flag di ABILITAzione del \_ terminale virtuale di input \_ \_ viene impostato sull'handle del buffer di input usando il flag SetConsoleMode.

Sono disponibili due modalità interne che controllano le sequenze emesse per le chiavi di input specificate, la modalità dei tasti di cursore e la modalità dei tasti della tastiera. Questi sono descritti nella sezione modifiche della modalità.

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Tasti di cursore


| Chiave         | Modalità normale | Modalità applicazione |
|-------------|-------------|------------------|
| Freccia SU    | ESC \[ A    | ESC O A          |
| Freccia GIÙ  | ESC \[ B    | ESC O B          |
| Freccia DESTRA | ESC \[ C    | ESC O C          |
| Freccia SINISTRA  | ESC \[ D    | ESC O D          |
| Home page        | ESC \[ H    | ESC O H          |
| Fine         | ESC \[ F    | ESC O F          |



Inoltre, se si preme CTRL con una qualsiasi di queste chiavi, vengono generate le sequenze seguenti, indipendentemente dalla modalità dei tasti di cursore:


| Chiave                | Qualsiasi modalità       |
|--------------------|----------------|
| CTRL + freccia su    | ESC \[ 1; 5 A |
| CTRL + freccia giù  | ESC \[ 1; 5 B |
| CTRL + freccia destra | ESC \[ 1; 5 C |
| CTRL + freccia sinistra  | ESC \[ 1; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Tastierino numerico & tasti funzione


| Chiave       | Sequenza     |
|-----------|--------------|
| Backspace | 0x7F (CANC)   |
| Sospendi     | 0x1A (SUB)   |
| Carattere speciale di escape    | 0x1B (ESC)   |
| Insert    | ESC \[ 2 ~   |
| Elimina    | ESC \[ 3 ~   |
| PGSU   | ESC \[ 5 ~   |
| PGGIÙ | ESC \[ 6 ~   |
| F1        | ESC O P      |
| F2        | ESC O Q      |
| F3        | ESC O R      |
| F4        | ESC O S      |
| F5        | ESC \[ 1 5 ~ |
| F6        | ESC \[ 1 7 ~ |
| F7        | ESC \[ 1 8 ~ |
| F8        | ESC \[ 1 9 ~ |
| F9        | ESC \[ 2 0 ~ |
| F10       | ESC \[ 2 1 ~ |
| F11       | ESC \[ 2 3 ~ |
| F12       | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificatori

ALT viene trattato anteponendo la sequenza con un carattere di escape: ESC &lt; c &gt; dove &lt; c &gt; è il carattere passato dal sistema operativo. ALT + CTRL viene gestito allo stesso modo, ad eccezione del fatto che il sistema operativo avrà già spostato &lt; il &gt; tasto c sul carattere di controllo appropriato che verrà inoltrato all'applicazione.

La combinazione di tasti CTRL viene in genere passata esattamente come ricevuta dal sistema. Si tratta in genere di un singolo carattere spostato nello spazio riservato dei caratteri di controllo (0x0-0x1F). Ad esempio, Ctrl + @ (0x40) diventa NUL (0x00), CTRL + \[ (0x5b) diventa ESC (0x1B) e così via. Alcune combinazioni di tasti CTRL vengono trattate in modo speciale in base alla tabella seguente:


| Chiave                | Sequenza       |
|--------------------|----------------|
| CTRL+BARRA SPAZIATRICE       | 0x00 (NUL)     |
| CTRL + freccia su    | ESC \[ 1; 5 A |
| CTRL + freccia giù  | ESC \[ 1; 5 B |
| CTRL + freccia destra | ESC \[ 1; 5 C |
| CTRL + freccia sinistra  | ESC \[ 1; 5 D |



**Nota**  Il tasto CTRL + freccia destra viene considerato come AltGr. Quando entrambi gli elementi vengono visualizzati insieme, verranno rimossi e il valore Unicode del carattere presentato dal sistema verrà passato nella destinazione. Il sistema effettuerà la pre-conversione dei valori di AltGr in base alle impostazioni di input di sistema correnti.



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Campioni


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>Esempio di sequenze di terminali SGR

Nel codice riportato di seguito vengono forniti alcuni esempi di formattazione del testo.

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

**Nota**  Nell'esempio precedente, la stringa ' `\x1b[31m` ' è l'implementazione di **ESC \[ &lt; n &gt; m** con &lt; n &gt; è 31.



Il grafico seguente mostra l'output dell'esempio di codice precedente.

![output della console con il comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Esempio di abilitazione dell'elaborazione di terminali virtuali

Il codice seguente fornisce un esempio della modalità consigliata per abilitare l'elaborazione di terminali virtuali per un'applicazione. Lo scopo dell'esempio è illustrare:

1. La modalità esistente deve sempre essere recuperata tramite GetConsoleMode e analizzata prima di essere impostata con SetConsoleMode.

2. Il controllo della restituzione `0` di SetConsoleMode e di GetLastError restituisce uno stato \_ non valido \_ del parametro è il meccanismo corrente per determinare quando viene eseguito in un sistema di livello inferiore. Un parametro dell'applicazione che riceve lo stato \_ non valido \_ con uno dei flag della modalità console più recenti nel campo di bit dovrebbe ridurre normalmente il comportamento e riprovare.

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Esempio di funzionalità di aggiornamento dell'anniversario selezionato

L'esempio seguente è destinato a essere un esempio più affidabile di codice che usa una serie di sequenze di escape per modificare il buffer, con particolare attenzione alle funzionalità aggiunte nell'aggiornamento dell'anniversario per Windows 10.

Questo esempio usa il buffer dello schermo alternativo, la modifica delle tabulazioni, l'impostazione dei margini di scorrimento e la modifica del set di caratteri.

```C
//
//    Copyright (C) Microsoft.  All rights reserved.
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
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");   // bright yellow on bright blue
    printf("x");            // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m");       // restore color
    printf(ESC "(B");       // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");  // Make the border bright yellow on bright blue
    printf(fIsTop? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++) 
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B");       // exit line drawing mode
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
    Size.Y = ScreenBufferInfo.srWindow.Bottom -  ScreenBufferInfo.srWindow.Top + 1;

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








