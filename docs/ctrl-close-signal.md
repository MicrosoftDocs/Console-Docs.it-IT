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
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357891"
---
# <a name="ctrlclose-signal"></a>CTRL + segnale di chiusura

Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console. Tutti i processi collegati alla console ricevono il segnale, assegnando a ogni processo la possibilità di eseguire la pulizia prima della terminazione. Quando un processo riceve questo segnale, la funzione handler può eseguire una delle azioni seguenti dopo l'esecuzione di qualsiasi operazione di pulizia:

- Chiamare [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) per terminare il processo.
- Restituisce **false**. Se nessuna delle funzioni del gestore registrate restituisce **true**, il gestore predefinito termina il processo.
- Restituisce **true**. In questo caso, non vengono chiamate altre funzioni del gestore e il processo viene terminato.