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
# <a name="console-aliases"></a>Alias di console


Gli alias di console vengono usati per eseguire il mapping di stringhe di origine alle stringhe di destinazione. Ad esempio, è possibile definire un alias console che esegue il mapping di "test" a "CD an \\ \_ \_ Long \_ path \\ test". Quando si digita "test" nella riga di comando, il sottosistema della console espande l'alias ed esegue il comando CD specificato.

Per definire un alias di console, usare Doskey.exe per creare una macro oppure usare la funzione [**AddConsoleAlias**](addconsolealias.md) . Nell'esempio seguente viene utilizzato Doskey.exe:

**test DOSKEY = CD \\ ** ** \\ test** <em>di \_ \_ \_ percorso molto lungo</em>

La chiamata seguente a [**AddConsoleAlias**](addconsolealias.md) crea lo stesso alias della console:

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

Per aggiungere parametri a una macro alias console usando Doskey.exe, usare i parametri batch da $1 a $9. Per ulteriori informazioni sui codici speciali che possono essere utilizzati nelle definizioni delle macro DOSKEY, vedere la guida della riga di comando per Doskey.exe o [DOSKEY](https://go.microsoft.com/fwlink/p/?linkid=196265) in TechNet.

Tutte le istanze di un file eseguibile in esecuzione nella stessa finestra della console condividono qualsiasi alias della console definito. Più istanze dello stesso file eseguibile in esecuzione in finestre della console diverse non condividono gli alias della console. Diversi file eseguibili in esecuzione nella stessa finestra della console non condividono gli alias della console.

Per recuperare la stringa di destinazione per una stringa di origine e un file eseguibile specificati, usare la funzione [**GetConsoleAlias**](getconsolealias.md) . Per recuperare tutti gli alias per un file eseguibile specificato, utilizzare la funzione [**GetConsoleAliases**](getconsolealiases.md) . Per recuperare i nomi di tutti gli alias per cui sono stati definiti gli alias della console, usare la funzione [**GetConsoleAliasExes**](getconsolealiasexes.md) .

 

 




