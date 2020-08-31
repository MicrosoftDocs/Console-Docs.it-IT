---
title: GetConsoleMode (funzione)
description: Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a2d18ed191d1d82cc54c3277aa38badb0aedb630
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059740"
---
# <a name="getconsolemode-function"></a>GetConsoleMode (funzione)


Recupera la modalità di input corrente del buffer di input di una console o la modalità di output corrente di un buffer dello schermo della console.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleHandle* \[ in\]  
Handle per il buffer di input della console o il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpMode* \[ out\]  
Puntatore a una variabile che riceve la modalità corrente del buffer specificato.

Se il parametro *hConsoleHandle* è un handle di input, la modalità può essere costituita da uno o più dei valori seguenti. Quando viene creata una console, tutte le modalità di input eccetto **Abilita \_ \_ input finestra** sono abilitate per impostazione predefinita.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</td>
<td><p>I caratteri letti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> vengono scritti nel buffer dello schermo attivo mentre vengono letti. Questa modalità può essere utilizzata solo se è abilitata anche la modalità <strong>ENABLE_LINE_INPUT</strong> .</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</td>
<td><p>Se abilitata, il testo immesso in una finestra della console verrà inserito nella posizione corrente del cursore e tutto il testo successivo a tale percorso non verrà sovrascritto. Se disabilitato, tutto il testo seguente verrà sovrascritto.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</td>
<td><p>La funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> restituisce solo quando viene letto un carattere di ritorno a capo. Se questa modalità è disabilitata, le funzioni restituiscono quando sono disponibili uno o più caratteri.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</td>
<td><p>Se il puntatore del mouse si trova all'interno dei bordi della finestra della console e la finestra ha lo stato attivo della tastiera, gli eventi del mouse generati dal movimento del mouse e dalle pressioni dei pulsanti vengono inseriti nel buffer di input. Questi eventi vengono eliminati da <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, anche quando questa modalità è abilitata.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</td>
<td><p>CTRL + C viene elaborato dal sistema e non viene inserito nel buffer di input. Se il buffer di input viene letto da <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, altre chiavi di controllo vengono elaborate dal sistema e non vengono restituite nel buffer <strong>ReadFile</strong> o <strong>ReadConsole</strong> . Se è abilitata anche la modalità <strong>ENABLE_LINE_INPUT</strong> , i caratteri backspace, ritorno a capo e avanzamento riga vengono gestiti dal sistema.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</td>
<td><p>Questo flag consente all'utente di usare il mouse per selezionare e modificare il testo.</p>
<p>Per abilitare questa modalità, utilizzare <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> . Per disabilitare questa modalità, utilizzare <strong>ENABLE_EXTENDED_FLAGS</strong> senza questo flag.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</td>
<td><p>Le interazioni utente che modificano le dimensioni del buffer dello schermo della console sono segnalate nel buffer di input della console&#39;s. Le informazioni su questi eventi possono essere lette dal buffer di input dalle applicazioni che usano la funzione <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , ma non da quelle che usano <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</td>
<td><p>Impostando questo flag, il motore di elaborazione dei terminali virtuali viene indirizzato alla conversione dell'input utente ricevuto dalla finestra della console in <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">sequenze di terminali virtuali della console</a> che possono essere recuperate da un'applicazione di supporto tramite le funzioni <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> .</p>
<p>L'utilizzo tipico di questo flag è concepito insieme a ENABLE_VIRTUAL_TERMINAL_PROCESSING nell'handle di output per connettersi a un'applicazione che comunica esclusivamente tramite sequenze di terminali virtuali.</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

Se il parametro *hConsoleHandle* è un handle del buffer dello schermo, la modalità può essere costituita da uno o più dei valori seguenti. Quando viene creato un buffer dello schermo, entrambe le modalità di output sono abilitate per impostazione predefinita.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</td>
<td><p>I caratteri scritti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o restituiti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> vengono analizzati per le sequenze di controlli ASCII e viene eseguita l'azione corretta. Vengono elaborati i caratteri di ritorno a capo, tabulazione, ritorno a capo e avanzamento riga.</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</td>
<td><p>Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o si esegue l'eco con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, il cursore si sposta all'inizio della riga successiva quando raggiunge la fine della riga corrente. In questo modo, le righe visualizzate nella finestra della console scorrono automaticamente quando il cursore avanza oltre l'ultima riga nella finestra. Consente inoltre di scorrere verso l'alto il contenuto del buffer dello schermo della console (eliminando la prima riga del buffer dello schermo della console) quando il cursore avanza oltre l'ultima riga nel buffer dello schermo della console. Se questa modalità è disabilitata, l'ultimo carattere della riga viene sovrascritto con i caratteri successivi.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</td>
<td><p>Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, i caratteri vengono analizzati per VT100 e sequenze di caratteri di controllo simili che controllano lo spostamento del cursore, la modalità colore/carattere e altre operazioni che possono essere eseguite anche tramite le API della console esistenti. Per altre informazioni, vedere <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">sequenze di terminali virtuali della console</a>.</p></td>
</tr>
<tr class="even">
<td><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</td>
<td><p>Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, viene aggiunto uno stato aggiuntivo al wrapping di fine riga che può ritardare le operazioni di spostamento del cursore e scorrimento del buffer.</p>
<p>In genere, quando ENABLE_WRAP_AT_EOL_OUTPUT è impostato e il testo raggiunge la fine della riga, il cursore si sposta immediatamente alla riga successiva e il contenuto del buffer scorre verso l'alto di una riga. Diversamente da questo set di flag, l'operazione di scorrimento e lo spostamento del cursore vengono posticipati fino all'arrivo del carattere successivo. Il carattere scritto verrà stampato nella posizione finale sulla riga e il cursore rimarrà al di sopra di questo carattere come se ENABLE_WRAP_AT_EOL_OUTPUT fosse disattivato, ma il successivo carattere stampabile verrà stampato come se ENABLE_WRAP_AT_EOL_OUTPUT fosse attivo. Non si verificherà alcuna sovrascrittura. In particolare, il cursore avanza rapidamente fino alla riga seguente, viene eseguito uno scorrimento, se necessario, il carattere viene stampato e il cursore avanza di una posizione.</p>
<p>L'utilizzo tipico di questo flag è concepito insieme all'impostazione ENABLE_VIRTUAL_TERMINAL_PROCESSING per emulare meglio un emulatore di terminale in cui la scrittura del carattere finale sullo schermo (nell'angolo inferiore destro) senza attivare uno scorrimento immediato è il comportamento desiderato.</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</td>
<td><p>Le API per la scrittura di attributi di caratteri, tra cui <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> e <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , consentono di utilizzare flag di <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">attributi di caratteri</a> per modificare il colore del primo piano e dello sfondo del testo. È stato inoltre specificato un intervallo di flag DBCS con il prefisso COMMON_LVB. In passato, questi flag funzionavano solo nelle tabelle codici DBCS per le lingue cinese, giapponese e coreano.</p>
<p>Con l'eccezione dei flag di byte iniziali e finali, i flag rimanenti che descrivono il disegno a linee e i video inversi (scambio di primo piano e colori di sfondo) possono essere utili per altri linguaggi per enfatizzare porzioni di output.</p>
<p>L'impostazione di questo flag della modalità console consentirà l'utilizzo di questi attributi in ogni tabella codici in ogni lingua.</p>
<p>È disattivata per impostazione predefinita per garantire la compatibilità con le applicazioni note che hanno utilizzato in passato la console ignorando questi flag sui computer non CJK per archiviare i bit in questi campi per loro scopi o per errore.</p>
<p>Si noti che l'uso della modalità di ENABLE_VIRTUAL_TERMINAL_PROCESSING può comportare l'impostazione di LVB Grid e dei flag video inversi mentre questo flag è disattivato se l'applicazione collegata richiede la sottolineatura o il video inverso tramite le <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">sequenze di terminali virtuali della console</a>.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Una console di è costituita da un buffer di input e uno o più buffer dello schermo. La modalità di un buffer della console determina il comportamento della console durante le operazioni di input o output (I/O). Un set di costanti flag viene usato con gli handle di input e un altro set viene usato con gli handle del buffer dello schermo (output). L'impostazione delle modalità di output di un buffer dello schermo non influisce sulle modalità di output di altri buffer dello schermo.

Le **modalità \_ Abilita \_ input riga** e **Abilita \_ \_ input echo** influiscono solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) per la lettura dal buffer di input della console. Analogamente, l'abilitazione della modalità di ** \_ \_ input elaborata** interessa principalmente gli utenti **ReadFile** e **ReadConsole** , con la differenza che determina anche se l'input di CTRL + C viene segnalato nel buffer di input (per la lettura da parte della funzione [**ReadConsoleInput**](readconsoleinput.md) ) o viene passato a una funzione definita dall'applicazione.

Le **modalità \_ Abilita \_ input finestra** e **Abilita \_ \_ input mouse** determinano se le interazioni utente che coinvolgono il ridimensionamento delle finestre e le azioni del mouse vengono segnalate nel buffer di input o eliminate. Questi eventi possono essere letti da [**ReadConsoleInput**](readconsoleinput.md), ma vengono sempre filtrati in base a [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](readconsole.md).

L' **Abilitazione dell' \_ \_ output elaborato** e l' **Abilitazione del \_ wrapping \_ in modalità di \_ \_ output EOL** hanno effetto solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md).

Per modificare le modalità I/O di una console, chiamare la funzione [**SetConsoleMode**](setconsolemode.md) .

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

<a name="requirements"></a>Requisiti
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimo supportato</p></td>
<td><p>Windows 2000 Professional [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows 2000 Server [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ConsoleApi. h (tramite wincon. h, Includi Windows. h)</td>
</tr>
<tr class="even">
<td><p>Libreria</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[Funzioni console](console-functions.md)

[Modalità console](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




