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
# <a name="ctrlclose-signal"></a><span data-ttu-id="af40c-104">CTRL + segnale di chiusura</span><span class="sxs-lookup"><span data-stu-id="af40c-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="af40c-105">Il sistema genera un segnale CTRL + CLOSE quando l'utente chiude una console.</span><span class="sxs-lookup"><span data-stu-id="af40c-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="af40c-106">Tutti i processi collegati alla console ricevono il segnale, assegnando a ogni processo la possibilità di eseguire la pulizia prima della terminazione.</span><span class="sxs-lookup"><span data-stu-id="af40c-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="af40c-107">Quando un processo riceve questo segnale, la funzione handler può eseguire una delle azioni seguenti dopo l'esecuzione di qualsiasi operazione di pulizia:</span><span class="sxs-lookup"><span data-stu-id="af40c-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="af40c-108">Chiamare [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) per terminare il processo.</span><span class="sxs-lookup"><span data-stu-id="af40c-108">Call [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) to terminate the process.</span></span>
- <span data-ttu-id="af40c-109">Restituisce **false**.</span><span class="sxs-lookup"><span data-stu-id="af40c-109">Return **FALSE**.</span></span> <span data-ttu-id="af40c-110">Se nessuna delle funzioni del gestore registrate restituisce **true**, il gestore predefinito termina il processo.</span><span class="sxs-lookup"><span data-stu-id="af40c-110">If none of the registered handler functions returns **TRUE**, the default handler terminates the process.</span></span>
- <span data-ttu-id="af40c-111">Restituisce **true**.</span><span class="sxs-lookup"><span data-stu-id="af40c-111">Return **TRUE**.</span></span> <span data-ttu-id="af40c-112">In questo caso, non vengono chiamate altre funzioni del gestore e il processo viene terminato.</span><span class="sxs-lookup"><span data-stu-id="af40c-112">In this case, no other handler functions are called and the process terminates.</span></span>