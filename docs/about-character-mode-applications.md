---
title: Informazioni sulle console
description: Le console di offrono un supporto di alto livello per le applicazioni in modalità carattere semplici che interagiscono con l'utente utilizzando le funzioni che leggono dall'input standard e scrivono in output standard o errore standard.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037529"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="8d573-104">Informazioni sulle applicazioni in modalità carattere</span><span class="sxs-lookup"><span data-stu-id="8d573-104">About Character Mode Applications</span></span>

<span data-ttu-id="8d573-105">Applicazioni in modalità carattere (o "riga di comando"):</span><span class="sxs-lookup"><span data-stu-id="8d573-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="8d573-106">\[Facoltativamente \] , leggere i dati dall'input standard (stdin)</span><span class="sxs-lookup"><span data-stu-id="8d573-106">\[Optionally\] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="8d573-107">"Lavoro"</span><span class="sxs-lookup"><span data-stu-id="8d573-107">Do "work"</span></span>
3. <span data-ttu-id="8d573-108">\[Facoltativamente \] , scrivere i dati nell'output standard (stdout) o nell'errore standard (stderr)</span><span class="sxs-lookup"><span data-stu-id="8d573-108">\[Optionally\] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="8d573-109">Le applicazioni in modalità carattere comunicano con l'utente finale tramite un'applicazione "console" (o "terminale").</span><span class="sxs-lookup"><span data-stu-id="8d573-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="8d573-110">Una console converte l'input dell'utente da tastiera, mouse, touch screen, penna e così via e lo invia a un stdin dell'applicazione in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="8d573-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="8d573-111">Una console può anche visualizzare l'output di testo di un'applicazione in modalità carattere sullo schermo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8d573-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="8d573-112">In Windows la console è incorporata e fornisce un'API avanzata tramite cui le applicazioni in modalità carattere possono interagire con l'utente.</span><span class="sxs-lookup"><span data-stu-id="8d573-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span> <span data-ttu-id="8d573-113">Tuttavia, nell'era recente, il team di console sta incoraggiando tutte le applicazioni in modalità carattere da sviluppare con le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) tramite le chiamate API classiche per la massima compatibilità tra Windows e altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="8d573-113">However, in the recent era, the console team is encouraging all character mode applications to be developed with [virtual terminal sequences](console-virtual-terminal-sequences.md) over the classic API calls for maximum compatibility between Windows and other operating systems.</span></span> <span data-ttu-id="8d573-114">Altre informazioni su questa transizione e sui compromessi sono disponibili nella discussione sulle [API classiche rispetto alle sequenze di terminali virtuali](classic-vs-vt.md).</span><span class="sxs-lookup"><span data-stu-id="8d573-114">More details on this transition and the trade offs involved can be found in our discussion of [classic APIs versus virtual terminal sequences](classic-vs-vt.md).</span></span>

- [<span data-ttu-id="8d573-115">Console</span><span class="sxs-lookup"><span data-stu-id="8d573-115">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="8d573-116">Metodi di input e output</span><span class="sxs-lookup"><span data-stu-id="8d573-116">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="8d573-117">Tabelle codici della console</span><span class="sxs-lookup"><span data-stu-id="8d573-117">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="8d573-118">Gestori di controllo della console</span><span class="sxs-lookup"><span data-stu-id="8d573-118">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="8d573-119">Alias di console</span><span class="sxs-lookup"><span data-stu-id="8d573-119">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="8d573-120">Sicurezza dei buffer della console e diritti di accesso</span><span class="sxs-lookup"><span data-stu-id="8d573-120">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="8d573-121">Problemi relativi alle applicazioni console</span><span class="sxs-lookup"><span data-stu-id="8d573-121">Console Application Issues</span></span>](console-application-issues.md)
