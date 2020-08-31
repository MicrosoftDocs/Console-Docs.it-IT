---
title: Funzione di callback HandlerRoutine
description: Funzione definita dall'applicazione utilizzata con la funzione SetConsoleCtrlHandler. Un processo della console usa questa funzione per gestire i segnali di controllo ricevuti dal processo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/HandlerRoutine
- wincon/HandlerRoutine
- HandlerRoutine
MS-HAID:
- '\_win32\_handlerroutine'
- base.handlerroutine
- consoles.handlerroutine
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2e8732fa-7dfd-415b-b2fc-c27a400496f2
topic_type:
- apiref
api_name:
- HandlerRoutine
api_location:
- Wincon.h
api_type:
- UserDefined
ms.openlocfilehash: 14205baaddd98c8c22881c5f448119412e1f4a1c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060124"
---
# <a name="handlerroutine-callback-function"></a>Funzione di callback HandlerRoutine


Funzione definita dall'applicazione utilizzata con la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Un processo della console usa questa funzione per gestire i segnali di controllo ricevuti dal processo. Quando viene ricevuto il segnale, il sistema crea un nuovo thread nel processo per eseguire la funzione.

Il tipo di ** \_ routine PHANDLER** definisce un puntatore a questa funzione di callback. **HandlerRoutine** è un segnaposto per il nome della funzione definita dall'applicazione.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

<a name="parameters"></a>Parametri
----------

*dwCtrlType* \[ in\]  
Tipo di segnale di controllo ricevuto dal gestore. Questo parametro può essere uno dei valori seguenti.

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
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>È stato ricevuto un segnale CTRL + C, dall'input da tastiera o da un segnale generato dalla funzione <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a> .</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>È stato ricevuto un segnale CTRL + BREAK, dall'input da tastiera o da un segnale generato da <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_CLOSE_EVENT"></span><span id="ctrl_close_event"></span>
<strong>CTRL_CLOSE_EVENT</strong> 2</td>
<td><p>Un segnale inviato dal sistema a tutti i processi collegati a una console quando l'utente chiude la console (facendo clic su <strong>Chiudi</strong> nel menu della finestra della console&#39;s o facendo clic sul pulsante <strong>Termina attività</strong> da Gestione attività).</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_LOGOFF_EVENT"></span><span id="ctrl_logoff_event"></span>
<strong>CTRL_LOGOFF_EVENT</strong> 5</td>
<td><p>Segnale inviato dal sistema a tutti i processi della console quando un utente esegue la disconnessione. Questo segnale non indica quale utente sta effettuando la disconnessione, pertanto non è possibile effettuare supposizioni.</p>
<p>Si noti che questo segnale viene ricevuto solo dai servizi. Le applicazioni interattive vengono terminate alla disconnessione, quindi non sono presenti quando il sistema invia questo segnale.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_SHUTDOWN_EVENT"></span><span id="ctrl_shutdown_event"></span>
<strong>CTRL_SHUTDOWN_EVENT</strong> 6</td>
<td><p>Segnale inviato dal sistema alla chiusura del sistema. Le applicazioni interattive non sono presenti nel momento in cui il sistema invia questo segnale, pertanto può essere ricevuto solo da servizi in questa situazione. I servizi hanno anche un proprio meccanismo di notifica per gli eventi di arresto. Per ulteriori informazioni, vedere <a href="https://msdn.microsoft.com/library/windows/desktop/ms683240" data-raw-source="[&lt;strong&gt;Handler&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/ms683240)"><strong>handler</strong></a>.</p>
<p>Questo segnale può essere generato anche da un'applicazione che usa <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>GenerateConsoleCtrlEvent</strong></a>.</p></td>
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

Se la funzione gestisce il segnale di controllo, deve restituire **true**. Se restituisce **false**, viene utilizzata la funzione del gestore successiva nell'elenco dei gestori per questo processo.

<a name="remarks"></a>Osservazioni
-------

Poiché il sistema crea un nuovo thread nel processo per eseguire la funzione del gestore, è possibile che la funzione del gestore venga terminata da un altro thread nel processo. Assicurarsi di sincronizzare i thread del processo con il thread per la funzione del gestore.

Ogni processo della console dispone di un proprio elenco di funzioni **HandlerRoutine** . Inizialmente, questo elenco contiene solo una funzione di gestione predefinita che chiama [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658). Un processo console consente di aggiungere o rimuovere funzioni aggiuntive del gestore chiamando la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) , che non influisce sull'elenco di funzioni del gestore per altri processi. Quando un processo della console riceve uno dei segnali di controllo, le relative funzioni di gestione vengono chiamate in base a un'ultima chiamata registrata prima che uno dei gestori restituisca **true**. Se nessuno dei gestori restituisce **true**, viene chiamato il gestore predefinito.

L' ** \_ \_ evento CTRL Close**, **l' \_ \_ evento di disconnessione CTRL**e i segnali ** \_ \_ evento di chiusura CTRL** consentono al processo di eseguire la pulizia prima della terminazione. Un **HandlerRoutine** può eseguire tutte le operazioni di pulizia necessarie, quindi eseguire una delle operazioni seguenti:

- Chiamare la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) per terminare il processo.
- Restituisce **false**. Se nessuna delle funzioni del gestore registrate restituisce **true**, il gestore predefinito termina il processo.
- Restituisce **true**. In questo caso, non vengono chiamate altre funzioni del gestore e il sistema termina il processo.

Un processo può utilizzare la funzione [**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) per impedire al sistema di visualizzare una finestra di dialogo all'utente durante la disconnessione o l'arresto. In questo caso, il sistema termina il processo quando **HandlerRoutine** restituisce **true** o quando scade il periodo di timeout.

Quando un'applicazione console viene eseguita come servizio, riceve un gestore di controllo della console predefinito modificato. Questo gestore modificato non chiama [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) durante l'elaborazione dell' ** \_ \_ evento di disconnessione CTRL** e dei segnali di **chiusura dell' \_ \_ evento CTRL** . Ciò consente al servizio di continuare l'esecuzione dopo che l'utente si disconnette. Se il servizio installa il proprio gestore di controllo della console, questo gestore viene chiamato prima del gestore predefinito. Se il gestore installato chiama **ExitProcess** durante l'elaborazione del segnale dell' ** \_ \_ evento di disconnessione CTRL** , il servizio viene chiuso quando l'utente si disconnette.

Si noti che una libreria o una DLL di terze parti può installare un gestore di controllo della console per l'applicazione. In caso contrario, questo gestore esegue l'override del gestore predefinito e può causare la chiusura dell'applicazione quando l'utente si disconnette.

## <a name="timeouts"></a>Timeout

| Event                  | Circostanze                   | Timeout                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _qualsiasi_                           | parametro `SPI_GETHUNGAPPTIMEOUT` di sistema, 5000 ms            |
| `CTRL_LOGOFF_EVENT`    | _rapido_[1] | chiave del registro di sistema `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _nessuno dei precedenti_             | parametro `SPI_GETWAITTOKILLTIMEOUT` di sistema, 5000 ms         |
| `CTRL_SHUTDOWN_EVENT`  | **processo del servizio**             | parametro `SPI_GETWAITTOKILLSERVICETIMEOUT` di sistema, 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _rapido_[1] | chiave del registro di sistema `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _nessuno dei precedenti_             | parametro `SPI_GETWAITTOKILLTIMEOUT` di sistema, 5000 ms         |
| `CTRL_C`, `CTRL_BREAK` | _qualsiasi_                           | **Nessun timeout**                                              |

_[1]: gli eventi "rapidi" non vengono mai usati, ma è ancora disponibile codice per supportarli._

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
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[Gestori di controlli console](console-control-handlers.md)

[Funzioni console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)

 

 




