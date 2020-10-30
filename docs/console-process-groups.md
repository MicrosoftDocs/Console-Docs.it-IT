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
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038449"
---
# <a name="console-process-groups"></a>Gruppi di processi console

Quando un processo usa la funzione [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) per creare un nuovo processo console, può specificare il flag **Crea \_ nuovo \_ \_ gruppo di processi** per rendere il nuovo processo il processo radice di un gruppo di processi console. Il gruppo di processi include tutti i processi discendenti dal processo radice.

Un processo può utilizzare la funzione [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) per inviare un segnale CTRL + C o Ctrl + Break a tutti i processi in un gruppo di processi della console. Il segnale viene ricevuto solo da quei processi del gruppo collegati alla stessa console del processo che ha chiamato **GenerateConsoleCtrlEvent** .
