---
title: Tabelle codici della console
description: Una tabella codici è un mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: cacc4cb1d88a7d2aa01c35e0f0d94b44c393d28c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060145"
---
# <a name="console-code-pages"></a>Tabelle codici della console


Una *tabella codici* è un mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.

Associate a ogni console sono due tabelle codici: una per l'input e una per l'output. Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente. Usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console. Un'applicazione può utilizzare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) per impostare e recuperare le tabelle codici di input di una console e le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) per impostare e recuperare le tabelle codici di output.

Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati nel registro di sistema con la chiave seguente.

**Tabella \_ \_ \\ \\ \\ codici NLS del controllo CurrentControlSet \\ di HKEY Local Machine System \\**

Per informazioni sull'utilizzo delle funzioni del registro di sistema per determinare le tabelle codici disponibili, vedere [**Registro di sistema**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

 

 




