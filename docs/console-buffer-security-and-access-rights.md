---
title: Diritti di accesso e sicurezza del buffer della console
description: Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console. Per altre informazioni sulla sicurezza, vedere modello di controllo di accesso.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060161"
---
# <a name="console-buffer-security-and-access-rights"></a>Diritti di accesso e sicurezza del buffer della console


Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console. Per altre informazioni sulla sicurezza, vedere [modello di controllo di accesso](https://msdn.microsoft.com/library/windows/desktop/aa374876).

È possibile specificare un [descrittore di sicurezza](https://msdn.microsoft.com/library/windows/desktop/aa379563) per i buffer di input della console e dello schermo della console quando si chiama la funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Se si specifica **null**, l'oggetto ottiene un descrittore di sicurezza predefinito. Gli ACL nel descrittore di sicurezza predefinito per un buffer della console provengono dal token primario o di rappresentazione del creatore.

Gli handle restituiti da [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)e [**GetStdHandle**](getstdhandle.md) dispongono dei diritti di accesso di ** \_ lettura** e ** \_ scrittura** generici.

I diritti di accesso validi includono i [diritti di accesso](https://msdn.microsoft.com/library/windows/desktop/aa446632)generico di ** \_ lettura** e ** \_ scrittura** generica.


| valore                            | Significato                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **Generic \_ LETTURA** (0x80000000L)  | Richiede l'accesso in lettura al buffer dello schermo della console, consentendo al processo di leggere i dati dal buffer. |
| **Generic \_ SCRITTURA** (0x40000000L) | Richiede l'accesso in scrittura al buffer dello schermo della console, consentendo al processo di scrivere i dati nel buffer. |










