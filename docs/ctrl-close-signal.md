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
# <a name="ctrlclose-signal"></a><span data-ttu-id="07bea-104">CTRL + segnale di chiusura</span><span class="sxs-lookup"><span data-stu-id="07bea-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="07bea-105">Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console.</span><span class="sxs-lookup"><span data-stu-id="07bea-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="07bea-106">Tutti i processi collegati alla console ricevono il segnale, assegnando a ogni processo la possibilità di eseguire la pulizia prima della terminazione.</span><span class="sxs-lookup"><span data-stu-id="07bea-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="07bea-107">Quando un processo riceve questo segnale, la funzione handler può eseguire una delle azioni seguenti dopo l'esecuzione di qualsiasi operazione di pulizia:</span><span class="sxs-lookup"><span data-stu-id="07bea-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="07bea-108">Chiamare [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) per terminare il processo.</span><span class="sxs-lookup"><span data-stu-id="07bea-108">Call [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) to terminate the process.</span></span>
- <span data-ttu-id="07bea-109">Restituisce **false** .</span><span class="sxs-lookup"><span data-stu-id="07bea-109">Return **FALSE** .</span></span> <span data-ttu-id="07bea-110">Se nessuna delle funzioni del gestore registrate restituisce **true** , il gestore predefinito termina il processo.</span><span class="sxs-lookup"><span data-stu-id="07bea-110">If none of the registered handler functions returns **TRUE** , the default handler terminates the process.</span></span>
- <span data-ttu-id="07bea-111">Restituisce **true** .</span><span class="sxs-lookup"><span data-stu-id="07bea-111">Return **TRUE** .</span></span> <span data-ttu-id="07bea-112">In questo caso, non vengono chiamate altre funzioni del gestore e il processo viene terminato.</span><span class="sxs-lookup"><span data-stu-id="07bea-112">In this case, no other handler functions are called and the process terminates.</span></span>
