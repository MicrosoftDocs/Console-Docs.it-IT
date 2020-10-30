---
title: SetConsoleCtrlHandler (funzione)
description: Aggiunge o rimuove una funzione HandlerRoutine definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 1c5c67bc5900a36bb50c0da90516fab0cec2e366
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039419"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler (funzione)

Aggiunge o rimuove una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.

Se non viene specificata alcuna funzione del gestore, la funzione imposta un attributo ereditabile che determina se il processo chiamante ignora i segnali <kbd>CTRL</kbd> + <kbd>C</kbd> .

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Parametri

*HandlerRoutine* \[ in, facoltativo\]  
Puntatore alla funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione da aggiungere o rimuovere. Questo parametro può essere **null** .

*Aggiungi* \[ in\]  
Se questo parametro è **true** , viene aggiunto il gestore; Se è **false** , il gestore viene rimosso.

Se il parametro *HandlerRoutine* è **null** , un **valore true** fa in modo che il processo chiamante ignori l'input <kbd>CTRL</kbd> + <kbd>c</kbd> e un valore **false** ripristini la normale elaborazione dell'input di <kbd>CTRL</kbd> + <kbd>c</kbd> . Questo attributo di ignorare o elaborare <kbd>CTRL</kbd> + <kbd>C</kbd> viene ereditato dai processi figlio.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Questa funzione fornisce una notifica simile per l'applicazione console e i servizi forniti da [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) per le applicazioni grafiche con un message pump. È anche possibile usare questa funzione da un'applicazione grafica, ma non vi è alcuna garanzia che arrivi prima della notifica da **WM \_ QUERYENDSESSION** .

Ogni processo della console dispone di un proprio elenco di funzioni [**HandlerRoutine**](handlerroutine.md) definite dall'applicazione che gestiscono i segnali <kbd>CTRL</kbd> + <kbd>C</kbd> e <kbd>CTRL</kbd> + <kbd>break</kbd> . Le funzioni del gestore gestiscono inoltre i segnali generati dal sistema quando l'utente chiude la console, si disconnette o arresta il sistema. Inizialmente, l'elenco dei gestori per ogni processo contiene solo una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processo console consente di aggiungere o rimuovere funzioni aggiuntive del gestore chiamando la funzione **SetConsoleCtrlHandler** , che non influisce sull'elenco di funzioni del gestore per altri processi. Quando un processo della console riceve uno dei segnali di controllo, le relative funzioni di gestione vengono chiamate in base a un'ultima chiamata registrata prima che uno dei gestori non restituisce `TRUE` . Se nessuno dei gestori restituisce `TRUE` , viene chiamato il gestore predefinito.

Per i processi della console, le combinazioni di tasti <kbd>CTRL</kbd> + <kbd>c</kbd> e <kbd>CTRL</kbd> + <kbd>interrompono</kbd> in genere vengono considerate come segnali (evento **CTRL \_ c \_** e **\_ \_ evento di rottura CTRL** ). Quando una finestra della console con lo stato attivo riceve <kbd>CTRL</kbd> + <kbd>C</kbd> o <kbd>CTRL</kbd> + <kbd>INTERR</kbd>, il segnale viene in genere passato a tutti i processi che condividono tale console.

<kbd>CTRL</kbd> + <kbd>Break</kbd> viene sempre considerato come un segnale, ma è <kbd>CTRL</kbd> + possibile modificare il comportamento tipico di CTRL<kbd>C</kbd> in tre modi che impediscono la chiamata delle funzioni del gestore:

- La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la **modalità \_ Abilita \_ input elaborato** per il buffer di input di una console, quindi <kbd>CTRL</kbd> + <kbd>C</kbd> viene segnalato come input da tastiera anziché come segnale.
- La chiamata di **SetConsoleCtrlHandler** con gli argomenti **null** e **true** fa in modo che il processo chiamante ignori i segnali <kbd>CTRL</kbd> + <kbd>C</kbd> . Questo attributo viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.
- Se è in corso il debug di un processo della console e i segnali <kbd>CTRL</kbd> + <kbd>c</kbd> non sono stati disabilitati, il sistema genera un'eccezione di **\_ controllo dbg \_ C** . Questa eccezione viene generata solo per il vantaggio del debugger e un'applicazione non deve mai usare un gestore di eccezioni per gestirla. Se l'eccezione viene gestita dal debugger, un'applicazione non noterà la <kbd>combinazione di tasti CTRL</kbd> + <kbd>C</kbd>, con una sola eccezione: le attese avvisi vengono terminate. Se il debugger passa l'eccezione su non gestito, <kbd>CTRL</kbd> + <kbd>C</kbd> viene passato al processo della console e considerato come un segnale, come descritto in precedenza.

Un processo della console può utilizzare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale <kbd>CTRL</kbd> + <kbd>C</kbd> o <kbd>CTRL</kbd> + <kbd>break</kbd> a un gruppo di processi della console.

Il sistema genera l'evento di **\_ chiusura \_ CTRL** , l' **\_ \_ evento di disconnessione** CTRL e i segnali **\_ \_ evento di chiusura CTRL** quando l'utente chiude la console, si disconnette o arresta il sistema in modo che il processo abbia la possibilità di eseguire la pulizia prima della terminazione. Le funzioni console, o qualsiasi funzione di runtime del linguaggio C che chiama funzioni console, potrebbero non funzionare in modo affidabile durante l'elaborazione di uno dei tre segnali citati in precedenza. Il motivo è che è possibile che alcune o tutte le routine di pulitura della console interna siano state chiamate prima di eseguire il gestore del segnale di processo.

**Windows 7, Windows 8, Windows 8.1 e Windows 10:**

Se un'applicazione console carica la libreria gdi32.dll o user32.dll, la funzione [**HandlerRoutine**](handlerroutine.md) specificata quando si chiama **SetConsoleCtrlHandler** non viene chiamata per l' **\_ \_ evento di disconnessione CTRL** e per gli eventi di **\_ arresto \_ di CTRL** . Il sistema operativo riconosce i processi che caricano gdi32.dll o user32.dll come applicazioni Windows anziché come applicazioni console. Questo comportamento si verifica anche per le applicazioni console che non chiamano funzioni direttamente in gdi32.dll o user32.dll, ma chiamano funzioni quali le funzioni [Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) che eseguono chiamate a loro volta in gdi32.dll o user32.dll.

Per ricevere eventi quando un utente si disconnette o il dispositivo si arresta in questi casi, creare una finestra nascosta nell'applicazione console e quindi gestire i messaggi della finestra [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) e [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) che la finestra nascosta riceve. È possibile creare una finestra nascosta chiamando il metodo [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con il parametro *dwExStyle* impostato su 0.

## <a name="examples"></a>Esempio

Per un esempio, vedere [registrazione di una funzione di gestione del controllo](registering-a-control-handler-function.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | |

## <a name="see-also"></a>Vedi anche

[Gestori di controllo della console](console-control-handlers.md)

[Funzioni console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)
