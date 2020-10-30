---
title: Console-desktop di Windows
description: Una console è un'applicazione che fornisce I/O alle applicazioni della riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039119"
---
# <a name="consoles"></a><span data-ttu-id="13bbf-104">Console</span><span class="sxs-lookup"><span data-stu-id="13bbf-104">Consoles</span></span>

<span data-ttu-id="13bbf-105">Una *console* è un'applicazione che fornisce servizi di I/O alle applicazioni in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="13bbf-105">A *console* is an application that provides I/O services to character-mode applications.</span></span>

<span data-ttu-id="13bbf-106">Una console di è costituita da un buffer di input e uno o più buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="13bbf-106">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="13bbf-107">Il *buffer di input* contiene una coda di record di input, ognuno dei quali contiene informazioni su un evento di input.</span><span class="sxs-lookup"><span data-stu-id="13bbf-107">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="13bbf-108">La coda di input include sempre gli eventi chiave-pressione e rilascio chiave.</span><span class="sxs-lookup"><span data-stu-id="13bbf-108">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="13bbf-109">Può inoltre includere eventi del mouse (movimenti del puntatore e pressioni e versioni dei pulsanti) ed eventi durante i quali le azioni utente influiscono sulle dimensioni del buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="13bbf-109">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="13bbf-110">Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="13bbf-110">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="13bbf-111">Un qualsiasi numero di processi può condividere una console.</span><span class="sxs-lookup"><span data-stu-id="13bbf-111">Any number of processes can share a console.</span></span>

> [!TIP]
><span data-ttu-id="13bbf-112">Una concezione più ampia delle console e del modo in cui sono correlate ai terminali e alle applicazioni client da riga di comando sono reperibili nella Guida di **[orientamento dell'ecosistema](ecosystem-roadmap.md)** .</span><span class="sxs-lookup"><span data-stu-id="13bbf-112">A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

- [<span data-ttu-id="13bbf-113">Creazione di una console</span><span class="sxs-lookup"><span data-stu-id="13bbf-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="13bbf-114">Collegamento a una console</span><span class="sxs-lookup"><span data-stu-id="13bbf-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="13bbf-115">Chiusura di una console</span><span class="sxs-lookup"><span data-stu-id="13bbf-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="13bbf-116">Handle della console</span><span class="sxs-lookup"><span data-stu-id="13bbf-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="13bbf-117">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="13bbf-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="13bbf-118">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="13bbf-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="13bbf-119">Dimensioni del buffer della finestra e dello schermo</span><span class="sxs-lookup"><span data-stu-id="13bbf-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="13bbf-120">Selezione nella console</span><span class="sxs-lookup"><span data-stu-id="13bbf-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="13bbf-121">Scorrimento del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="13bbf-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
