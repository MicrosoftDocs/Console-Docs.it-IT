---
title: Modalità console di alto livello
description: Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059628"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="73da6-104">Modalità console di alto livello</span><span class="sxs-lookup"><span data-stu-id="73da6-104">High-Level Console Modes</span></span>


<span data-ttu-id="73da6-105">Il comportamento delle funzioni console di alto livello è influenzato dalle modalità di input e output della console.</span><span class="sxs-lookup"><span data-stu-id="73da6-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="73da6-106">Tutte le modalità di input della console seguenti sono abilitate per il buffer di input di una console quando viene creata una console:</span><span class="sxs-lookup"><span data-stu-id="73da6-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="73da6-107">Modalità input linea</span><span class="sxs-lookup"><span data-stu-id="73da6-107">Line input mode</span></span>
- <span data-ttu-id="73da6-108">Modalità di input elaborata</span><span class="sxs-lookup"><span data-stu-id="73da6-108">Processed input mode</span></span>
- <span data-ttu-id="73da6-109">Modalità input echo</span><span class="sxs-lookup"><span data-stu-id="73da6-109">Echo input mode</span></span>

<span data-ttu-id="73da6-110">Entrambe le modalità di output della console seguenti sono abilitate per un buffer dello schermo della console quando viene creato:</span><span class="sxs-lookup"><span data-stu-id="73da6-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="73da6-111">Modalità output elaborata</span><span class="sxs-lookup"><span data-stu-id="73da6-111">Processed output mode</span></span>
- <span data-ttu-id="73da6-112">Wrapping in modalità di output EOL</span><span class="sxs-lookup"><span data-stu-id="73da6-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="73da6-113">Tutte e tre le modalità di input, insieme alla modalità output elaborata, sono progettate per essere utilizzate insieme.</span><span class="sxs-lookup"><span data-stu-id="73da6-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="73da6-114">È consigliabile abilitare o disabilitare tutte queste modalità come gruppo.</span><span class="sxs-lookup"><span data-stu-id="73da6-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="73da6-115">Quando tutti sono abilitati, l'applicazione viene definita in modalità "cotta", il che significa che la maggior parte dell'elaborazione viene gestita per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="73da6-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="73da6-116">Quando tutti sono disabilitati, l'applicazione è in modalità "Raw", il che significa che l'input non viene filtrato e l'elaborazione viene lasciata all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="73da6-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="73da6-117">Un'applicazione può usare la funzione [**GetConsoleMode**](getconsolemode.md) per determinare la modalità corrente del buffer di input o dello schermo di una console.</span><span class="sxs-lookup"><span data-stu-id="73da6-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="73da6-118">È possibile abilitare o disabilitare una qualsiasi di queste modalità usando i valori seguenti nella funzione [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="73da6-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="73da6-119">Si noti che l'impostazione della modalità di output di un buffer dello schermo non influisce sulla modalità di output di altri buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="73da6-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="73da6-120">Mode</span><span class="sxs-lookup"><span data-stu-id="73da6-120">Mode</span></span></th>
<th><span data-ttu-id="73da6-121">Descrizione</span><span class="sxs-lookup"><span data-stu-id="73da6-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="73da6-122"><strong>ENABLE_PROCESSED_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="73da6-122"><strong>ENABLE_PROCESSED_INPUT</strong></span></span></td>
<td><span data-ttu-id="73da6-123">Viene usato con un handle di input della console per fare in modo che il sistema elabori l'input della chiave di modifica o di controllo del sistema anziché restituirlo come input nel buffer dell'operazione di lettura&#39;s.</span><span class="sxs-lookup"><span data-stu-id="73da6-123">Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer.</span></span> <span data-ttu-id="73da6-124">Se è abilitato anche l'input di riga, gli spazi e i ritorni a capo vengono gestiti correttamente.</span><span class="sxs-lookup"><span data-stu-id="73da6-124">If line input is also enabled, backspaces and carriage returns are handled correctly.</span></span> <span data-ttu-id="73da6-125">Un backspace determina lo spostamento del cursore indietro di uno spazio senza influire sul carattere in corrispondenza della posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="73da6-125">A backspace causes the cursor to move back one space without affecting the character at the cursor position.</span></span> <span data-ttu-id="73da6-126">Un ritorno a capo viene convertito in una combinazione di caratteri di ritorno a capo-avanzamento riga.</span><span class="sxs-lookup"><span data-stu-id="73da6-126">A carriage return is converted to carriage return – line feed character combination.</span></span> <span data-ttu-id="73da6-127">Se la modalità di input echo è abilitata e l'output deve riflettere la modifica del sistema, l'output elaborato deve essere abilitato per il buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="73da6-127">If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer.</span></span> <span data-ttu-id="73da6-128">Se l'input elaborato è abilitato, la combinazione di tasti CTRL + C viene passata al gestore appropriato, indipendentemente dal fatto che sia abilitato l'input della riga.</span><span class="sxs-lookup"><span data-stu-id="73da6-128">If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled.</span></span> <span data-ttu-id="73da6-129">Per altre informazioni sui gestori di controllo, vedere <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">gestori di controlli della console</a>.</span><span class="sxs-lookup"><span data-stu-id="73da6-129">For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="73da6-130"><strong>ENABLE_LINE_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="73da6-130"><strong>ENABLE_LINE_INPUT</strong></span></span></td>
<td><span data-ttu-id="73da6-131">Usato con un handle di input della console per fare in modo che le funzioni <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> e <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> restituiscano quando viene premuto il tasto INVIO.</span><span class="sxs-lookup"><span data-stu-id="73da6-131">Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed.</span></span> <span data-ttu-id="73da6-132">Se la modalità di input della riga è disabilitata, le funzioni restituiscono quando uno o più caratteri sono disponibili nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="73da6-132">If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="73da6-133"><strong>ENABLE_ECHO_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="73da6-133"><strong>ENABLE_ECHO_INPUT</strong></span></span></td>
<td><span data-ttu-id="73da6-134">Usato con un handle di input della console per fare in modo che l'input della tastiera letto dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> venga restituito al buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="73da6-134">Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer.</span></span> <span data-ttu-id="73da6-135">I caratteri vengono restituiti solo se il processo che chiama <strong>ReadFile</strong> o <strong>ReadConsole</strong> dispone di un handle aperto per il buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="73da6-135">Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer.</span></span> <span data-ttu-id="73da6-136">Non è possibile abilitare la modalità Echo a meno che non sia abilitata anche l'input della riga.</span><span class="sxs-lookup"><span data-stu-id="73da6-136">Echo mode cannot be enabled unless line input is also enabled.</span></span> <span data-ttu-id="73da6-137">La modalità di output del buffer dello schermo attivo influiscono sul modo in cui viene visualizzato l'input eco.</span><span class="sxs-lookup"><span data-stu-id="73da6-137">The output mode of the active screen buffer affects the way echoed input is displayed.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="73da6-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="73da6-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="73da6-139">Utilizzato con un handle del buffer dello schermo della console per fare in modo che il sistema esegua l'azione appropriata per i caratteri di controllo ANSI scritti in un buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="73da6-139">Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer.</span></span> <span data-ttu-id="73da6-140">I caratteri di ritorno a capo, tabulazione, campana, ritorno a capo e avanzamento riga vengono elaborati.</span><span class="sxs-lookup"><span data-stu-id="73da6-140">The backspace, tab, bell, carriage return, and line feed characters are processed.</span></span> <span data-ttu-id="73da6-141">Un carattere di tabulazione sposta il cursore alla successiva tabulazione, che si verifica ogni otto caratteri.</span><span class="sxs-lookup"><span data-stu-id="73da6-141">A tab character moves the cursor to the next tab stop, which occurs every eight characters.</span></span> <span data-ttu-id="73da6-142">Un carattere a campana emette un tono breve.</span><span class="sxs-lookup"><span data-stu-id="73da6-142">A bell character sounds a short tone.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="73da6-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="73da6-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="73da6-144">Utilizzato con un handle del buffer dello schermo della console per fare in modo che la posizione di output corrente (posizione del cursore) si sposti sulla prima colonna nella riga successiva (riga) quando viene raggiunta la fine della riga corrente.</span><span class="sxs-lookup"><span data-stu-id="73da6-144">Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached.</span></span> <span data-ttu-id="73da6-145">Se viene raggiunta la parte inferiore dell'area della finestra, l'origine della finestra viene spostata verso il basso di una riga.</span><span class="sxs-lookup"><span data-stu-id="73da6-145">If the bottom of the window region is reached, the window origin is moved down one row.</span></span> <span data-ttu-id="73da6-146">Questo movimento ha l'effetto di scorrere il contenuto della finestra verso l'alto di una riga.</span><span class="sxs-lookup"><span data-stu-id="73da6-146">This movement has the effect of scrolling the contents of the window up one row.</span></span> <span data-ttu-id="73da6-147">Se viene raggiunta la fine del buffer dello schermo della console, il contenuto del buffer dello schermo della console viene spostato verso l'alto di una riga e la riga superiore del buffer dello schermo della console viene eliminata.</span><span class="sxs-lookup"><span data-stu-id="73da6-147">If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.</span></span>
<p><span data-ttu-id="73da6-148">Se questa modalità è disabilitata, l'ultimo carattere della riga viene sovrascritto con i caratteri successivi.</span><span class="sxs-lookup"><span data-stu-id="73da6-148">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




