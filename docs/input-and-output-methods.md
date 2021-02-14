---
title: Metodi di input e output
description: Esistono due approcci diversi per l'I/O della console, la scelta tra cui dipende la flessibilità e il controllo delle esigenze di un'applicazione.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: e1802d3fd503d377cac9b404353f94c717b44f20
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358291"
---
# <a name="input-and-output-methods"></a>Metodi di input e output

Esistono due approcci diversi per l'I/O della console, la scelta tra cui dipende la flessibilità e il controllo delle esigenze di un'applicazione. L'approccio generale consente l'I/O del flusso di caratteri semplice, ma limita l'accesso ai buffer di input e dello schermo di una console. Con l'approccio di basso livello è necessario che gli sviluppatori scrivano altro codice e scelgano tra una gamma maggiore di funzioni, ma offre anche una maggiore flessibilità per un'applicazione.

> [!NOTE]
> L'approccio di basso livello non è consigliato per lo sviluppo nuovo e continuo. Le applicazioni che necessitano di funzionalità dalle funzioni di I/O della console di basso livello sono consigliate per l'uso di **[sequenze di terminali virtuali](console-virtual-terminal-sequences.md)** ed esplorare la documentazione su **[funzioni classiche rispetto al terminale virtuale](classic-vs-vt.md)** e **[alla roadmap degli ecosistemi](ecosystem-roadmap.md)**.

Un'applicazione può usare le funzioni di I/O dei file, [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile), e le funzioni console, [**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md), per l'i/o di alto livello che fornisce l'accesso indiretto ai buffer di input e dello schermo di una console. Le funzioni di input di alto livello filtrano ed elaborano i dati nel buffer di input di una console per restituire l'input come flusso di caratteri, ignorando l'input del mouse e del ridimensionamento del buffer. Analogamente, le funzioni di output di alto livello scrivono un flusso di caratteri visualizzati nella posizione corrente del cursore in un buffer dello schermo. Un'applicazione controlla la modalità di funzionamento di queste funzioni impostando le modalità I/O della console.

Le funzioni di I/O di basso livello forniscono l'accesso diretto ai buffer di input e dello schermo di una console, consentendo a un'applicazione di accedere a eventi di input per il mouse e il ridimensionamento del buffer e le informazioni estese per gli eventi della tastiera. Le funzioni di output di basso livello consentono a un'applicazione di leggere o scrivere in un numero specificato di celle di caratteri consecutivi in un buffer dello schermo o di leggere o scrivere in blocchi rettangolari di celle di tipo carattere in una posizione specificata in un buffer dello schermo. Le modalità di input di una console influiscono sull'input di basso livello, consentendo all'applicazione di determinare se gli eventi del mouse e del ridimensionamento del buffer vengono inseriti nel buffer di input. Le modalità di output di una console non hanno effetto sull'output di basso livello.

I metodi di I/O di alto livello e di basso livello non si escludono a vicenda e un'applicazione può usare qualsiasi combinazione di queste funzioni. In genere, tuttavia, un'applicazione usa esclusivamente un approccio o l'altro ed è consigliabile concentrarsi su un particolare paradigma per ottenere risultati ottimali.

> [!TIP]
> L'applicazione ideale per la ricerca in avanti si concentra sui metodi di alto livello e aumenta ulteriormente le esigenze con le **[sequenze di terminali virtuali](console-virtual-terminal-sequences.md)** tramite I metodi i/o di alto livello, quando necessario, evitando completamente l'utilizzo di funzioni di i/o di basso livello.

Negli argomenti seguenti vengono descritte le modalità console e le funzioni di I/O di alto livello e di basso livello.

- [Modalità della console](console-modes.md)
- [I/O console di alto livello](high-level-console-i-o.md)
- [Modalità console di alto livello](high-level-console-modes.md)
- [Funzioni di input e output console di alto livello](high-level-console-input-and-output-functions.md)
- [Sequenze del terminale virtuale della console](console-virtual-terminal-sequences.md)
- [Funzioni classiche rispetto alle sequenze di terminali virtuali](classic-vs-vt.md)
- [Roadmap all'ecosistema](ecosystem-roadmap.md)
- [I/O console di basso livello](low-level-console-i-o.md)
- [Modalità console di basso livello](low-level-console-modes.md)
- [Funzioni di input della console di basso livello](low-level-console-input-functions.md)
- [Funzioni di output della console di basso livello](low-level-console-output-functions.md)