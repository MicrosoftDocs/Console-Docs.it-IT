---
title: Sicurezza dei buffer della console e diritti di accesso
description: Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console. Per ulteriori informazioni sulla sicurezza, vedere Access-Control Model.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: dfafdbd59c2b06929c35612d7dcf03b24439eba2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93036979"
---
# <a name="console-buffer-security-and-access-rights"></a>Sicurezza dei buffer della console e diritti di accesso

Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console. Per altre informazioni sulla sicurezza, vedere [modello di controllo di accesso](https://msdn.microsoft.com/library/windows/desktop/aa374876).

## <a name="console-object-security-descriptors"></a>Descrittori di sicurezza oggetto console

È possibile specificare un [descrittore di sicurezza](https://msdn.microsoft.com/library/windows/desktop/aa379563) per i buffer di input della console e dello schermo della console quando si chiama la funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Se si specifica **null** , l'oggetto ottiene un descrittore di sicurezza predefinito. Gli ACL nel descrittore di sicurezza predefinito per un buffer della console provengono dal token primario o di rappresentazione del creatore.

Gli handle restituiti da [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)e [**GetStdHandle**](getstdhandle.md) dispongono dei diritti di accesso di **\_ lettura** e **\_ scrittura** generici.

I diritti di accesso validi includono i [diritti di accesso](https://msdn.microsoft.com/library/windows/desktop/aa446632)generico di **\_ lettura** e **\_ scrittura** generica.

| Valore | Significato |
|-|-|
| **Generic \_ LETTURA** (0x80000000L)  | Richiede l'accesso in lettura al buffer dello schermo della console, consentendo al processo di leggere i dati dal buffer. |
| **Generic \_ SCRITTURA** (0x40000000L) | Richiede l'accesso in scrittura al buffer dello schermo della console, consentendo al processo di scrivere i dati nel buffer. |

> [!NOTE]
> **[Piattaforma UWP (Universal Windows Platform) le app console](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** e quelle con un **[livello di integrità](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** inferiore rispetto alla console collegata non saranno consentite sia per la lettura del buffer di output sia per la scrittura nel buffer di input anche se i descrittori di sicurezza sopra indicati normalmente lo consentiranno. Per ulteriori informazioni, vedere la discussione dei **[verbi in modo errato](#wrong-way-verbs)** .

## <a name="wrong-way-verbs"></a>Verbi Wrong-Way

Alcune operazioni sugli oggetti console verranno negate anche se l'oggetto dispone di un descrittore di sicurezza dichiarato per consentire in modo specifico la lettura o la scrittura. Questo riguarda specificamente le applicazioni da riga di comando in esecuzione in un contesto con privilegi ridotti che condividono una sessione della console creata da un'applicazione della riga di comando in un contesto più permissivo.

Il termine "verbi errati" deve essere applicato all'operazione che corrisponde al flusso normale per uno degli oggetti console. In particolare, viene scritto il flusso normale per il buffer di output e viene letto il flusso normale per il buffer di input. Il "errato" sarà quindi la lettura del buffer di output o la scrittura del buffer di input. Si tratta di funzioni descritte nella documentazione sulle **[funzioni di i/O della console di basso livello](low-level-console-i-o.md)** .

I due scenari in cui è possibile trovare sono i seguenti:

1. **[Piattaforma UWP (Universal Windows Platform) app console](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** . Poiché si tratta di cugini di altre applicazioni piattaforma UWP (Universal Windows Platform), gli utenti si aspettano che siano isolati da altre applicazioni e forniscano garanzie sugli effetti del loro funzionamento.
1. Qualsiasi applicazione console avviata intenzionalmente con un **[livello di integrità](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** inferiore rispetto alla sessione esistente, che può essere eseguita con l' **[assegnazione di etichette o la manipolazione dei token durante CreateProcess](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** .

Se viene rilevato uno di questi scenari, la console di applicherà il flag "verbi errati" alla connessione dell'applicazione della riga di comando e rifiuterà le chiamate alle API seguenti per ridurre la superficie di comunicazione tra i livelli:

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

Le chiamate rifiutate riceveranno un codice di errore di **accesso negato** , come se l'autorizzazione di lettura o scrittura venisse negata dai descrittori di sicurezza per l'oggetto.
