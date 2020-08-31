---
title: Console
description: Le console di gestiscono l'input e l'output (I/O) per le applicazioni in modalità carattere (applicazioni che non forniscono una propria interfaccia utente grafica).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 99f351efbf6b68733b5c3e7b94cee03708d6cbef
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060204"
---
# <a name="consoles"></a><span data-ttu-id="691f2-104">Console</span><span class="sxs-lookup"><span data-stu-id="691f2-104">Consoles</span></span>


<span data-ttu-id="691f2-105">Le console di gestiscono l'input e l'output (I/O) per le applicazioni in modalità carattere (applicazioni che non forniscono una propria interfaccia utente grafica).</span><span class="sxs-lookup"><span data-stu-id="691f2-105">Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).</span></span>

<span data-ttu-id="691f2-106">Le funzioni console consentono diversi livelli di accesso a una console.</span><span class="sxs-lookup"><span data-stu-id="691f2-106">The console functions enable different levels of access to a console.</span></span> <span data-ttu-id="691f2-107">Le funzioni di I/O della console di alto livello consentono a un'applicazione di leggere da input standard per recuperare l'input da tastiera archiviato nel buffer di input di una console.</span><span class="sxs-lookup"><span data-stu-id="691f2-107">The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer.</span></span> <span data-ttu-id="691f2-108">Le funzioni consentono anche a un'applicazione di scrivere nell'output standard o in un errore standard per visualizzare il testo nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="691f2-108">The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer.</span></span> <span data-ttu-id="691f2-109">Le funzioni di alto livello supportano anche il reindirizzamento degli handle standard e il controllo delle modalità console per le diverse funzionalità di I/O.</span><span class="sxs-lookup"><span data-stu-id="691f2-109">The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality.</span></span> <span data-ttu-id="691f2-110">Le funzioni di I/O della console di basso livello consentono alle applicazioni di ricevere input dettagliati sugli eventi di tastiera e mouse, nonché gli eventi che coinvolgono interazioni utente con la finestra della console.</span><span class="sxs-lookup"><span data-stu-id="691f2-110">The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window.</span></span> <span data-ttu-id="691f2-111">Le funzioni di basso livello consentono inoltre un maggiore controllo dell'output sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="691f2-111">The low-level functions also enable greater control of output to the screen.</span></span>

<span data-ttu-id="691f2-112">Questa panoramica descrive il supporto per le applicazioni in modalità carattere.</span><span class="sxs-lookup"><span data-stu-id="691f2-112">This overview describes support for character-mode applications.</span></span>

- [<span data-ttu-id="691f2-113">Informazioni sulle console</span><span class="sxs-lookup"><span data-stu-id="691f2-113">About Consoles</span></span>](about-character-mode-applications.md)
- [<span data-ttu-id="691f2-114">Uso della console</span><span class="sxs-lookup"><span data-stu-id="691f2-114">Using the Console</span></span>](using-the-console.md)
- [<span data-ttu-id="691f2-115">Riferimento alla console</span><span class="sxs-lookup"><span data-stu-id="691f2-115">Console Reference</span></span>](console-reference.md)

 

 




