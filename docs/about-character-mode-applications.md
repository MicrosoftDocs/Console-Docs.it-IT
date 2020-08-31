---
title: Informazioni sulle console
description: Le console di offrono un supporto di alto livello per le applicazioni in modalità carattere semplici che interagiscono con l'utente utilizzando le funzioni che leggono dall'input standard e scrivono in output standard o errore standard.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060249"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="ad314-104">Informazioni sulle applicazioni in modalità carattere</span><span class="sxs-lookup"><span data-stu-id="ad314-104">About Character Mode Applications</span></span>

<span data-ttu-id="ad314-105">Applicazioni in modalità carattere (o "riga di comando"):</span><span class="sxs-lookup"><span data-stu-id="ad314-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="ad314-106">Facoltativamente Leggere i dati dall'input standard (stdin)</span><span class="sxs-lookup"><span data-stu-id="ad314-106">[Optionally] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="ad314-107">"Lavoro"</span><span class="sxs-lookup"><span data-stu-id="ad314-107">Do "work"</span></span>
3. <span data-ttu-id="ad314-108">Facoltativamente Scrivere dati in output standard (stdout) o errore standard (stderr)</span><span class="sxs-lookup"><span data-stu-id="ad314-108">[Optionally] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="ad314-109">Le applicazioni in modalità carattere comunicano con l'utente finale tramite un'applicazione "console" (o "terminale").</span><span class="sxs-lookup"><span data-stu-id="ad314-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="ad314-110">Una console converte l'input dell'utente da tastiera, mouse, touch screen, penna e così via e lo invia a un stdin dell'applicazione in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="ad314-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="ad314-111">Una console può anche visualizzare l'output di testo di un'applicazione in modalità carattere sullo schermo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ad314-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="ad314-112">In Windows la console è incorporata e fornisce un'API avanzata tramite cui le applicazioni in modalità carattere possono interagire con l'utente.</span><span class="sxs-lookup"><span data-stu-id="ad314-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span>

- [<span data-ttu-id="ad314-113">Console</span><span class="sxs-lookup"><span data-stu-id="ad314-113">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="ad314-114">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="ad314-114">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="ad314-115">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="ad314-115">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="ad314-116">Gestori di controlli console</span><span class="sxs-lookup"><span data-stu-id="ad314-116">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="ad314-117">Alias di console</span><span class="sxs-lookup"><span data-stu-id="ad314-117">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="ad314-118">Diritti di accesso e sicurezza del buffer della console</span><span class="sxs-lookup"><span data-stu-id="ad314-118">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="ad314-119">Problemi delle applicazioni console</span><span class="sxs-lookup"><span data-stu-id="ad314-119">Console Application Issues</span></span>](console-application-issues.md)

 

 




