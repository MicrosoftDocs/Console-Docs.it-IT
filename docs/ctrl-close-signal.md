---
title: CTRL + segnale di chiusura
description: Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: d3775bf0b8536fc531905ee6665a1e2c294d0a68
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038229"
---
# <a name="ctrlclose-signal"></a>CTRL + segnale di chiusura

Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console. Tutti i processi collegati alla console ricevono il segnale, assegnando a ogni processo la possibilità di eseguire la pulizia prima della terminazione. Quando un processo riceve questo segnale, la funzione handler può eseguire una delle azioni seguenti dopo l'esecuzione di qualsiasi operazione di pulizia:

- Chiamare [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) per terminare il processo.
- Restituisce **false** . Se nessuna delle funzioni del gestore registrate restituisce **true** , il gestore predefinito termina il processo.
- Restituisce **true** . In questo caso, non vengono chiamate altre funzioni del gestore e il processo viene terminato.
