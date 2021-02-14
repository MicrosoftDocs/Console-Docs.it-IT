---
title: Gruppi di processi console
description: Quando un processo usa la funzione CreateProcess per creare un nuovo processo console, può specificare il flag crea \_ nuovo \_ \_ gruppo di processi per rendere il nuovo processo il processo radice di un gruppo di processi console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358101"
---
# <a name="console-process-groups"></a><span data-ttu-id="061f8-104">Gruppi di processi console</span><span class="sxs-lookup"><span data-stu-id="061f8-104">Console Process Groups</span></span>

<span data-ttu-id="061f8-105">Quando un processo usa la funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) per creare un nuovo processo console, può specificare il flag **Crea \_ nuovo \_ \_ gruppo di processi** per rendere il nuovo processo il processo radice di un gruppo di processi console.</span><span class="sxs-lookup"><span data-stu-id="061f8-105">When a process uses the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="061f8-106">Il gruppo di processi include tutti i processi discendenti dal processo radice.</span><span class="sxs-lookup"><span data-stu-id="061f8-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="061f8-107">Un processo può utilizzare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale CTRL + C o Ctrl + Break a tutti i processi in un gruppo di processi della console.</span><span class="sxs-lookup"><span data-stu-id="061f8-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="061f8-108">Il segnale viene ricevuto solo da quei processi del gruppo collegati alla stessa console del processo che ha chiamato **GenerateConsoleCtrlEvent**.</span><span class="sxs-lookup"><span data-stu-id="061f8-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.</span></span>