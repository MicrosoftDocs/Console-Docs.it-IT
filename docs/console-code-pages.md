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
# <a name="console-code-pages"></a><span data-ttu-id="cb59f-105">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="cb59f-105">Console Code Pages</span></span>

<span data-ttu-id="cb59f-106">Una *tabella codici* è un mapping di 256 codici carattere a singoli caratteri.</span><span class="sxs-lookup"><span data-stu-id="cb59f-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="cb59f-107">Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.</span><span class="sxs-lookup"><span data-stu-id="cb59f-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="cb59f-108">Associate a ogni console sono due tabelle codici: una per l'input e una per l'output.</span><span class="sxs-lookup"><span data-stu-id="cb59f-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="cb59f-109">Una console di usa la relativa tabella codici di input per convertire l'input da tastiera nel valore del carattere corrispondente.</span><span class="sxs-lookup"><span data-stu-id="cb59f-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="cb59f-110">Usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="cb59f-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="cb59f-111">Un'applicazione può utilizzare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) per impostare e recuperare le tabelle codici di input di una console e le funzioni [**SetConsoleOutputCP**](setconsoleoutputcp.md) e [**GetConsoleOutputCP**](getconsoleoutputcp.md) per impostare e recuperare le tabelle codici di output.</span><span class="sxs-lookup"><span data-stu-id="cb59f-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="cb59f-112">Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati nel registro di sistema con la seguente chiave: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span><span class="sxs-lookup"><span data-stu-id="cb59f-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span></span>

<span data-ttu-id="cb59f-113">Per informazioni sull'utilizzo delle funzioni del registro di sistema per determinare le tabelle codici disponibili, vedere [**Registro di sistema**](/windows/win32/sysinfo/registry).</span><span class="sxs-lookup"><span data-stu-id="cb59f-113">For information about using the registry functions to determine the available code pages, see [**Registry**](/windows/win32/sysinfo/registry).</span></span>

> [!TIP]
> <span data-ttu-id="cb59f-114">Per tutte le applicazioni da riga di comando nuove e aggiornate è consigliabile evitare le tabelle codici e utilizzare **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="cb59f-114">It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="cb59f-115">Il testo in formato UTF-16 può essere inviato *alla famiglia* di API della console.</span><span class="sxs-lookup"><span data-stu-id="cb59f-115">UTF-16 formatted text can be sent to the *W* family of console APIs.</span></span> <span data-ttu-id="cb59f-116">Il testo formattato UTF-8 può essere inviato a *una* famiglia di API console dopo aver verificato che la tabella codici sia impostata per la prima volta su **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** con le funzioni [**SetConsoleCP**](setconsolecp.md) e [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="cb59f-116">UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.</span></span>