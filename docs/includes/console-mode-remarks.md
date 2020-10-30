---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038875"
---
Una console di è costituita da un buffer di input e uno o più buffer dello schermo. La modalità di un buffer della console determina il comportamento della console durante le operazioni di input o output (I/O). Un set di costanti flag viene usato con gli handle di input e un altro set viene usato con gli handle del buffer dello schermo (output). L'impostazione delle modalità di output di un buffer dello schermo non influisce sulle modalità di output di altri buffer dello schermo.

Le **modalità \_ Abilita \_ input riga** e **Abilita \_ \_ input echo** influiscono solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) per la lettura dal buffer di input della console. Analogamente, l'abilitazione della modalità di **\_ \_ input elaborata** interessa principalmente gli utenti **ReadFile** e **ReadConsole** , con la differenza che determina anche se l'input di CTRL + C viene segnalato nel buffer di input (per la lettura da parte della funzione [**ReadConsoleInput**](../readconsoleinput.md) ) o viene passato a una funzione definita dall'applicazione.

Le **modalità \_ Abilita \_ input finestra** e **Abilita \_ \_ input mouse** determinano se le interazioni utente che coinvolgono il ridimensionamento delle finestre e le azioni del mouse vengono segnalate nel buffer di input o eliminate. Questi eventi possono essere letti da [**ReadConsoleInput**](../readconsoleinput.md), ma vengono sempre filtrati in base a [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](../readconsole.md).

L' **Abilitazione dell' \_ \_ output elaborato** e l' **Abilitazione del \_ wrapping \_ in modalità di \_ \_ output EOL** hanno effetto solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](../readconsole.md) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](../writeconsole.md).
