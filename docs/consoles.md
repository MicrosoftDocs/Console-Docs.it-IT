---
title: Console-desktop di Windows
description: Una console è un'applicazione che fornisce I/O alle applicazioni della riga di comando.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059945"
---
# <a name="consoles"></a><span data-ttu-id="ff398-104">Console</span><span class="sxs-lookup"><span data-stu-id="ff398-104">Consoles</span></span>

<span data-ttu-id="ff398-105">Una *console* (o *terminale*) è un'applicazione che fornisce I/O alle applicazioni in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="ff398-105">A *console* (or *terminal*) is an application that provides I/O to character-mode applications.</span></span> <span data-ttu-id="ff398-106">Questo meccanismo indipendente dal processore semplifica la portabilità delle applicazioni in modalità carattere esistenti o la creazione di nuovi strumenti e applicazioni in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="ff398-106">This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.</span></span>

<span data-ttu-id="ff398-107">Una console di è costituita da un buffer di input e uno o più buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="ff398-107">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="ff398-108">Il *buffer di input* contiene una coda di record di input, ognuno dei quali contiene informazioni su un evento di input.</span><span class="sxs-lookup"><span data-stu-id="ff398-108">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="ff398-109">La coda di input include sempre gli eventi chiave-pressione e rilascio chiave.</span><span class="sxs-lookup"><span data-stu-id="ff398-109">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="ff398-110">Può inoltre includere eventi del mouse (movimenti del puntatore e pressioni e versioni dei pulsanti) ed eventi durante i quali le azioni utente influiscono sulle dimensioni del buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="ff398-110">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="ff398-111">Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="ff398-111">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="ff398-112">Un qualsiasi numero di processi può condividere una console.</span><span class="sxs-lookup"><span data-stu-id="ff398-112">Any number of processes can share a console.</span></span>

- [<span data-ttu-id="ff398-113">Creazione di una console</span><span class="sxs-lookup"><span data-stu-id="ff398-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="ff398-114">Connessione a una console</span><span class="sxs-lookup"><span data-stu-id="ff398-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="ff398-115">Chiusura di una console</span><span class="sxs-lookup"><span data-stu-id="ff398-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="ff398-116">Handle della console</span><span class="sxs-lookup"><span data-stu-id="ff398-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="ff398-117">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="ff398-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="ff398-118">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="ff398-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="ff398-119">Dimensioni del buffer della finestra e dello schermo</span><span class="sxs-lookup"><span data-stu-id="ff398-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="ff398-120">Selezione della console</span><span class="sxs-lookup"><span data-stu-id="ff398-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="ff398-121">Scorrimento del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="ff398-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
