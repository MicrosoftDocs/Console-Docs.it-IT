---
title: Informazioni sulle console
description: Le console di offrono un supporto di alto livello per le applicazioni in modalità carattere semplici che interagiscono con l'utente utilizzando le funzioni che leggono dall'input standard e scrivono in output standard o errore standard.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060249"
---
# <a name="about-character-mode-applications"></a>Informazioni sulle applicazioni in modalità carattere

Applicazioni in modalità carattere (o "riga di comando"):

1. Facoltativamente Leggere i dati dall'input standard (stdin)
2. "Lavoro"
3. Facoltativamente Scrivere dati in output standard (stdout) o errore standard (stderr)

Le applicazioni in modalità carattere comunicano con l'utente finale tramite un'applicazione "console" (o "terminale"). Una console converte l'input dell'utente da tastiera, mouse, touch screen, penna e così via e lo invia a un stdin dell'applicazione in modalità carattere. Una console può anche visualizzare l'output di testo di un'applicazione in modalità carattere sullo schermo dell'utente.

In Windows la console è incorporata e fornisce un'API avanzata tramite cui le applicazioni in modalità carattere possono interagire con l'utente.

- [Console](consoles.md)
- [Metodi di input e output](input-and-output-methods.md)
- [Tabelle codici della console](console-code-pages.md)
- [Gestori di controlli console](console-control-handlers.md)
- [Alias di console](console-aliases.md)
- [Diritti di accesso e sicurezza del buffer della console](console-buffer-security-and-access-rights.md)
- [Problemi delle applicazioni console](console-application-issues.md)

 

 




