---
title: CTRL + segnale di chiusura
description: Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: a44f54e5c73c77155d4aa1d8307375c176463a49
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059889"
---
# <a name="ctrlclose-signal"></a>CTRL + segnale di chiusura


Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console. Tutti i processi collegati alla console ricevono il segnale, assegnando a ogni processo la possibilità di eseguire la pulizia prima della terminazione. Quando un processo riceve questo segnale, la funzione handler può eseguire una delle azioni seguenti dopo l'esecuzione di qualsiasi operazione di pulizia:

- Chiamare [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) per terminare il processo.
- Restituisce **false**. Se nessuna delle funzioni del gestore registrate restituisce **true**, il gestore predefinito termina il processo.
- Restituisce **true**. In questo caso, non vengono chiamate altre funzioni del gestore e il processo viene terminato.

 

 




