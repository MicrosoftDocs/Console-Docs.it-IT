---
title: Pseudoconsoles-desktop di Windows
description: Un pseudoconsole è un concetto usato per fornire l'aspetto di hosting o manutenzione di un'applicazione in modalità carattere.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
ms.openlocfilehash: ce2dfb14371e35a738e9c42ba2be8d2bb2758946
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059569"
---
# <a name="pseudoconsoles"></a>Pseudoconsoles

Un *pseudoconsole* è un tipo di dispositivo che consente alle applicazioni di diventare l'host per le applicazioni in modalità carattere. 

Questo è contrario a una tipica sessione della console in cui il sistema operativo creerà una finestra di hosting per conto dell'applicazione in modalità carattere per gestire l'output grafico e l'input dell'utente.

Con pseudoconsole, la finestra di hosting non viene creata. L'applicazione che rende pseudoconsole deve essere responsabile della visualizzazione dell'output grafico e della raccolta dell'input dell'utente. In alternativa, le informazioni possono essere inoltrate ulteriormente a un'altra applicazione responsabile di queste attività in un punto successivo della catena.

Questa funzionalità è progettata per le applicazioni di terze parti "finestra del terminale" da esistere sulla piattaforma o per il reindirizzamento delle attività in modalità carattere a una sessione remota di "finestra del terminale" in un altro computer o anche in un'altra piattaforma.

Si noti che la sessione della console sottostante verrà comunque creata per conto dell'applicazione che richiede la pseudoconsole. Tutte le regole delle [sessioni della console](consoles.md) sono comunque valide, inclusa la possibilità per la connessione di più applicazioni in modalità carattere client alla sessione.

Per garantire la massima compatibilità con il mondo esistente della funzionalità pseudoterminal, le informazioni fornite sul canale pseudoconsole verranno sempre codificate in UTF-8. Questa operazione non influisce sulla tabella codici o sulla codifica delle applicazioni client associate. Se necessario, la traduzione si verificherà all'interno del sistema pseudoconsole.

Un esempio di introduzione è disponibile in [creazione di una sessione Pseudoconsole](creating-a-pseudoconsole-session.md).

Altre informazioni complementari su pseudoconsoles sono disponibili nel post di Blog relativo all'annuncio: [riga di comando di Windows: Introduzione alla pseudo console di Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).
