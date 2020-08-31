---
title: Modalità console di alto livello
description: Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059628"
---
# <a name="high-level-console-modes"></a>Modalità console di alto livello


Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console. Tutte le modalità di input della console seguenti sono abilitate per il buffer di input di una console quando viene creata una console:

- Modalità input linea
- Modalità di input elaborata
- Modalità input echo

Entrambe le modalità di output della console seguenti sono abilitate per un buffer dello schermo della console quando viene creato:

- Modalità output elaborata
- Wrapping in modalità di output EOL

Tutte e tre le modalità di input, insieme alla modalità output elaborata, sono progettate per essere utilizzate insieme. È consigliabile abilitare o disabilitare tutte queste modalità come gruppo. Quando tutti sono abilitati, l'applicazione viene definita in modalità "cotta", il che significa che la maggior parte dell'elaborazione viene gestita per l'applicazione. Quando tutti sono disabilitati, l'applicazione è in modalità "Raw", il che significa che l'input non viene filtrato e l'elaborazione viene lasciata all'applicazione.

Un'applicazione può usare la funzione [**GetConsoleMode**](getconsolemode.md) per determinare la modalità corrente del buffer di input o dello schermo di una console. È possibile abilitare o disabilitare una qualsiasi di queste modalità usando i valori seguenti nella funzione [**SetConsoleMode**](setconsolemode.md) . Si noti che l'impostazione della modalità di output di un buffer dello schermo non influisce sulla modalità di output di altri buffer dello schermo.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mode</th>
<th>Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>Viene usato con un handle di input della console per fare in modo che il sistema elabori l'input della chiave di modifica o di controllo del sistema anziché restituirlo come input nel buffer dell'operazione di lettura&#39;s. Se è abilitato anche l'input di riga, gli spazi e i ritorni a capo vengono gestiti correttamente. Un backspace determina lo spostamento del cursore indietro di uno spazio senza influire sul carattere in corrispondenza della posizione del cursore. Un ritorno a capo viene convertito in una combinazione di caratteri di ritorno a capo-avanzamento riga. Se la modalità di input echo è abilitata e l'output deve riflettere la modifica del sistema, l'output elaborato deve essere abilitato per il buffer dello schermo attivo. Se l'input elaborato è abilitato, la combinazione di tasti CTRL + C viene passata al gestore appropriato, indipendentemente dal fatto che sia abilitato l'input della riga. Per altre informazioni sui gestori di controllo, vedere <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">gestori di controlli della console</a>.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>Usato con un handle di input della console per fare in modo che le funzioni <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> e <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> restituiscano quando viene premuto il tasto INVIO. Se la modalità di input della riga è disabilitata, le funzioni restituiscono quando uno o più caratteri sono disponibili nel buffer di input.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>Usato con un handle di input della console per fare in modo che l'input della tastiera letto dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> venga restituito al buffer dello schermo attivo. I caratteri vengono restituiti solo se il processo che chiama <strong>ReadFile</strong> o <strong>ReadConsole</strong> dispone di un handle aperto per il buffer dello schermo attivo. Non è possibile abilitare la modalità Echo a meno che non sia abilitata anche l'input della riga. La modalità di output del buffer dello schermo attivo influiscono sul modo in cui viene visualizzato l'input eco.</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>Utilizzato con un handle del buffer dello schermo della console per fare in modo che il sistema esegua l'azione appropriata per i caratteri di controllo ANSI scritti in un buffer dello schermo. I caratteri di ritorno a capo, tabulazione, campana, ritorno a capo e avanzamento riga vengono elaborati. Un carattere di tabulazione sposta il cursore alla successiva tabulazione, che si verifica ogni otto caratteri. Un carattere a campana emette un tono breve.</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>Utilizzato con un handle del buffer dello schermo della console per fare in modo che la posizione di output corrente (posizione del cursore) si sposti sulla prima colonna nella riga successiva (riga) quando viene raggiunta la fine della riga corrente. Se viene raggiunta la parte inferiore dell'area della finestra, l'origine della finestra viene spostata verso il basso di una riga. Questo movimento ha l'effetto di scorrere il contenuto della finestra verso l'alto di una riga. Se viene raggiunta la fine del buffer dello schermo della console, il contenuto del buffer dello schermo della console viene spostato verso l'alto di una riga e la riga superiore del buffer dello schermo della console viene eliminata.
<p>Se questa modalità è disabilitata, l'ultimo carattere della riga viene sovrascritto con i caratteri successivi.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




