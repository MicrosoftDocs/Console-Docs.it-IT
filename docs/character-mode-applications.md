---
title: Applicazioni in modalità carattere
description: Le console di gestiscono l'input e l'output (I/O) per le applicazioni in modalità carattere (applicazioni che non forniscono una propria interfaccia utente grafica).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037349"
---
# <a name="character-mode-applications"></a>Applicazioni in modalità carattere

Le console di gestiscono l'input e l'output (I/O) per le applicazioni in modalità carattere (applicazioni che non forniscono una propria interfaccia utente grafica).

Le funzioni console consentono diversi livelli di accesso a una console. Le funzioni di I/O della console di alto livello consentono a un'applicazione di leggere da input standard per recuperare l'input da tastiera archiviato nel buffer di input di una console. Le funzioni consentono anche a un'applicazione di scrivere nell'output standard o in un errore standard per visualizzare il testo nel buffer dello schermo della console. Le funzioni di alto livello supportano anche il reindirizzamento degli handle standard e il controllo delle modalità console per le diverse funzionalità di I/O. Le funzioni di I/O della console di basso livello consentono alle applicazioni di ricevere input dettagliati sugli eventi di tastiera e mouse, nonché gli eventi che coinvolgono interazioni utente con la finestra della console. Le funzioni di basso livello consentono inoltre un maggiore controllo dell'output sullo schermo.

Questa panoramica descrive il supporto per le applicazioni in modalità carattere.

- [Informazioni sulle console](about-character-mode-applications.md)
- [Uso della console](using-the-console.md)
- [Riferimento alla console](console-reference.md)
