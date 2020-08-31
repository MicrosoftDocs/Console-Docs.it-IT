---
title: Gruppi di processi console
description: Quando un processo usa la funzione CreateProcess per creare un nuovo processo console, può specificare il flag crea \_ nuovo \_ \_ gruppo di processi per rendere il nuovo processo il processo radice di un gruppo di processi console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 467959e651f7e0806742ca3920ca0d441d5543cc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060089"
---
# <a name="console-process-groups"></a><span data-ttu-id="ede4d-104">Gruppi di processi console</span><span class="sxs-lookup"><span data-stu-id="ede4d-104">Console Process Groups</span></span>


<span data-ttu-id="ede4d-105">Quando un processo usa la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) per creare un nuovo processo console, può specificare il flag **Crea \_ nuovo \_ \_ gruppo di processi** per rendere il nuovo processo il processo radice di un gruppo di processi console.</span><span class="sxs-lookup"><span data-stu-id="ede4d-105">When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="ede4d-106">Il gruppo di processi include tutti i processi discendenti dal processo radice.</span><span class="sxs-lookup"><span data-stu-id="ede4d-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="ede4d-107">Un processo può utilizzare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale CTRL + C o Ctrl + Break a tutti i processi in un gruppo di processi della console.</span><span class="sxs-lookup"><span data-stu-id="ede4d-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="ede4d-108">Il segnale viene ricevuto solo da quei processi del gruppo collegati alla stessa console del processo che ha chiamato **GenerateConsoleCtrlEvent**.</span><span class="sxs-lookup"><span data-stu-id="ede4d-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.</span></span>

 

 




