---
title: Dimensioni del buffer della finestra e dello schermo
description: Le dimensioni di un buffer dello schermo sono espresse in termini di una griglia di coordinate basata su celle di tipo carattere.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 86a8967eeff35a7a5416273e639ba8bbe5a31ef1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060513"
---
# <a name="window-and-screen-buffer-size"></a>Dimensioni del buffer della finestra e dello schermo


Le dimensioni di un buffer dello schermo sono espresse in termini di una griglia di coordinate basata su celle di tipo carattere. La larghezza è il numero di celle di tipo carattere in ogni riga e l'altezza è il numero di righe. Associato a ogni buffer dello schermo è una finestra che determina le dimensioni e la posizione della parte rettangolare del buffer dello schermo della console visualizzato nella finestra della console. La finestra di un buffer dello schermo viene definita specificando le coordinate delle celle dei caratteri delle celle in alto a sinistra e in basso a destra del rettangolo della finestra.

Un buffer dello schermo può essere di qualsiasi dimensione, limitato solo dalla memoria disponibile. Le dimensioni della finestra di un buffer dello schermo non possono superare le dimensioni corrispondenti del buffer dello schermo della console o della finestra massima che può rientrare sullo schermo in base alle dimensioni del carattere corrente (controllate esclusivamente dall'utente).

La funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) restituisce le informazioni seguenti su un buffer dello schermo e la relativa finestra:

- Dimensioni correnti del buffer dello schermo della console
- Posizione corrente della finestra
- Dimensioni massime della finestra in base alla dimensione corrente del buffer dello schermo, alla dimensione corrente del carattere e alle dimensioni dello schermo

La funzione [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) restituisce la dimensione massima della finestra di una console in base al tipo di carattere e alle dimensioni dello schermo correnti. Questa dimensione è diversa dalle dimensioni massime della finestra restituite da [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) in quanto le dimensioni del buffer dello schermo della console vengono ignorate.

Per modificare le dimensioni di un buffer dello schermo, utilizzare la funzione [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) . Questa funzione ha esito negativo se una o più dimensioni della dimensione specificata sono inferiori alla dimensione corrispondente della finestra della console.

Per modificare le dimensioni o la posizione della finestra di un buffer dello schermo, utilizzare la funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) . Questa funzione ha esito negativo se le coordinate dell'angolo finestra specificate superano i limiti del buffer dello schermo della console o dello schermo. La modifica delle dimensioni della finestra del buffer dello schermo attivo cambia le dimensioni della finestra della console visualizzata sullo schermo.

Un processo può modificare la modalità di input della console per abilitare l'input della finestra, in modo che il processo sia in grado di ricevere input quando l'utente modifica le dimensioni del buffer dello schermo della console. Se un'applicazione Abilita l'input della finestra, può usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per recuperare le dimensioni del buffer della finestra e dello schermo all'avvio. Queste informazioni possono quindi essere usate per determinare il modo in cui i dati vengono visualizzati nella finestra. Se l'utente modifica le dimensioni del buffer dello schermo della console, l'applicazione può rispondere modificando il modo in cui vengono visualizzati i dati. Ad esempio, un'applicazione può modificare la modalità di ritorno a capo del testo alla fine della riga se il numero di caratteri per riga cambia. Se un'applicazione non Abilita l'input della finestra, deve usare la finestra ereditata e le dimensioni del buffer dello schermo oppure impostarle sulle dimensioni desiderate durante l'avvio e ripristinare le dimensioni ereditate all'uscita. Per ulteriori informazioni sulla modalità di input della finestra, vedere [modalità console di basso livello](low-level-console-modes.md).

 

 




