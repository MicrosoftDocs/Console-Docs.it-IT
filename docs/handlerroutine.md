---
title: Funzione di callback HandlerRoutine
description: Funzione definita dall'applicazione utilizzata con la funzione SetConsoleCtrlHandler. Un processo della console usa questa funzione per gestire i segnali di controllo ricevuti dal processo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
- WinCon.h
api_type:
- UserDefined
ms.openlocfilehash: bd028892101b38ac7f0bfa307547ca4aa4cf5b0e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358741"
---
# <a name="handlerroutine-callback-function"></a>Funzione di callback HandlerRoutine

Funzione definita dall'applicazione utilizzata con la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Un processo della console usa questa funzione per gestire i segnali di controllo ricevuti dal processo. Quando viene ricevuto il segnale, il sistema crea un nuovo thread nel processo per eseguire la funzione.

Il tipo di **\_ routine PHANDLER** definisce un puntatore a questa funzione di callback. **HandlerRoutine** è un segnaposto per il nome della funzione definita dall'applicazione.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

## <a name="parameters"></a>Parametri

*dwCtrlType* \[ in\]  
Tipo di segnale di controllo ricevuto dal gestore. Questo parametro può avere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **CTRL_C_EVENT** 0 | <kbd></kbd> + È stato ricevuto un segnale CTRL <kbd>C</kbd> , dall'input da tastiera o da un segnale generato dalla funzione **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** . |
| **CTRL_BREAK_EVENT** 1 | <kbd></kbd> + È stato ricevuto un segnale di <kbd>rottura</kbd> CTRL, dall'input da tastiera o da un segnale generato da **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)**. |
| **CTRL_CLOSE_EVENT** 2 | Segnale inviato dal sistema a tutti i processi collegati a una console quando l'utente chiude la console (scegliendo **Chiudi** dal menu finestra della finestra della console oppure facendo clic sul pulsante **Termina attività** da Gestione attività). |
| **CTRL_LOGOFF_EVENT** 5 | Segnale inviato dal sistema a tutti i processi della console quando un utente esegue la disconnessione. Questo segnale non indica quale utente sta effettuando la disconnessione, pertanto non è possibile effettuare supposizioni.<br /><br />Si noti che questo segnale viene ricevuto solo dai servizi. Le applicazioni interattive vengono terminate alla disconnessione, quindi non sono presenti quando il sistema invia questo segnale. |
| **CTRL_SHUTDOWN_EVENT** 6 | Segnale inviato dal sistema alla chiusura del sistema. Le applicazioni interattive non sono presenti nel momento in cui il sistema invia questo segnale, pertanto può essere ricevuto solo da servizi in questa situazione. I servizi hanno anche un proprio meccanismo di notifica per gli eventi di arresto. Per ulteriori informazioni, vedere **[handler](/windows/win32/api/winsvc/nc-winsvc-lphandler_function)**.<br /><br />Questo segnale può essere generato anche da un'applicazione che usa **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)**. |

## <a name="return-value"></a>Valore restituito

Se la funzione gestisce il segnale di controllo, deve restituire **true**. Se restituisce **false**, viene utilizzata la funzione del gestore successiva nell'elenco dei gestori per questo processo.

## <a name="remarks"></a>Commenti

Poiché il sistema crea un nuovo thread nel processo per eseguire la funzione del gestore, è possibile che la funzione del gestore venga terminata da un altro thread nel processo. Assicurarsi di sincronizzare i thread del processo con il thread per la funzione del gestore.

Ogni processo della console dispone di un proprio elenco di funzioni **HandlerRoutine** . Inizialmente, questo elenco contiene solo una funzione di gestione predefinita che chiama [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess). Un processo console consente di aggiungere o rimuovere funzioni aggiuntive del gestore chiamando la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) , che non influisce sull'elenco di funzioni del gestore per altri processi. Quando un processo della console riceve uno dei segnali di controllo, le relative funzioni di gestione vengono chiamate in base a un'ultima chiamata registrata prima che uno dei gestori restituisca **true**. Se nessuno dei gestori restituisce **true**, viene chiamato il gestore predefinito.

L' **\_ \_ evento CTRL Close**, **l' \_ \_ evento di disconnessione CTRL** e i segnali **\_ \_ evento di chiusura CTRL** consentono al processo di eseguire la pulizia prima della terminazione. Un **HandlerRoutine** può eseguire tutte le operazioni di pulizia necessarie, quindi eseguire una delle operazioni seguenti:

- Chiamare la funzione [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) per terminare il processo.
- Restituisce **false**. Se nessuna delle funzioni del gestore registrate restituisce **true**, il gestore predefinito termina il processo.
- Restituisce **true**. In questo caso, non vengono chiamate altre funzioni del gestore e il sistema termina il processo.

Un processo può utilizzare la funzione [**SetProcessShutdownParameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setprocessshutdownparameters) per impedire al sistema di visualizzare una finestra di dialogo all'utente durante la disconnessione o l'arresto. In questo caso, il sistema termina il processo quando **HandlerRoutine** restituisce **true** o quando scade il periodo di timeout.

Quando un'applicazione console viene eseguita come servizio, riceve un gestore di controllo della console predefinito modificato. Questo gestore modificato non chiama [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) durante l'elaborazione dell' **\_ \_ evento di disconnessione CTRL** e dei segnali di **chiusura dell' \_ \_ evento CTRL** . Ciò consente al servizio di continuare l'esecuzione dopo che l'utente si disconnette. Se il servizio installa il proprio gestore di controllo della console, questo gestore viene chiamato prima del gestore predefinito. Se il gestore installato chiama **ExitProcess** durante l'elaborazione del segnale dell' **\_ \_ evento di disconnessione CTRL** , il servizio viene chiuso quando l'utente si disconnette.

Si noti che una libreria o una DLL di terze parti può installare un gestore di controllo della console per l'applicazione. In caso contrario, questo gestore esegue l'override del gestore predefinito e può causare la chiusura dell'applicazione quando l'utente si disconnette.

## <a name="timeouts"></a>Timeout

| Evento                  | Circostanze                   | Timeout                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _qualsiasi_                           | parametro `SPI_GETHUNGAPPTIMEOUT` di sistema, 5000 ms            |
| `CTRL_LOGOFF_EVENT`    | _rapido_[1] | chiave del registro di sistema `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _nessuno dei precedenti_             | parametro `SPI_GETWAITTOKILLTIMEOUT` di sistema, 5000 ms         |
| `CTRL_SHUTDOWN_EVENT`  | **processo del servizio**             | parametro `SPI_GETWAITTOKILLSERVICETIMEOUT` di sistema, 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _rapido_[1] | chiave del registro di sistema `CriticalAppShutdownTimeout` o 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _nessuno dei precedenti_             | parametro `SPI_GETWAITTOKILLTIMEOUT` di sistema, 5000 ms         |
| `CTRL_C`, `CTRL_BREAK` | _qualsiasi_                           | **Nessun timeout**                                              |

_[1]: gli eventi "rapidi" non vengono mai usati, ma è ancora disponibile codice per supportarli._

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |

## <a name="see-also"></a>Vedere anche

[Gestori di controllo della console](console-control-handlers.md)

[Funzioni della console](console-functions.md)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocessshutdownparameters)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setprocessshutdownparameters)