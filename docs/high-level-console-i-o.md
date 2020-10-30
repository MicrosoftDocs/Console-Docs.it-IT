---
title: I/O console High-Level
description: Le funzioni di I/O di alto livello forniscono un modo semplice per leggere un flusso di caratteri dall'input della console o per scrivere un flusso di caratteri nell'output della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 1ab8707fbc801962bbb32f17f7b575343ca530ba
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038679"
---
# <a name="high-level-console-io"></a>I/O console High-Level

Le funzioni di I/O di alto livello forniscono un modo semplice per leggere un flusso di caratteri dall'input della console o per scrivere un flusso di caratteri nell'output della console. Un'operazione di lettura di alto livello ottiene i caratteri di input dal buffer di input di una console e li archivia in un buffer specificato. Un'operazione di scrittura di alto livello accetta caratteri da un buffer specificato e li scrive in un buffer dello schermo in corrispondenza della posizione corrente del cursore, spostando il cursore mentre viene scritto ogni carattere.

L'I/O di alto livello consente di scegliere tra le funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) e le funzioni [**ReadConsole**](readconsole.md) e [**WriteConsole**](writeconsole.md) . Sono identici, tranne che per due importanti differenze. Le funzioni della console supportano l'utilizzo di caratteri Unicode o del set di caratteri ANSI tramite le varianti A e W di ogni funzione. le funzioni di I/O dei file non supportano Unicode, ad eccezione di UTF-8 impostato con la `CP_UTF8` costante nelle funzioni **[SetConsoleCP](setconsolecp.md)** e **[SetConsoleOutputCP](setconsoleoutputcp.md)** prima di usare. Inoltre, è possibile utilizzare le funzioni di I/O dei file per accedere ai file, alle pipe e ai dispositivi di comunicazione seriale. le funzioni della console possono essere utilizzate solo con handle di console. Questa distinzione è importante se un'applicazione si basa su handle standard che potrebbero essere stati reindirizzati.

Quando si usa un set di funzioni di alto livello, un'applicazione può controllare il testo e i colori di sfondo usati per visualizzare i caratteri successivamente scritti in un buffer dello schermo con il meccanismo preferito tramite **[sequenze di terminali virtuali](console-virtual-terminal-sequences.md)** . Un'applicazione può inoltre utilizzare le modalità console che interessano le operazioni di I/O della console di alto livello per abilitare o disabilitare le proprietà seguenti:

- Ripetizione dell'input della tastiera sul buffer dello schermo attivo
- Input di riga, in cui un'operazione di lettura non viene restituita fino a quando non viene premuto il tasto invio
- Elaborazione automatica dell'input da tastiera per gestire i ritorni a capo, CTRL + C e altri dettagli di input
- Elaborazione automatica dell'output per gestire il ritorno a capo delle righe, i ritorni a capo, gli spazi e gli altri dettagli di output

Per altre informazioni, vedere i seguenti argomenti:

- [Modalità console](console-modes.md)
- [Modalità console di alto livello](high-level-console-modes.md)
- [Funzioni di input e output console di alto livello](high-level-console-input-and-output-functions.md)
- [API classiche e sequenze di terminali virtuali](classic-vs-vt.md)
