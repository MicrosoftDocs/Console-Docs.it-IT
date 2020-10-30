---
title: Pseudoconsoles-desktop di Windows
description: Un pseudoconsole è un concetto usato per fornire l'aspetto di hosting o manutenzione di un'applicazione in modalità carattere.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039479"
---
# <a name="pseudoconsoles"></a><span data-ttu-id="c040d-104">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="c040d-104">Pseudoconsoles</span></span>

<span data-ttu-id="c040d-105">Un *pseudoconsole* è un tipo di dispositivo che consente alle applicazioni di diventare l'host per le applicazioni in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="c040d-105">A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications.</span></span>

<span data-ttu-id="c040d-106">Questo è contrario a una tipica sessione della console in cui il sistema operativo creerà una finestra di hosting per conto dell'applicazione in modalità carattere per gestire l'output grafico e l'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c040d-106">This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.</span></span>

<span data-ttu-id="c040d-107">Con pseudoconsole, la finestra di hosting non viene creata.</span><span class="sxs-lookup"><span data-stu-id="c040d-107">With a pseudoconsole, the hosting window is not created.</span></span> <span data-ttu-id="c040d-108">L'applicazione che rende pseudoconsole deve essere responsabile della visualizzazione dell'output grafico e della raccolta dell'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c040d-108">The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input.</span></span> <span data-ttu-id="c040d-109">In alternativa, le informazioni possono essere inoltrate ulteriormente a un'altra applicazione responsabile di queste attività in un punto successivo della catena.</span><span class="sxs-lookup"><span data-stu-id="c040d-109">Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.</span></span>

<span data-ttu-id="c040d-110">Questa funzionalità è progettata per le applicazioni di terze parti "finestra del terminale" da esistere sulla piattaforma o per il reindirizzamento delle attività in modalità carattere a una sessione remota di "finestra del terminale" in un altro computer o anche in un'altra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="c040d-110">This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.</span></span>

<span data-ttu-id="c040d-111">Si noti che la sessione della console sottostante verrà comunque creata per conto dell'applicazione che richiede la pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="c040d-111">Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole.</span></span> <span data-ttu-id="c040d-112">Tutte le regole delle [sessioni della console](consoles.md) sono comunque valide, inclusa la possibilità per la connessione di più applicazioni in modalità carattere client alla sessione.</span><span class="sxs-lookup"><span data-stu-id="c040d-112">All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.</span></span>

<span data-ttu-id="c040d-113">Per garantire la massima compatibilità con il mondo esistente della funzionalità pseudoterminal, le informazioni fornite sul canale pseudoconsole verranno sempre codificate in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c040d-113">To provide maximum compatibility with the existing world of pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8.</span></span> <span data-ttu-id="c040d-114">Questa operazione non influisce sulla tabella codici o sulla codifica delle applicazioni client associate.</span><span class="sxs-lookup"><span data-stu-id="c040d-114">This does not affect the codepage or encoding of the client applications that are attached.</span></span> <span data-ttu-id="c040d-115">Se necessario, la traduzione si verificherà all'interno del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="c040d-115">Translation will happen inside the pseudoconsole system as necessary.</span></span>

<span data-ttu-id="c040d-116">Un esempio di introduzione è disponibile in [creazione di una sessione Pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="c040d-116">An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<span data-ttu-id="c040d-117">Altre informazioni complementari su pseudoconsoles sono disponibili nel post di Blog relativo all'annuncio: [riga di comando di Windows: Introduzione alla pseudo console di Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="c040d-117">Some additional background information on pseudoconsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>
