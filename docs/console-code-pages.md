---
title: Tabelle codici della console
description: Una tabella codici è un mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: 0ab9152c2be3f7487f43aee2a0a5c19766a433be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358251"
---
# <a name="console-code-pages"></a>Tabelle codici della console

Una *tabella codici* è un mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.

Associate a ogni console sono due tabelle codici: una per l'input e una per l'output. Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente. Usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console. Un'applicazione può utilizzare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) per impostare e recuperare le tabelle codici di input di una console e le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) per impostare e recuperare le tabelle codici di output.

Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati nel registro di sistema con la seguente chiave: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Per informazioni sull'utilizzo delle funzioni del registro di sistema per determinare le tabelle codici disponibili, vedere [**Registro di sistema**](/windows/win32/sysinfo/registry).

> [!TIP]
> Per tutte le applicazioni da riga di comando nuove e aggiornate è consigliabile evitare le tabelle codici e utilizzare **[Unicode](/windows/win32/intl/unicode)**. Il testo in formato UTF-16 può essere inviato *alla famiglia* di API della console. Il testo formattato UTF-8 può essere inviato a *una* famiglia di API console dopo aver verificato che la tabella codici sia impostata per la prima volta su **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** con le funzioni [**SetConsoleCP**](setconsolecp.md) e [**SetConsoleOutputCP**](setconsoleoutputcp.md) .