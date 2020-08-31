---
title: Alias di console
description: Vengono descritti gli alias della console e il modo in cui vengono usati per eseguire il mapping delle stringhe di origine alle stringhe di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: bce57b152262da06b1950eb3566ca8b67d0bb580
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060172"
---
# <a name="console-aliases"></a><span data-ttu-id="3ca7e-104">Alias di console</span><span class="sxs-lookup"><span data-stu-id="3ca7e-104">Console Aliases</span></span>


<span data-ttu-id="3ca7e-105">Gli alias di console vengono usati per eseguire il mapping di stringhe di origine alle stringhe di destinazione.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-105">Console aliases are used to map source strings to target strings.</span></span> <span data-ttu-id="3ca7e-106">Ad esempio, è possibile definire un alias console che esegue il mapping di "test" a "CD an \\ \_ \_ Long \_ path \\ test".</span><span class="sxs-lookup"><span data-stu-id="3ca7e-106">For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test".</span></span> <span data-ttu-id="3ca7e-107">Quando si digita "test" nella riga di comando, il sottosistema della console espande l'alias ed esegue il comando CD specificato.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-107">When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.</span></span>

<span data-ttu-id="3ca7e-108">Per definire un alias di console, usare Doskey.exe per creare una macro oppure usare la funzione [**AddConsoleAlias**](addconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="3ca7e-108">To define a console alias, use Doskey.exe to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function.</span></span> <span data-ttu-id="3ca7e-109">Nell'esempio seguente viene utilizzato Doskey.exe:</span><span class="sxs-lookup"><span data-stu-id="3ca7e-109">The following example uses Doskey.exe:</span></span>

<span data-ttu-id="3ca7e-110">**test DOSKEY = CD \\ \*\* \*\* \\ test** <em>di \_ \_ \_ percorso molto lungo</em></span><span class="sxs-lookup"><span data-stu-id="3ca7e-110">**doskey test=cd \\**<em>a\_very\_long\_path</em>**\\test**</span></span>

<span data-ttu-id="3ca7e-111">La chiamata seguente a [**AddConsoleAlias**](addconsolealias.md) crea lo stesso alias della console:</span><span class="sxs-lookup"><span data-stu-id="3ca7e-111">The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:</span></span>

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

<span data-ttu-id="3ca7e-112">Per aggiungere parametri a una macro alias console usando Doskey.exe, usare i parametri batch da $1 a $9.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-112">To add parameters to a console alias macro using Doskey.exe, use the batch parameters $1 through $9.</span></span> <span data-ttu-id="3ca7e-113">Per ulteriori informazioni sui codici speciali che possono essere utilizzati nelle definizioni delle macro DOSKEY, vedere la guida della riga di comando per Doskey.exe o [DOSKEY](https://go.microsoft.com/fwlink/p/?linkid=196265) in TechNet.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-113">For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for Doskey.exe or [Doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) on TechNet.</span></span>

<span data-ttu-id="3ca7e-114">Tutte le istanze di un file eseguibile in esecuzione nella stessa finestra della console condividono qualsiasi alias della console definito.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-114">All instances of an executable file running in the same console window share any defined console aliases.</span></span> <span data-ttu-id="3ca7e-115">Più istanze dello stesso file eseguibile in esecuzione in finestre della console diverse non condividono gli alias della console.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-115">Multiple instances of the same executable file running in different console windows do not share console aliases.</span></span> <span data-ttu-id="3ca7e-116">Diversi file eseguibili in esecuzione nella stessa finestra della console non condividono gli alias della console.</span><span class="sxs-lookup"><span data-stu-id="3ca7e-116">Different executable files running in the same console window do not share console aliases.</span></span>

<span data-ttu-id="3ca7e-117">Per recuperare la stringa di destinazione per una stringa di origine e un file eseguibile specificati, usare la funzione [**GetConsoleAlias**](getconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="3ca7e-117">To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function.</span></span> <span data-ttu-id="3ca7e-118">Per recuperare tutti gli alias per un file eseguibile specificato, utilizzare la funzione [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="3ca7e-118">To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span> <span data-ttu-id="3ca7e-119">Per recuperare i nomi di tutti gli alias per cui sono stati definiti gli alias della console, usare la funzione [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="3ca7e-119">To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

 

 




