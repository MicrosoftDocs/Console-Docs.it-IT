---
ms.openlocfilehash: ca6de914ff9199090e96e2c813a176fcc90df27d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357281"
---
Una console è costituita da un buffer di input e da uno o più buffer dello schermo. La modalità di un buffer della console determina il comportamento della console durante le operazioni di input o output (I/O). Un set di costanti flag viene usato con gli handle di input e un altro set viene usato con gli handle del buffer dello schermo (output). L'impostazione delle modalità di output di un buffer dello schermo non influisce sulle modalità di output degli altri buffer dello schermo.

Le modalità **ENABLE\_LINE\_INPUT** e **ENABLE\_ECHO\_INPUT** influiscono solo sui processi che utilizzano le funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](../readconsole.md) per leggere dal buffer di input della console. Analogamente la modalità **ENABLE\_PROCESSED\_INPUT** influisce principalmente sugli utenti **ReadFile** e **ReadConsole** ad eccezione del fatto che determina anche se l'input di CTRL + C viene riportato nel buffer di input (per la lettura da parte della funzione [**ReadConsoleInput**](../readconsoleinput.md)) o viene passato a una funzione definita dall'applicazione.

Le modalità **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** determinano se le interazioni dell'utente che coinvolgono il ridimensionamento delle finestre e le azioni del mouse vengono riportate nel buffer di input o eliminate. Questi eventi possono essere letti dalla funzione [**ReadConsoleInput**](../readconsoleinput.md) ma vengono sempre filtrati dalle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**ReadConsole**](../readconsole.md).

Le modalità **ENABLE\_PROCESSED\_OUTPUT** e **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** influiscono solo i processi che utilizzano le funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](../readconsole.md) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](../writeconsole.md).