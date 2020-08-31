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
# <a name="console-code-pages"></a><span data-ttu-id="916e8-105">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="916e8-105">Console Code Pages</span></span>


<span data-ttu-id="916e8-106">Una *tabella codici* è un mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="916e8-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="916e8-107">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="916e8-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="916e8-108">Associate a ogni console sono due tabelle codici: una per l'input e una per l'output.</span><span class="sxs-lookup"><span data-stu-id="916e8-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="916e8-109">Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.</span><span class="sxs-lookup"><span data-stu-id="916e8-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="916e8-110">Usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="916e8-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="916e8-111">Un'applicazione può utilizzare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) per impostare e recuperare le tabelle codici di input di una console e le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) per impostare e recuperare le tabelle codici di output.</span><span class="sxs-lookup"><span data-stu-id="916e8-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="916e8-112">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati nel registro di sistema con la chiave seguente.</span><span class="sxs-lookup"><span data-stu-id="916e8-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key.</span></span>

<span data-ttu-id="916e8-113">**Tabella \_ \_ \\ \\ \\ codici NLS del controllo CurrentControlSet \\ di HKEY Local Machine System \\**</span><span class="sxs-lookup"><span data-stu-id="916e8-113">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="916e8-114">Per informazioni sull'utilizzo delle funzioni del registro di sistema per determinare le tabelle codici disponibili, vedere [**Registro di sistema**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span><span class="sxs-lookup"><span data-stu-id="916e8-114">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

 

 




