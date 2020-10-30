---
title: I/O console Low-Level
description: Le funzioni di I/O della console di basso livello espandono il controllo di un'applicazione sull'I/O della console consentendo l'accesso diretto ai buffer di input e dello schermo di una console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b4ec834e44f7ff291466cfe1714442bc17ca7aca
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039549"
---
# <a name="low-level-console-io"></a><span data-ttu-id="8f524-104">I/O console Low-Level</span><span class="sxs-lookup"><span data-stu-id="8f524-104">Low-Level Console I/O</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="8f524-105">Le funzioni di I/O della console di basso livello espandono il controllo di un'applicazione sull'I/O della console consentendo l'accesso diretto ai buffer di input e dello schermo di una console.</span><span class="sxs-lookup"><span data-stu-id="8f524-105">The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.</span></span> <span data-ttu-id="8f524-106">Queste funzioni consentono a un'applicazione di eseguire le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="8f524-106">These functions enable an application to perform the following tasks:</span></span>

- <span data-ttu-id="8f524-107">Ricevere input sugli eventi di ridimensionamento del mouse e del buffer</span><span class="sxs-lookup"><span data-stu-id="8f524-107">Receive input about mouse and buffer-resizing events</span></span>
- <span data-ttu-id="8f524-108">Ricevere informazioni estese sugli eventi di input da tastiera</span><span class="sxs-lookup"><span data-stu-id="8f524-108">Receive extended information about keyboard input events</span></span>
- <span data-ttu-id="8f524-109">Scrivere record di input nel buffer di input</span><span class="sxs-lookup"><span data-stu-id="8f524-109">Write input records to the input buffer</span></span>
- <span data-ttu-id="8f524-110">Legge i record di input senza rimuoverli dal buffer di input</span><span class="sxs-lookup"><span data-stu-id="8f524-110">Read input records without removing them from the input buffer</span></span>
- <span data-ttu-id="8f524-111">Determinare il numero di eventi in sospeso nel buffer di input</span><span class="sxs-lookup"><span data-stu-id="8f524-111">Determine the number of pending events in the input buffer</span></span>
- <span data-ttu-id="8f524-112">Svuotare il buffer di input</span><span class="sxs-lookup"><span data-stu-id="8f524-112">Flush the input buffer</span></span>
- <span data-ttu-id="8f524-113">Lettura e scrittura di stringhe di caratteri Unicode o ANSI in una posizione specificata in un buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="8f524-113">Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer</span></span>
- <span data-ttu-id="8f524-114">Lettura e scrittura di stringhe di testo e di attributi di colore di sfondo in una posizione specificata del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="8f524-114">Read and write strings of text and background color attributes at a specified screen buffer location</span></span>
- <span data-ttu-id="8f524-115">Lettura e scrittura di blocchi rettangolari di dati di tipo carattere e colore in una posizione specificata del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="8f524-115">Read and write rectangular blocks of character and color data at a specified screen buffer location</span></span>
- <span data-ttu-id="8f524-116">Scrivere un singolo carattere Unicode o ANSI o una combinazione di attributi di colore di sfondo e testo in un numero specificato di celle consecutive a partire da una posizione specificata del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="8f524-116">Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location</span></span>

<span data-ttu-id="8f524-117">Per altre informazioni, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="8f524-117">For more information, see the following topics:</span></span>

- [<span data-ttu-id="8f524-118">Modalità console</span><span class="sxs-lookup"><span data-stu-id="8f524-118">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="8f524-119">Modalità console di basso livello</span><span class="sxs-lookup"><span data-stu-id="8f524-119">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="8f524-120">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="8f524-120">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="8f524-121">Funzioni di output della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="8f524-121">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)
