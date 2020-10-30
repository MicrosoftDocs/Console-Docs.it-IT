---
title: Informazioni sulle console
description: Le console di offrono un supporto di alto livello per le applicazioni in modalità carattere semplici che interagiscono con l'utente utilizzando le funzioni che leggono dall'input standard e scrivono in output standard o errore standard.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037529"
---
# <a name="about-character-mode-applications"></a>Informazioni sulle applicazioni in modalità carattere

Applicazioni in modalità carattere (o "riga di comando"):

1. \[Facoltativamente \] , leggere i dati dall'input standard (stdin)
2. "Lavoro"
3. \[Facoltativamente \] , scrivere i dati nell'output standard (stdout) o nell'errore standard (stderr)

Le applicazioni in modalità carattere comunicano con l'utente finale tramite un'applicazione "console" (o "terminale"). Una console converte l'input dell'utente da tastiera, mouse, touch screen, penna e così via e lo invia a un stdin dell'applicazione in modalità carattere. Una console può anche visualizzare l'output di testo di un'applicazione in modalità carattere sullo schermo dell'utente.

In Windows la console è incorporata e fornisce un'API avanzata tramite cui le applicazioni in modalità carattere possono interagire con l'utente. Tuttavia, nell'era recente, il team di console sta incoraggiando tutte le applicazioni in modalità carattere da sviluppare con le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) tramite le chiamate API classiche per la massima compatibilità tra Windows e altri sistemi operativi. Altre informazioni su questa transizione e sui compromessi sono disponibili nella discussione sulle [API classiche rispetto alle sequenze di terminali virtuali](classic-vs-vt.md).

- [Console](consoles.md)
- [Metodi di input e output](input-and-output-methods.md)
- [Tabelle codici della console](console-code-pages.md)
- [Gestori di controllo della console](console-control-handlers.md)
- [Alias di console](console-aliases.md)
- [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md)
- [Problemi relativi alle applicazioni console](console-application-issues.md)
