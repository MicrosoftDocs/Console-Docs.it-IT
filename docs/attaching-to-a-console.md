---
title: Collegamento a una console
description: Un processo può usare la funzione AttachConsole per connettersi a una console. Un processo può essere collegato a una console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037459"
---
# <a name="attaching-to-a-console"></a>Collegamento a una console

Un processo può usare la funzione [**AttachConsole**](attachconsole.md) per connettersi a una console come client. Un processo può essere collegato a una console.

A una console possono essere collegati molti processi. Per recuperare un elenco dei processi collegati a una console, chiamare la funzione [**GetConsoleProcessList**](getconsoleprocesslist.md) .

Per connettersi come server, vedere informazioni su [**Pseudoconsoles**](pseudoconsoles.md).
