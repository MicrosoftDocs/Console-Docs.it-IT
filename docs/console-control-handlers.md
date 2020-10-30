---
title: Gestori di controllo della console
description: Ogni processo della console dispone di un proprio elenco di funzioni del gestore di controllo chiamate dal sistema quando il processo riceve un segnale CTRL + C, CTRL + INTERr o CTRL + CLOSE.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 41a1326b5b27531bf74ac571d6881a0f67c2b073
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038429"
---
# <a name="console-control-handlers"></a>Gestori di controllo della console

Ogni processo della console dispone di un proprio elenco di funzioni del gestore di controllo chiamate dal sistema quando il processo riceve un segnale [CTRL + C](ctrl-c-and-ctrl-break-signals.md), [CTRL + INTERR](ctrl-c-and-ctrl-break-signals.md)o [CTRL + Close](ctrl-close-signal.md) . Inizialmente, l'elenco dei gestori di controllo per ogni processo contiene solo una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un processo della console può aggiungere o rimuovere funzioni [**HandlerRoutine**](handlerroutine.md) aggiuntive chiamando la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Questa funzione non influisce sugli elenchi di gestori di controllo per altri processi. Quando un processo della console riceve uno dei segnali di controllo, chiama le funzioni del gestore su una base Ultima registrazione, prima chiamata, fino a quando uno dei gestori non restituisce **true** . Se nessuno dei gestori restituisce **true** , viene chiamato il gestore predefinito.

Il parametro *dwCtrlType* della funzione identifica il segnale di controllo ricevuto e il valore restituito indica se il segnale è stato gestito.

Un nuovo thread viene avviato all'interno del processo client della riga di comando per eseguire le routine del gestore. Altre informazioni sui valori di timeout e sull'azione di questo thread sono reperibili nella documentazione della funzione [**HandlerRoutine**](handlerroutine.md#remarks) .

Per un esempio di una funzione del gestore di controllo, vedere [registrazione di una funzione](registering-a-control-handler-function.md)di gestione del controllo.
