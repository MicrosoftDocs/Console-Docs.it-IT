---
title: Funzioni di input e output della console High-Level
description: Le funzioni ReadFile e WriteFile, o le funzioni ReadConsole e WriteConsole, consentono a un'applicazione di leggere l'input della console e di scrivere l'output della console come flusso di caratteri.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: 4da8845e4e35170980d306930c182ff6e5fb6cbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358301"
---
# <a name="high-level-console-input-and-output-functions"></a>Funzioni di input e output della console High-Level

Le funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) , o le funzioni [**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md) , consentono a un'applicazione di leggere l'input della console e di scrivere l'output della console come flusso di caratteri. **ReadConsole** e **WriteConsole** si comportano esattamente come **ReadFile** e **WriteFile** , ad eccezione del fatto che possono essere usati come funzioni a caratteri wide (in cui gli argomenti di testo devono usare Unicode) o come funzioni ANSI (in cui gli argomenti di testo devono usare caratteri del set di caratteri di Windows). Le applicazioni che devono gestire un singolo set di origini per supportare Unicode o il set di caratteri ANSI devono usare **ReadConsole** e **WriteConsole**.

[**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md) possono essere usati solo con gli handle della console. [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) possono essere usati con altri handle, ad esempio file o pipe. **ReadConsole** e **WriteConsole** hanno esito negativo se usato con un handle standard che è stato reindirizzato e non è più un handle della console.

Per ottenere l'input da tastiera, un processo può usare [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) con un handle per il buffer di input della console oppure può usare **ReadFile** per leggere l'input da un file o una pipe se `STDIN` è stato reindirizzato. Queste funzioni restituiscono solo eventi di tastiera che possono essere convertiti in caratteri ANSI o Unicode. L'input che può essere restituito include le combinazioni di tasti del controllo. Le funzioni non restituiscono gli eventi della tastiera che coinvolgono i tasti funzione o i tasti di direzione. Gli eventi di input generati dal mouse, dalla finestra, dallo stato attivo o dall'input del menu vengono eliminati.

Se la modalità di input della riga è abilitata (modalità predefinita), [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**ReadConsole**](readconsole.md) non ritornano all'applicazione chiamante fino a quando non viene premuto il tasto INVIO. Se la modalità di input della riga è disabilitata, le funzioni non restituiscono finché non è disponibile almeno un carattere. In entrambe le modalità, tutti i caratteri disponibili vengono letti fino a quando non sono disponibili altre chiavi o il numero di caratteri specificato è stato letto. I caratteri non letti vengono memorizzati nel buffer fino alla successiva operazione di lettura. Le funzioni segnalano il numero totale di caratteri effettivamente letti. Se è abilitata la modalità di input echo, i caratteri letti da queste funzioni vengono scritti nel buffer dello schermo attivo nella posizione corrente del cursore.

Un processo può usare [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o **WriteConsole** per scrivere in un buffer dello schermo attivo o inattivo oppure può usare **WriteFile** per scrivere in un file o una pipe se stdout è stato reindirizzato. La modalità di output elaborata e il wrapping in modalità di output EOL controllano il modo in cui i caratteri vengono scritti o restituiti a un buffer dello schermo.

I caratteri scritti da [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md), o restituiti da [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md), vengono inseriti in un buffer dello schermo in corrispondenza della posizione corrente del cursore. Quando viene scritto ogni carattere, la posizione del cursore passa alla cella del carattere successivo. Tuttavia, il comportamento alla fine di una riga dipende dal wrapping del buffer dello schermo della console alla modalità di output EOL.

Per ulteriori dettagli sulla posizione del cursore, è possibile usare le **[sequenze di terminali virtuali](console-virtual-terminal-sequences.md)**, in particolare nella categoria **[stato query](console-virtual-terminal-sequences.md#query-state)** , per trovare la posizione corrente e la categoria **[posizionamento cursore](console-virtual-terminal-sequences.md#cursor-positioning)** per l'impostazione della posizione corrente. In alternativa, un'applicazione può utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per determinare la posizione corrente del cursore e la funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) per impostare la posizione del cursore. Tuttavia, il meccanismo delle **sequenze di terminali virtuali** è preferibile per lo sviluppo nuovo e continuo. Per ulteriori informazioni sulla strategia alla base di questa decisione, vedere la documentazione relativa alle **[funzioni classiche rispetto](classic-vs-vt.md)** alla guida alla roadmap per gli **[ecosistemi](ecosystem-roadmap.md)** e ai terminali virtuali.

Per un esempio in cui vengono utilizzate le funzioni di I/O della console di alto livello, vedere [utilizzo delle funzioni di input e Output High-Level](using-the-high-level-input-and-output-functions.md).