---
title: SetConsoleCtrlHandler (funzione)
description: Aggiunge o rimuove una funzione HandlerRoutine definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060292"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler (funzione)


Aggiunge o rimuove una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione dall'elenco di funzioni del gestore per il processo chiamante.

Se non viene specificata alcuna funzione del gestore, la funzione imposta un attributo ereditabile che determina se il processo chiamante ignora i segnali CTRL + C.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a>Parametri
----------

*HandlerRoutine* \[ in, facoltativo\]  
Puntatore alla funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione da aggiungere o rimuovere. Questo parametro può essere **null**.

*Aggiungi* \[ in\]  
Se questo parametro è **true**, viene aggiunto il gestore; Se è **false**, il gestore viene rimosso.

Se il parametro *HandlerRoutine* è **null**, un valore **true** fa in modo che il processo chiamante ignori l'input di CTRL + c e un valore **false** ripristini l'elaborazione normale dell'input di CTRL + c. Questo attributo di ignorare o elaborare CTRL + C viene ereditato dai processi figlio.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Questa funzione fornisce una notifica simile per l'applicazione console e i servizi forniti da [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) per le applicazioni grafiche con un message pump. È anche possibile usare questa funzione da un'applicazione grafica, ma non vi è alcuna garanzia che arrivi prima della notifica da **WM \_ QUERYENDSESSION**.

Ogni processo della console dispone di un proprio elenco di funzioni [**HandlerRoutine**](handlerroutine.md) definite dall'applicazione che gestiscono i segnali CTRL + C e CTRL + INTERR. Le funzioni del gestore gestiscono inoltre i segnali generati dal sistema quando l'utente chiude la console, si disconnette o arresta il sistema. Inizialmente, l'elenco dei gestori per ogni processo contiene solo una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processo console consente di aggiungere o rimuovere funzioni aggiuntive del gestore chiamando la funzione **SetConsoleCtrlHandler** , che non influisce sull'elenco di funzioni del gestore per altri processi. Quando un processo della console riceve uno dei segnali di controllo, le relative funzioni di gestione vengono chiamate in base a un'ultima chiamata registrata prima che uno dei gestori restituisca TRUE. Se nessuno dei gestori restituisce TRUE, viene chiamato il gestore predefinito.

Per i processi della console, le combinazioni di tasti CTRL + C e CTRL + INTERr vengono in genere considerate come segnali (evento**CTRL \_ C \_ ** e ** \_ \_ evento di rottura CTRL**). Quando una finestra della console con lo stato attivo riceve la combinazione di tasti CTRL + C o CTRL + INTERr, il segnale viene in genere passato a tutti i processi che condividono tale console.

CTRL + INTERr viene sempre considerato come un segnale, ma è possibile modificare il comportamento tipico di CTRL + C in tre modi che impediscono la chiamata delle funzioni del gestore:

- La funzione [**SetConsoleMode**](setconsolemode.md) può disabilitare la **modalità \_ Abilita \_ input elaborato** per il buffer di input di una console, quindi CTRL + C viene segnalato come input da tastiera anziché come segnale.
- La chiamata di **SetConsoleCtrlHandler** con gli argomenti **null** e **true** fa sì che il processo chiamante ignori i segnali CTRL + C. Questo attributo viene ereditato dai processi figlio, ma può essere abilitato o disabilitato da qualsiasi processo senza influire sui processi esistenti.
- Se è in corso il debug di un processo console e i segnali CTRL + C non sono stati disabilitati, il sistema genera un'eccezione di ** \_ controllo dbg \_ C** . Questa eccezione viene generata solo per il vantaggio del debugger e un'applicazione non deve mai usare un gestore di eccezioni per gestirla. Se l'eccezione viene gestita dal debugger, un'applicazione non noterà la combinazione di tasti CTRL + C, con una sola eccezione: le attese avvisi vengono terminate. Se il debugger passa l'eccezione su non gestito, CTRL + C viene passato al processo della console e considerato come un segnale, come descritto in precedenza.

Un processo console può usare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale CTRL + C o Ctrl + Break a un gruppo di processi della console.

Il sistema genera l'evento di ** \_ chiusura \_ CTRL**, l' ** \_ \_ evento di disconnessione**CTRL e i segnali ** \_ \_ evento di chiusura CTRL** quando l'utente chiude la console, si disconnette o arresta il sistema in modo che il processo abbia la possibilità di eseguire la pulizia prima della terminazione. Le funzioni console, o qualsiasi funzione di runtime del linguaggio C che chiama funzioni console, potrebbero non funzionare in modo affidabile durante l'elaborazione di uno dei tre segnali citati in precedenza. Il motivo è che è possibile che alcune o tutte le routine di pulitura della console interna siano state chiamate prima di eseguire il gestore del segnale di processo.

**Windows 7, Windows 8, Windows 8.1 e Windows 10:**

Se un'applicazione console carica la libreria gdi32.dll o user32.dll, la funzione [**HandlerRoutine**](handlerroutine.md) specificata quando si chiama **SetConsoleCtrlHandler** non viene chiamata per l' ** \_ \_ evento di disconnessione CTRL** e per gli eventi di ** \_ arresto \_ di CTRL** . Il sistema operativo riconosce i processi che caricano gdi32.dll o user32.dll come applicazioni Windows anziché come applicazioni console. Questo comportamento si verifica anche per le applicazioni console che non chiamano funzioni direttamente in gdi32.dll o user32.dll, ma chiamano funzioni quali le funzioni [Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) che eseguono chiamate a loro volta in gdi32.dll o user32.dll.

Per ricevere eventi quando un utente si disconnette o il dispositivo si arresta in questi casi, creare una finestra nascosta nell'applicazione console e quindi gestire i messaggi della finestra [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) e [**WM \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) che la finestra nascosta riceve. È possibile creare una finestra nascosta chiamando il metodo [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con il parametro *dwExStyle* impostato su 0.

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [registrazione di una funzione di gestione del controllo](registering-a-control-handler-function.md).

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


[Gestori di controlli console](console-control-handlers.md)

[Funzioni console](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)

 

 




