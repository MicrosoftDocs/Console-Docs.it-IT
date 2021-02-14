---
title: SetConsoleCtrlHandler (funzione)
description: Aggiunge o rimuove una funzione HandlerRoutine definita dall'applicazione nell'elenco di funzioni gestore per il processo chiamante.
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
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357711"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler (funzione)

Aggiunge o rimuove una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione nell'elenco di funzioni di gestione per il processo chiamante.

Se non viene specificata alcuna funzione gestore, la funzione imposta un attributo ereditabile che determina se il processo chiamante ignora i segnali <kbd>CTRL</kbd>+<kbd>C</kbd>.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Parametri

*HandlerRoutine* \[in, facoltativo\]  
Un puntatore alla funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione da aggiungere o rimuovere. Questo parametro può essere **NULL**.

*Add* \[in\]  
Se questo parametro è **TRUE**, il gestore viene aggiunto; se è **FALSE**, il gestore viene rimosso.

Se il parametro *HandlerRoutine* è **NULL**, il valore **TRUE** fa in modo che il processo chiamante ignori l'input <kbd>CTRL</kbd>+<kbd>C</kbd> e il valore **FALSE** ripristina la normale elaborazione dell'input <kbd>CTRL</kbd>+<kbd>C</kbd>. Questo attributo che determina se <kbd>CTRL</kbd>+<kbd>C</kbd> viene ignorato o elaborato viene ereditato dai processi figlio.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Questa funzione fornisce una notifica simile per l'applicazione console e i servizi che [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) fornisce per le applicazioni grafiche con un message pump. È anche possibile usare questa funzione da un'applicazione grafica, ma non è garantito che arrivi prima della notifica da **WM\_QUERYENDSESSION**.

Ogni processo della console dispone di un elenco specifico di funzioni [**HandlerRoutine**](handlerroutine.md) definite dall'applicazione che gestiscono i segnali <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>BREAK</kbd>. Le funzioni gestore gestiscono anche i segnali generati dal sistema quando l'utente chiude la console, si disconnette o arresta il sistema. Inizialmente, l'elenco dei gestori per ogni processo contiene solo una funzione gestore predefinita che chiama la funzione [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess). Un processo della console aggiunge o rimuove ulteriori funzioni gestore chiamando la funzione **SetConsoleCtrlHandler**, che non influisce sull'elenco di funzioni gestore per altri processi. Quando un processo della console riceve uno dei segnali di controllo, vengono chiamate le relative funzioni gestore, partendo dall'ultima registrata, finché uno dei gestori non restituisce `TRUE`. Se nessuno dei gestori restituisce `TRUE`, viene chiamato il gestore predefinito.

Per i processi della console, le combinazioni di tasti <kbd>CTRL</kbd>+<kbd>C</kbd> e <kbd>CTRL</kbd>+<kbd>INTERR</kbd> in genere vengono considerate come segnali (**CTRL\_C\_EVENT** e **CTRL\_BREAK\_EVENT**). Quando una finestra della console con lo stato attivo della tastiera riceve <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd>, il segnale viene generalmente passato a tutti i processi che condividono tale console.

<kbd>CTRL</kbd>+<kbd>INTERR</kbd> viene sempre considerato come segnale, ma è possibile modificare il comportamento tipico di <kbd>CTRL</kbd>+<kbd>C</kbd> in tre modi che impediscono la chiamata delle funzioni gestore:

- La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la modalità **ENABLE\_PROCESSED\_INPUT** per il buffer di input di una console, in modo che <kbd>CTRL</kbd>+<kbd>C</kbd> venga segnalato come input di tastiera anziché come segnale.
- Se si chiama **SetConsoleCtrlHandler** con gli argomenti **NULL** e **TRUE**, il processo chiamante ignora i segnali <kbd>CTRL</kbd>+<kbd>C</kbd>. Questo attributo viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.
- Se è in corso il debug di un processo della console e i segnali <kbd>CTRL</kbd>+<kbd>C</kbd> segnali non sono stati disabilitati, il sistema genera un'eccezione **DBG\_CONTROL\_C**. Questa eccezione viene generata solo a vantaggio del debugger e un'applicazione non deve mai usare un gestore di eccezioni per gestirla. Se l'eccezione viene gestita dal debugger, un'applicazione non noterà la combinazione <kbd>CTRL</kbd>+<kbd>C</kbd>, con un'eccezione: le attese con avvisi vengono terminate. Se il debugger imposta l'eccezione su non gestita, <kbd>CTRL</kbd>+<kbd>C</kbd> viene passato al processo della console e considerato come un segnale, come indicato in precedenza.

Un processo della console può usare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>INTERR</kbd> a un gruppo di processi della console.

Il sistema genera i segnali **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** e **CTRL\_SHUTDOWN\_EVENT** quando l'utente chiude la console, si disconnette o arresta il sistema, per consentire al processo di eseguire la pulizia prima della terminazione. Le funzioni della console, o qualsiasi funzione di runtime C che chiama funzioni della console, potrebbero non funzionare in modo affidabile durante l'elaborazione di uno dei tre segnali citati in precedenza. Questo perché alcune o tutte le routine di pulitura della console interna potrebbero essere state chiamate prima dell'esecuzione del gestore di segnale del processo.

**Windows 7, Windows 8, Windows 8.1 e Windows 10:**

Se un'applicazione console carica la libreria gdi32.dll o user32.dll, la funzione [**HandlerRoutine**](handlerroutine.md) specificata chiamando **SetConsoleCtrlHandler** non viene chiamata per gli eventi **CTRL\_LOGOFF\_EVENT** e **CTRL\_SHUTDOWN\_EVENT**. Il sistema operativo riconosce i processi che caricano gdi32.dll o user32.dll come applicazioni Windows anziché come applicazioni console. Questo comportamento si verifica anche per le applicazioni console che non chiamano direttamente le funzioni in gdi32.dll o user32.dll, ma chiamano funzioni come le [funzioni Shell](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) che a loro volta chiamano le funzioni in gdi32.dll o user32.dll.

Per ricevere eventi quando un utente si disconnette o il dispositivo si arresta in questi casi, creare una finestra nascosta nell'applicazione console e quindi gestire i messaggi [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) e [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) ricevuti dalla finestra nascosta. È possibile creare una finestra nascosta chiamando il metodo [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) con il parametro *dwExStyle* impostato su 0.

## <a name="examples"></a>Esempi

Un esempio è disponibile in [Registrazione di una funzione gestore di controllo](registering-a-control-handler-function.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | |

## <a name="see-also"></a>Vedere anche

[Gestori di controllo della console](console-control-handlers.md)

[Funzioni della console](console-functions.md)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)