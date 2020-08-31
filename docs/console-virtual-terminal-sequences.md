---
title: Sequenze di terminali virtuali console
description: Le sequenze di terminali virtuali sono sequenze di caratteri di controllo che possono controllare lo spostamento del cursore, la modalità colore/carattere e altre operazioni quando vengono scritte nel flusso di output.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: d05aa6f44cc97478d4eb2aba25587b2506e84a98
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059969"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="6a2af-104">Sequenze di terminali virtuali console</span><span class="sxs-lookup"><span data-stu-id="6a2af-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="6a2af-105">Le sequenze di terminali virtuali sono sequenze di caratteri di controllo che possono controllare lo spostamento del cursore, la modalità colore/carattere e altre operazioni quando vengono scritte nel flusso di output.</span><span class="sxs-lookup"><span data-stu-id="6a2af-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="6a2af-106">Le sequenze possono anche essere ricevute nel flusso di input in risposta a una sequenza di informazioni di query del flusso di output o come codifica dell'input utente quando viene impostata la modalità appropriata.</span><span class="sxs-lookup"><span data-stu-id="6a2af-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="6a2af-107">Per configurare questo comportamento, è possibile usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2af-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="6a2af-108">Alla fine di questo documento è incluso un esempio della modalità consigliata per abilitare i comportamenti dei terminali virtuali.</span><span class="sxs-lookup"><span data-stu-id="6a2af-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="6a2af-109">Il comportamento delle sequenze seguenti si basa sulle tecnologie dell'emulatore di terminale VT100 e derivato, in particolare l'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="6a2af-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="6a2af-110">Altre informazioni sulle sequenze di terminali sono disponibili in <http://vt100.net> e in <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .</span><span class="sxs-lookup"><span data-stu-id="6a2af-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="6a2af-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Sequenze di output</span><span class="sxs-lookup"><span data-stu-id="6a2af-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="6a2af-112">Le sequenze terminali seguenti vengono intercettate dall'host della console quando vengono scritte nel flusso di output, se il flag di ABILITAzione del \_ \_ terminale virtuale \_ è impostato sull'handle del buffer dello schermo mediante la funzione [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2af-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="6a2af-113">Si noti che il \_ \_ \_ flag di restituzione automatica della nuova riga può essere utile anche per emulare il posizionamento del cursore e il comportamento di scorrimento di altri emulatori terminali in relazione ai caratteri scritti nella colonna finale in una riga.</span><span class="sxs-lookup"><span data-stu-id="6a2af-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="6a2af-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posizionamento semplice del cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="6a2af-115">In tutte le descrizioni seguenti, ESC è sempre il valore esadecimale 0x1B.</span><span class="sxs-lookup"><span data-stu-id="6a2af-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="6a2af-116">Non è necessario includere spazi nelle sequenze di terminali.</span><span class="sxs-lookup"><span data-stu-id="6a2af-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="6a2af-117">Per un esempio di come queste sequenze vengono usate in pratica, vedere l' [esempio](#example) alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="6a2af-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="6a2af-118">Nella tabella seguente vengono descritte le sequenze di escape semplici con un solo comando di azione subito dopo il carattere ESC.</span><span class="sxs-lookup"><span data-stu-id="6a2af-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="6a2af-119">Queste sequenze non hanno parametri e hanno effetto immediato.</span><span class="sxs-lookup"><span data-stu-id="6a2af-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="6a2af-120">Tutti i comandi in questa tabella sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) per posizionare il cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="6a2af-121">Lo spostamento del cursore verrà limitato dal viewport corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="6a2af-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="6a2af-122">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="6a2af-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="6a2af-123">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-123">Sequence</span></span> | <span data-ttu-id="6a2af-124">Sintassi abbreviata</span><span class="sxs-lookup"><span data-stu-id="6a2af-124">Shorthand</span></span> | <span data-ttu-id="6a2af-125">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-125">Behavior</span></span>                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="6a2af-126">ESC A</span></span>    | <span data-ttu-id="6a2af-127">CUU</span><span class="sxs-lookup"><span data-stu-id="6a2af-127">CUU</span></span>       | <span data-ttu-id="6a2af-128">Cursore su 1</span><span class="sxs-lookup"><span data-stu-id="6a2af-128">Cursor Up by 1</span></span>                                                                                                                                |
| <span data-ttu-id="6a2af-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="6a2af-129">ESC B</span></span>    | <span data-ttu-id="6a2af-130">CUD</span><span class="sxs-lookup"><span data-stu-id="6a2af-130">CUD</span></span>       | <span data-ttu-id="6a2af-131">Cursore in basso di 1</span><span class="sxs-lookup"><span data-stu-id="6a2af-131">Cursor Down by 1</span></span>                                                                                                                              |
| <span data-ttu-id="6a2af-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="6a2af-132">ESC C</span></span>    | <span data-ttu-id="6a2af-133">CUF</span><span class="sxs-lookup"><span data-stu-id="6a2af-133">CUF</span></span>       | <span data-ttu-id="6a2af-134">Cursore in poi (destra) di 1</span><span class="sxs-lookup"><span data-stu-id="6a2af-134">Cursor Forward (Right) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="6a2af-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="6a2af-135">ESC D</span></span>    | <span data-ttu-id="6a2af-136">CUB</span><span class="sxs-lookup"><span data-stu-id="6a2af-136">CUB</span></span>       | <span data-ttu-id="6a2af-137">Cursore indietro (sinistra) di 1</span><span class="sxs-lookup"><span data-stu-id="6a2af-137">Cursor Backward (Left) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="6a2af-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="6a2af-138">ESC M</span></span>    | <span data-ttu-id="6a2af-139">RI</span><span class="sxs-lookup"><span data-stu-id="6a2af-139">RI</span></span>        | <span data-ttu-id="6a2af-140">Indice inverso: esegue l'operazione inversa di \\ n, sposta il cursore verso l'alto di una riga, mantiene la posizione orizzontale, scorre il buffer se necessario\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="6a2af-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="6a2af-141">ESC 7</span></span>    | <span data-ttu-id="6a2af-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="6a2af-142">DECSC</span></span>     | <span data-ttu-id="6a2af-143">Salva posizione cursore in memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-143">Save Cursor Position in Memory\*\*</span></span>                                                                                                            |
| <span data-ttu-id="6a2af-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="6a2af-144">ESC 8</span></span>    | <span data-ttu-id="6a2af-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="6a2af-145">DECSR</span></span>     | <span data-ttu-id="6a2af-146">Ripristina posizione cursore dalla memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-146">Restore Cursor Position from Memory\*\*</span></span>                                                                                                       |



<span data-ttu-id="6a2af-147">**Nota**</span><span class="sxs-lookup"><span data-stu-id="6a2af-147">**Note**</span></span>  
<span data-ttu-id="6a2af-148">\* Se sono impostati margini di scorrimento, il RI all'interno dei margini scorrerà solo il contenuto dei margini e rimarrà invariato il viewport.</span><span class="sxs-lookup"><span data-stu-id="6a2af-148">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="6a2af-149">(Vedere margini di scorrimento)</span><span class="sxs-lookup"><span data-stu-id="6a2af-149">(See Scrolling Margins)</span></span>

<span data-ttu-id="6a2af-150">\*\*Non verrà salvato alcun valore in memoria fino al primo utilizzo del comando Save.</span><span class="sxs-lookup"><span data-stu-id="6a2af-150">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="6a2af-151">L'unico modo per accedere al valore salvato è con il comando Restore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-151">The only way to access the saved value is with the restore command.</span></span>



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="6a2af-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posizionamento del cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="6a2af-153">Le tabelle seguenti comprendono le sequenze di tipo CSI (Control Sequence Introducr).</span><span class="sxs-lookup"><span data-stu-id="6a2af-153">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="6a2af-154">Tutte le sequenze CSI iniziano con ESC (0x1B) seguito da \[ (parentesi quadra aperta, 0x5b) e possono contenere parametri di lunghezza variabile per specificare altre informazioni per ogni operazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-154">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="6a2af-155">Questa operazione sarà rappresentata dall'abbreviazione &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-155">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="6a2af-156">Ogni tabella riportata di seguito è raggruppata per funzionalità con note sotto ogni tabella che illustra il funzionamento del gruppo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-156">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="6a2af-157">Per tutti i parametri, le regole seguenti si applicano se non diversamente specificato:</span><span class="sxs-lookup"><span data-stu-id="6a2af-157">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="6a2af-158">&lt;n &gt; rappresenta la distanza da spostare ed è un parametro facoltativo</span><span class="sxs-lookup"><span data-stu-id="6a2af-158">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="6a2af-159">Se &lt; n &gt; viene omesso o è uguale a 0, verrà considerato come 1</span><span class="sxs-lookup"><span data-stu-id="6a2af-159">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="6a2af-160">&lt;n &gt; non può essere maggiore di 32.767 (valore short massimo)</span><span class="sxs-lookup"><span data-stu-id="6a2af-160">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="6a2af-161">&lt;n &gt; non può essere negativo</span><span class="sxs-lookup"><span data-stu-id="6a2af-161">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="6a2af-162">Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2af-162">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="6a2af-163">Lo spostamento del cursore verrà limitato dal viewport corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="6a2af-163">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="6a2af-164">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="6a2af-164">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="6a2af-165">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-165">Sequence</span></span>                       | <span data-ttu-id="6a2af-166">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-166">Code</span></span>      | <span data-ttu-id="6a2af-167">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-167">Description</span></span>                         | <span data-ttu-id="6a2af-168">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-168">Behavior</span></span>                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-169">ESC \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="6a2af-169">ESC \[ &lt;n&gt; A</span></span>             | <span data-ttu-id="6a2af-170">CUU</span><span class="sxs-lookup"><span data-stu-id="6a2af-170">CUU</span></span>       | <span data-ttu-id="6a2af-171">Cursore su</span><span class="sxs-lookup"><span data-stu-id="6a2af-171">Cursor Up</span></span>                           | <span data-ttu-id="6a2af-172">Cursore per &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-172">Cursor up by &lt;n&gt;</span></span>                                                                                                     |
| <span data-ttu-id="6a2af-173">ESC \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="6a2af-173">ESC \[ &lt;n&gt; B</span></span>             | <span data-ttu-id="6a2af-174">CUD</span><span class="sxs-lookup"><span data-stu-id="6a2af-174">CUD</span></span>       | <span data-ttu-id="6a2af-175">Cursore in basso</span><span class="sxs-lookup"><span data-stu-id="6a2af-175">Cursor Down</span></span>                         | <span data-ttu-id="6a2af-176">Cursore verso il basso per &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-176">Cursor down by &lt;n&gt;</span></span>                                                                                                   |
| <span data-ttu-id="6a2af-177">ESC \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="6a2af-177">ESC \[ &lt;n&gt; C</span></span>             | <span data-ttu-id="6a2af-178">CUF</span><span class="sxs-lookup"><span data-stu-id="6a2af-178">CUF</span></span>       | <span data-ttu-id="6a2af-179">Cursore in su</span><span class="sxs-lookup"><span data-stu-id="6a2af-179">Cursor Forward</span></span>                      | <span data-ttu-id="6a2af-180">Cursore in poi (destra) per &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-180">Cursor forward (Right) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="6a2af-181">ESC \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="6a2af-181">ESC \[ &lt;n&gt; D</span></span>             | <span data-ttu-id="6a2af-182">CUB</span><span class="sxs-lookup"><span data-stu-id="6a2af-182">CUB</span></span>       | <span data-ttu-id="6a2af-183">Cursore indietro</span><span class="sxs-lookup"><span data-stu-id="6a2af-183">Cursor Backward</span></span>                     | <span data-ttu-id="6a2af-184">Cursore indietro (a sinistra) per &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-184">Cursor backward (Left) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="6a2af-185">ESC \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="6a2af-185">ESC \[ &lt;n&gt; E</span></span>             | <span data-ttu-id="6a2af-186">CNL</span><span class="sxs-lookup"><span data-stu-id="6a2af-186">CNL</span></span>       | <span data-ttu-id="6a2af-187">Riga successiva cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-187">Cursor Next Line</span></span>                    | <span data-ttu-id="6a2af-188">Cursore verso il basso fino all'inizio della &lt; n &gt; riga nel viewport</span><span class="sxs-lookup"><span data-stu-id="6a2af-188">Cursor down to beginning of &lt;n&gt;th line in the viewport</span></span>                                                               |
| <span data-ttu-id="6a2af-189">ESC \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="6a2af-189">ESC \[ &lt;n&gt; F</span></span>             | <span data-ttu-id="6a2af-190">CPL</span><span class="sxs-lookup"><span data-stu-id="6a2af-190">CPL</span></span>       | <span data-ttu-id="6a2af-191">Riga precedente cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-191">Cursor Previous Line</span></span>                | <span data-ttu-id="6a2af-192">Cursore fino all'inizio della &lt; n &gt; riga nel viewport</span><span class="sxs-lookup"><span data-stu-id="6a2af-192">Cursor up to beginning of &lt;n&gt;th line in the viewport</span></span>                                                                 |
| <span data-ttu-id="6a2af-193">ESC \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="6a2af-193">ESC \[ &lt;n&gt; G</span></span>             | <span data-ttu-id="6a2af-194">CHA</span><span class="sxs-lookup"><span data-stu-id="6a2af-194">CHA</span></span>       | <span data-ttu-id="6a2af-195">Assoluto cursore orizzontale</span><span class="sxs-lookup"><span data-stu-id="6a2af-195">Cursor Horizontal Absolute</span></span>          | <span data-ttu-id="6a2af-196">Il cursore passa &lt; alla &gt; Posizione n orizzontalmente nella riga corrente</span><span class="sxs-lookup"><span data-stu-id="6a2af-196">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span>                                                      |
| <span data-ttu-id="6a2af-197">ESC \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="6a2af-197">ESC \[ &lt;n&gt; d</span></span>             | <span data-ttu-id="6a2af-198">VPA</span><span class="sxs-lookup"><span data-stu-id="6a2af-198">VPA</span></span>       | <span data-ttu-id="6a2af-199">Posizione assoluta linea verticale</span><span class="sxs-lookup"><span data-stu-id="6a2af-199">Vertical Line Position Absolute</span></span>     | <span data-ttu-id="6a2af-200">Il cursore passa alla &lt; &gt; Posizione n verticalmente nella colonna corrente</span><span class="sxs-lookup"><span data-stu-id="6a2af-200">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span>                                                  |
| <span data-ttu-id="6a2af-201">ESC \[ &lt; y &gt; ; &lt; x &gt; H</span><span class="sxs-lookup"><span data-stu-id="6a2af-201">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="6a2af-202">CUP</span><span class="sxs-lookup"><span data-stu-id="6a2af-202">CUP</span></span>       | <span data-ttu-id="6a2af-203">Posizione cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-203">Cursor Position</span></span>                     | <span data-ttu-id="6a2af-204">\*Il cursore passa a &lt; x &gt; ; &lt; &gt; coordinata y all'interno del viewport, dove &lt; x &gt; è la colonna della &lt; &gt; linea y</span><span class="sxs-lookup"><span data-stu-id="6a2af-204">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="6a2af-205">ESC \[ &lt; y &gt; ; &lt; x &gt; f</span><span class="sxs-lookup"><span data-stu-id="6a2af-205">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="6a2af-206">HVP</span><span class="sxs-lookup"><span data-stu-id="6a2af-206">HVP</span></span>       | <span data-ttu-id="6a2af-207">Posizione verticale orizzontale</span><span class="sxs-lookup"><span data-stu-id="6a2af-207">Horizontal Vertical Position</span></span>        | <span data-ttu-id="6a2af-208">\*Il cursore passa a &lt; x &gt; ; &lt; &gt; coordinata y all'interno del viewport, dove &lt; x &gt; è la colonna della &lt; &gt; linea y</span><span class="sxs-lookup"><span data-stu-id="6a2af-208">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="6a2af-209">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="6a2af-209">ESC \[ s</span></span>                       | <span data-ttu-id="6a2af-210">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="6a2af-210">ANSISYSSC</span></span> | <span data-ttu-id="6a2af-211">Salva cursore-emulazione Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="6a2af-211">Save Cursor – Ansi.sys emulation</span></span>    | <span data-ttu-id="6a2af-212">\*\*Senza parametri, esegue un'operazione di salvataggio del cursore, ad esempio DECSC</span><span class="sxs-lookup"><span data-stu-id="6a2af-212">\*\*With no parameters, performs a save cursor operation like DECSC</span></span>                                                        |
| <span data-ttu-id="6a2af-213">\[U ESC</span><span class="sxs-lookup"><span data-stu-id="6a2af-213">ESC \[ u</span></span>                       | <span data-ttu-id="6a2af-214">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="6a2af-214">ANSISYSSC</span></span> | <span data-ttu-id="6a2af-215">Restore Cursor-Ansi.sys emulazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-215">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="6a2af-216">\*\*Senza parametri, esegue un'operazione di ripristino del cursore, ad esempio DECRC</span><span class="sxs-lookup"><span data-stu-id="6a2af-216">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span>                                                     |



<span data-ttu-id="6a2af-217">**Nota**</span><span class="sxs-lookup"><span data-stu-id="6a2af-217">**Note**</span></span>  
<span data-ttu-id="6a2af-218">\*&lt;&gt; &lt; i parametri x e y &gt; hanno le stesse limitazioni di &lt; n &gt; sopra.</span><span class="sxs-lookup"><span data-stu-id="6a2af-218">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="6a2af-219">Se &lt; &gt; le x e &lt; y &gt; vengono omesse, verranno impostate su 1; 1.</span><span class="sxs-lookup"><span data-stu-id="6a2af-219">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>

<span data-ttu-id="6a2af-220">\*\*ANSI.sys documentazione cronologica è reperibile in <https://msdn.microsoft.com/library/cc722862.aspx> ed è implementata per praticità/compatibilità.</span><span class="sxs-lookup"><span data-stu-id="6a2af-220">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="6a2af-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilità del cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="6a2af-222">I comandi seguenti consentono di controllare la visibilità del cursore e del relativo stato intermittente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-222">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="6a2af-223">Le sequenze DECTCEM sono in genere equivalenti alla chiamata dell'API della console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) per impostare la visibilità del cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-223">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="6a2af-224">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-224">Sequence</span></span>      | <span data-ttu-id="6a2af-225">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-225">Code</span></span>    | <span data-ttu-id="6a2af-226">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-226">Description</span></span>                  | <span data-ttu-id="6a2af-227">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-227">Behavior</span></span>                  |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="6a2af-228">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-228">ESC \[ ?</span></span> <span data-ttu-id="6a2af-229">12 ore</span><span class="sxs-lookup"><span data-stu-id="6a2af-229">12 h</span></span> | <span data-ttu-id="6a2af-230">ATT160</span><span class="sxs-lookup"><span data-stu-id="6a2af-230">ATT160</span></span>  | <span data-ttu-id="6a2af-231">Abilitazione del cursore di testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-231">Text Cursor Enable Blinking</span></span>  | <span data-ttu-id="6a2af-232">Avvia il cursore lampeggiante</span><span class="sxs-lookup"><span data-stu-id="6a2af-232">Start the cursor blinking</span></span> |
| <span data-ttu-id="6a2af-233">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-233">ESC \[ ?</span></span> <span data-ttu-id="6a2af-234">12 l</span><span class="sxs-lookup"><span data-stu-id="6a2af-234">12 l</span></span> | <span data-ttu-id="6a2af-235">ATT160</span><span class="sxs-lookup"><span data-stu-id="6a2af-235">ATT160</span></span>  | <span data-ttu-id="6a2af-236">Disabilitazione del cursore di testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-236">Text Cursor Disable Blinking</span></span>  | <span data-ttu-id="6a2af-237">Interrompi l'intermittenza del cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-237">Stop blinking the cursor</span></span>  |
| <span data-ttu-id="6a2af-238">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-238">ESC \[ ?</span></span> <span data-ttu-id="6a2af-239">25 ore</span><span class="sxs-lookup"><span data-stu-id="6a2af-239">25 h</span></span> | <span data-ttu-id="6a2af-240">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="6a2af-240">DECTCEM</span></span> | <span data-ttu-id="6a2af-241">Mostra modalità di abilitazione cursore testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-241">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="6a2af-242">Mostra cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-242">Show the cursor</span></span>           |
| <span data-ttu-id="6a2af-243">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-243">ESC \[ ?</span></span> <span data-ttu-id="6a2af-244">25 l</span><span class="sxs-lookup"><span data-stu-id="6a2af-244">25 l</span></span> | <span data-ttu-id="6a2af-245">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="6a2af-245">DECTCEM</span></span> | <span data-ttu-id="6a2af-246">Nascondi modalità di abilitazione cursore testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-246">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="6a2af-247">Nascondi cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-247">Hide the cursor</span></span>           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="6a2af-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posizionamento del viewport</span><span class="sxs-lookup"><span data-stu-id="6a2af-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="6a2af-249">Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata dell'API della console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per spostare il contenuto del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="6a2af-249">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="6a2af-250">**Attenzione**  I nomi dei comandi sono fuorvianti.</span><span class="sxs-lookup"><span data-stu-id="6a2af-250">**Caution**  The command names are misleading.</span></span> <span data-ttu-id="6a2af-251">Scroll si riferisce alla direzione di spostamento del testo durante l'operazione, non alla modalità di spostamento del viewport.</span><span class="sxs-lookup"><span data-stu-id="6a2af-251">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="6a2af-252">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-252">Sequence</span></span>           | <span data-ttu-id="6a2af-253">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-253">Code</span></span> | <span data-ttu-id="6a2af-254">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-254">Description</span></span> | <span data-ttu-id="6a2af-255">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-255">Behavior</span></span>                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-256">ESC \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="6a2af-256">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="6a2af-257">Unità di streaming (SU)</span><span class="sxs-lookup"><span data-stu-id="6a2af-257">SU</span></span>   | <span data-ttu-id="6a2af-258">Scorrimento verso l'alto</span><span class="sxs-lookup"><span data-stu-id="6a2af-258">Scroll Up</span></span>   | <span data-ttu-id="6a2af-259">Scorrere il testo per &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-259">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="6a2af-260">Noto anche come Pan Down, le nuove righe si riempiono dalla parte inferiore dello schermo</span><span class="sxs-lookup"><span data-stu-id="6a2af-260">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="6a2af-261">ESC \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="6a2af-261">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="6a2af-262">DS</span><span class="sxs-lookup"><span data-stu-id="6a2af-262">SD</span></span>   | <span data-ttu-id="6a2af-263">Scorrimento verso il basso</span><span class="sxs-lookup"><span data-stu-id="6a2af-263">Scroll Down</span></span> | <span data-ttu-id="6a2af-264">Scorri verso il basso per &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-264">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="6a2af-265">Noto anche come Pan up, le nuove righe vengono inserite nella parte superiore della schermata</span><span class="sxs-lookup"><span data-stu-id="6a2af-265">Also known as pan up, new lines fill in from the top of the screen</span></span>         |



<span data-ttu-id="6a2af-266">Il testo viene spostato a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-266">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="6a2af-267">Se il cursore si trova nella riga centrale del viewport, scorrere verso l'alto sposta la metà inferiore del viewport e inserisce righe vuote nella parte inferiore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-267">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="6a2af-268">Scorri verso il basso sposta la metà superiore delle righe del viewport e inserisce nuove righe nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-268">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="6a2af-269">Inoltre, è importante notare che lo scorrimento verso l'alto e verso il basso è influenzato anche dai margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="6a2af-269">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="6a2af-270">Lo scorrimento verso l'alto e verso il basso non influirà su alcuna riga al di fuori dei margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="6a2af-270">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="6a2af-271">Il valore predefinito per &lt; n &gt; è 1 e il valore può essere omesso facoltativamente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-271">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="6a2af-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modifica del testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="6a2af-273">Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata delle API della console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)e [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per modificare il contenuto del buffer di testo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-273">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="6a2af-274">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-274">Sequence</span></span>           | <span data-ttu-id="6a2af-275">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-275">Code</span></span> | <span data-ttu-id="6a2af-276">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-276">Description</span></span>      | <span data-ttu-id="6a2af-277">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-277">Behavior</span></span>                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-278">ESC \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="6a2af-278">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="6a2af-279">ICH</span><span class="sxs-lookup"><span data-stu-id="6a2af-279">ICH</span></span>  | <span data-ttu-id="6a2af-280">Inserisci carattere</span><span class="sxs-lookup"><span data-stu-id="6a2af-280">Insert Character</span></span> | <span data-ttu-id="6a2af-281">Inserisce &lt; n &gt; spazi nella posizione corrente del cursore, spostando tutto il testo esistente a destra.</span><span class="sxs-lookup"><span data-stu-id="6a2af-281">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="6a2af-282">Il testo che esce dalla schermata a destra viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="6a2af-282">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="6a2af-283">ESC \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="6a2af-283">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="6a2af-284">DCH</span><span class="sxs-lookup"><span data-stu-id="6a2af-284">DCH</span></span>  | <span data-ttu-id="6a2af-285">Elimina carattere</span><span class="sxs-lookup"><span data-stu-id="6a2af-285">Delete Character</span></span> | <span data-ttu-id="6a2af-286">Eliminare &lt; n &gt; caratteri nella posizione corrente del cursore, spostando i caratteri di spazio dal bordo destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-286">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span>                       |
| <span data-ttu-id="6a2af-287">ESC \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="6a2af-287">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="6a2af-288">ECH</span><span class="sxs-lookup"><span data-stu-id="6a2af-288">ECH</span></span>  | <span data-ttu-id="6a2af-289">Carattere di cancellazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-289">Erase Character</span></span>  | <span data-ttu-id="6a2af-290">&lt; &gt; Consente di cancellare n caratteri dalla posizione corrente del cursore sovrascrivendo gli elementi con uno spazio.</span><span class="sxs-lookup"><span data-stu-id="6a2af-290">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span>                                           |
| <span data-ttu-id="6a2af-291">ESC \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="6a2af-291">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="6a2af-292">IL</span><span class="sxs-lookup"><span data-stu-id="6a2af-292">IL</span></span>   | <span data-ttu-id="6a2af-293">Inserisci riga</span><span class="sxs-lookup"><span data-stu-id="6a2af-293">Insert Line</span></span>      | <span data-ttu-id="6a2af-294">Inserisce &lt; n &gt; righe nel buffer in corrispondenza della posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-294">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="6a2af-295">La riga in cui si trova il cursore e le linee sotto di essa verranno spostate verso il basso.</span><span class="sxs-lookup"><span data-stu-id="6a2af-295">The line the cursor is on, and lines below it, will be shifted downwards.</span></span>         |
| <span data-ttu-id="6a2af-296">ESC \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="6a2af-296">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="6a2af-297">DL</span><span class="sxs-lookup"><span data-stu-id="6a2af-297">DL</span></span>   | <span data-ttu-id="6a2af-298">Elimina riga</span><span class="sxs-lookup"><span data-stu-id="6a2af-298">Delete Line</span></span>      | <span data-ttu-id="6a2af-299">Elimina &lt; n &gt; righe dal buffer, a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-299">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span>                                                                  |



<span data-ttu-id="6a2af-300">**Nota**</span><span class="sxs-lookup"><span data-stu-id="6a2af-300">**Note**</span></span>  
<span data-ttu-id="6a2af-301">Per IL e DL, sono interessate solo le righe dei margini di scorrimento (vedere i margini di scorrimento).</span><span class="sxs-lookup"><span data-stu-id="6a2af-301">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="6a2af-302">Se non sono impostati margini, i bordi dei margini predefiniti corrispondono al viewport corrente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-302">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="6a2af-303">Se le righe vengono spostate al di sotto dei margini, vengono scartate.</span><span class="sxs-lookup"><span data-stu-id="6a2af-303">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="6a2af-304">Quando le righe vengono eliminate, le righe vuote vengono inserite nella parte inferiore dei margini, non vengono mai interessate le linee esterne al viewport.</span><span class="sxs-lookup"><span data-stu-id="6a2af-304">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="6a2af-305">Per ogni sequenza, il valore predefinito di &lt; n &gt; se viene omesso è 0.</span><span class="sxs-lookup"><span data-stu-id="6a2af-305">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="6a2af-306">Per i comandi seguenti, il parametro &lt; n &gt; presenta 3 valori validi:</span><span class="sxs-lookup"><span data-stu-id="6a2af-306">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="6a2af-307">0 cancella dalla posizione corrente del cursore (inclusivo) alla fine della riga/visualizzazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-307">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="6a2af-308">1 Cancella dall'inizio della riga/visualizza fino alla posizione corrente del cursore e inclusa</span><span class="sxs-lookup"><span data-stu-id="6a2af-308">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="6a2af-309">2 Cancella l'intera riga/visualizzazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-309">2 erases the entire line/display</span></span>


| <span data-ttu-id="6a2af-310">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-310">Sequence</span></span>           | <span data-ttu-id="6a2af-311">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-311">Code</span></span> | <span data-ttu-id="6a2af-312">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-312">Description</span></span>      | <span data-ttu-id="6a2af-313">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-313">Behavior</span></span>                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-314">ESC \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="6a2af-314">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="6a2af-315">ED</span><span class="sxs-lookup"><span data-stu-id="6a2af-315">ED</span></span>   | <span data-ttu-id="6a2af-316">Cancella nella visualizzazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-316">Erase in Display</span></span> | <span data-ttu-id="6a2af-317">Sostituisci tutto il testo nel viewport/schermata corrente specificato da &lt; n &gt; con caratteri di spazio</span><span class="sxs-lookup"><span data-stu-id="6a2af-317">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="6a2af-318">ESC \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="6a2af-318">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="6a2af-319">EL</span><span class="sxs-lookup"><span data-stu-id="6a2af-319">EL</span></span>   | <span data-ttu-id="6a2af-320">Cancella riga</span><span class="sxs-lookup"><span data-stu-id="6a2af-320">Erase in Line</span></span>    | <span data-ttu-id="6a2af-321">Sostituisce tutto il testo della riga con il cursore specificato da &lt; n &gt; con caratteri di spazio</span><span class="sxs-lookup"><span data-stu-id="6a2af-321">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span>    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="6a2af-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formattazione del testo</span><span class="sxs-lookup"><span data-stu-id="6a2af-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="6a2af-323">Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata delle API della console [**SetConsoleTextAttribute**](setconsoletextattribute.md) per modificare la formattazione di tutte le scritture future nel buffer di testo di output della console.</span><span class="sxs-lookup"><span data-stu-id="6a2af-323">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="6a2af-324">Questo comando è speciale in quanto la &lt; &gt; Posizione n seguente può accettare tra 0 e 16 parametri separati da punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="6a2af-324">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="6a2af-325">Quando non viene specificato alcun parametro, questo viene considerato come un singolo parametro 0.</span><span class="sxs-lookup"><span data-stu-id="6a2af-325">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="6a2af-326">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-326">Sequence</span></span>           | <span data-ttu-id="6a2af-327">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-327">Code</span></span> | <span data-ttu-id="6a2af-328">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-328">Description</span></span>            | <span data-ttu-id="6a2af-329">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-329">Behavior</span></span>                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="6a2af-330">ESC \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="6a2af-330">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="6a2af-331">SGR</span><span class="sxs-lookup"><span data-stu-id="6a2af-331">SGR</span></span>  | <span data-ttu-id="6a2af-332">Imposta rendering grafica</span><span class="sxs-lookup"><span data-stu-id="6a2af-332">Set Graphics Rendition</span></span> | <span data-ttu-id="6a2af-333">Imposta il formato dello schermo e del testo come specificato da &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-333">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="6a2af-334">La seguente tabella di valori può essere usata in &lt; n &gt; per rappresentare diverse modalità di formattazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-334">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="6a2af-335">Le modalità di formattazione vengono applicate da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="6a2af-335">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="6a2af-336">Se si applicano opzioni di formattazione in competizione, l'opzione più a destra avrà la precedenza.</span><span class="sxs-lookup"><span data-stu-id="6a2af-336">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="6a2af-337">Per le opzioni che specificano i colori, i colori verranno usati come definito nella tabella dei colori della console, che può essere modificata tramite l'API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) .</span><span class="sxs-lookup"><span data-stu-id="6a2af-337">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="6a2af-338">Se la tabella viene modificata per fare in modo che la posizione "blu" della tabella visualizzi una sfumatura di rosso RGB, tutte le chiamate al **blu in primo piano** visualizzeranno il colore rosso fino a quando non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="6a2af-338">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="6a2af-339">valore</span><span class="sxs-lookup"><span data-stu-id="6a2af-339">Value</span></span> | <span data-ttu-id="6a2af-340">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-340">Description</span></span>               | <span data-ttu-id="6a2af-341">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-341">Behavior</span></span>                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="6a2af-342">0</span><span class="sxs-lookup"><span data-stu-id="6a2af-342">0</span></span>     | <span data-ttu-id="6a2af-343">Predefinito</span><span class="sxs-lookup"><span data-stu-id="6a2af-343">Default</span></span>                   | <span data-ttu-id="6a2af-344">Restituisce tutti gli attributi allo stato predefinito prima della modifica</span><span class="sxs-lookup"><span data-stu-id="6a2af-344">Returns all attributes to the default state prior to modification</span></span>  |
| <span data-ttu-id="6a2af-345">1</span><span class="sxs-lookup"><span data-stu-id="6a2af-345">1</span></span>     | <span data-ttu-id="6a2af-346">Grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-346">Bold/Bright</span></span>               | <span data-ttu-id="6a2af-347">Applica il flag di luminosità/intensità al colore di primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-347">Applies brightness/intensity flag to foreground color</span></span>              |
| <span data-ttu-id="6a2af-348">4</span><span class="sxs-lookup"><span data-stu-id="6a2af-348">4</span></span>     | <span data-ttu-id="6a2af-349">Sottolineato</span><span class="sxs-lookup"><span data-stu-id="6a2af-349">Underline</span></span>                 | <span data-ttu-id="6a2af-350">Aggiunge la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="6a2af-350">Adds underline</span></span>                                                     |
| <span data-ttu-id="6a2af-351">24</span><span class="sxs-lookup"><span data-stu-id="6a2af-351">24</span></span>    | <span data-ttu-id="6a2af-352">Nessun sottolineatura</span><span class="sxs-lookup"><span data-stu-id="6a2af-352">No underline</span></span>              | <span data-ttu-id="6a2af-353">Rimuove la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="6a2af-353">Removes underline</span></span>                                                  |
| <span data-ttu-id="6a2af-354">7</span><span class="sxs-lookup"><span data-stu-id="6a2af-354">7</span></span>     | <span data-ttu-id="6a2af-355">Negativo</span><span class="sxs-lookup"><span data-stu-id="6a2af-355">Negative</span></span>                  | <span data-ttu-id="6a2af-356">Scambia i colori di primo piano e sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-356">Swaps foreground and background colors</span></span>                             |
| <span data-ttu-id="6a2af-357">27</span><span class="sxs-lookup"><span data-stu-id="6a2af-357">27</span></span>    | <span data-ttu-id="6a2af-358">Positivo (nessun valore negativo)</span><span class="sxs-lookup"><span data-stu-id="6a2af-358">Positive (No negative)</span></span>    | <span data-ttu-id="6a2af-359">Restituisce il primo piano/sfondo al normale</span><span class="sxs-lookup"><span data-stu-id="6a2af-359">Returns foreground/background to normal</span></span>                            |
| <span data-ttu-id="6a2af-360">30</span><span class="sxs-lookup"><span data-stu-id="6a2af-360">30</span></span>    | <span data-ttu-id="6a2af-361">Nero in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-361">Foreground Black</span></span>          | <span data-ttu-id="6a2af-362">Applica il nero in primo piano non in grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-362">Applies non-bold/bright black to foreground</span></span>                        |
| <span data-ttu-id="6a2af-363">31</span><span class="sxs-lookup"><span data-stu-id="6a2af-363">31</span></span>    | <span data-ttu-id="6a2af-364">Rosso in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-364">Foreground Red</span></span>            | <span data-ttu-id="6a2af-365">Applica il colore rosso in primo piano a quello non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-365">Applies non-bold/bright red to foreground</span></span>                          |
| <span data-ttu-id="6a2af-366">32</span><span class="sxs-lookup"><span data-stu-id="6a2af-366">32</span></span>    | <span data-ttu-id="6a2af-367">Verde primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-367">Foreground Green</span></span>          | <span data-ttu-id="6a2af-368">Applica il verde in primo piano non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-368">Applies non-bold/bright green to foreground</span></span>                        |
| <span data-ttu-id="6a2af-369">33</span><span class="sxs-lookup"><span data-stu-id="6a2af-369">33</span></span>    | <span data-ttu-id="6a2af-370">Giallo in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-370">Foreground Yellow</span></span>         | <span data-ttu-id="6a2af-371">Applica il giallo non grassetto/chiaro a in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-371">Applies non-bold/bright yellow to foreground</span></span>                       |
| <span data-ttu-id="6a2af-372">34</span><span class="sxs-lookup"><span data-stu-id="6a2af-372">34</span></span>    | <span data-ttu-id="6a2af-373">Blu in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-373">Foreground Blue</span></span>           | <span data-ttu-id="6a2af-374">Applica in primo piano non grassetto o blu brillante</span><span class="sxs-lookup"><span data-stu-id="6a2af-374">Applies non-bold/bright blue to foreground</span></span>                         |
| <span data-ttu-id="6a2af-375">35</span><span class="sxs-lookup"><span data-stu-id="6a2af-375">35</span></span>    | <span data-ttu-id="6a2af-376">Magenta in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-376">Foreground Magenta</span></span>        | <span data-ttu-id="6a2af-377">Applica il magenta non grassetto/luminoso a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-377">Applies non-bold/bright magenta to foreground</span></span>                      |
| <span data-ttu-id="6a2af-378">36</span><span class="sxs-lookup"><span data-stu-id="6a2af-378">36</span></span>    | <span data-ttu-id="6a2af-379">Ciano in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-379">Foreground Cyan</span></span>           | <span data-ttu-id="6a2af-380">Applica il cyan non grassetto/luminoso a in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-380">Applies non-bold/bright cyan to foreground</span></span>                         |
| <span data-ttu-id="6a2af-381">37</span><span class="sxs-lookup"><span data-stu-id="6a2af-381">37</span></span>    | <span data-ttu-id="6a2af-382">Bianco in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-382">Foreground White</span></span>          | <span data-ttu-id="6a2af-383">Applica in primo piano un bianco non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-383">Applies non-bold/bright white to foreground</span></span>                        |
| <span data-ttu-id="6a2af-384">38</span><span class="sxs-lookup"><span data-stu-id="6a2af-384">38</span></span>    | <span data-ttu-id="6a2af-385">Primo piano esteso</span><span class="sxs-lookup"><span data-stu-id="6a2af-385">Foreground Extended</span></span>       | <span data-ttu-id="6a2af-386">Applica il valore di colore esteso al primo piano (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="6a2af-386">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="6a2af-387">39</span><span class="sxs-lookup"><span data-stu-id="6a2af-387">39</span></span>    | <span data-ttu-id="6a2af-388">Valore predefinito primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-388">Foreground Default</span></span>        | <span data-ttu-id="6a2af-389">Applica solo la parte in primo piano delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="6a2af-389">Applies only the foreground portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="6a2af-390">40</span><span class="sxs-lookup"><span data-stu-id="6a2af-390">40</span></span>    | <span data-ttu-id="6a2af-391">Sfondo nero</span><span class="sxs-lookup"><span data-stu-id="6a2af-391">Background Black</span></span>          | <span data-ttu-id="6a2af-392">Applica il nero a sfondo non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-392">Applies non-bold/bright black to background</span></span>                        |
| <span data-ttu-id="6a2af-393">41</span><span class="sxs-lookup"><span data-stu-id="6a2af-393">41</span></span>    | <span data-ttu-id="6a2af-394">Rosso sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-394">Background Red</span></span>            | <span data-ttu-id="6a2af-395">Applica lo sfondo al rosso non in grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-395">Applies non-bold/bright red to background</span></span>                          |
| <span data-ttu-id="6a2af-396">42</span><span class="sxs-lookup"><span data-stu-id="6a2af-396">42</span></span>    | <span data-ttu-id="6a2af-397">Verde sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-397">Background Green</span></span>          | <span data-ttu-id="6a2af-398">Applica il verde a sfondo non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-398">Applies non-bold/bright green to background</span></span>                        |
| <span data-ttu-id="6a2af-399">43</span><span class="sxs-lookup"><span data-stu-id="6a2af-399">43</span></span>    | <span data-ttu-id="6a2af-400">Sfondo giallo</span><span class="sxs-lookup"><span data-stu-id="6a2af-400">Background Yellow</span></span>         | <span data-ttu-id="6a2af-401">Applica lo sfondo al giallo non in grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-401">Applies non-bold/bright yellow to background</span></span>                       |
| <span data-ttu-id="6a2af-402">44</span><span class="sxs-lookup"><span data-stu-id="6a2af-402">44</span></span>    | <span data-ttu-id="6a2af-403">Blu sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-403">Background Blue</span></span>           | <span data-ttu-id="6a2af-404">Applica lo sfondo al blu non grassetto/luminoso</span><span class="sxs-lookup"><span data-stu-id="6a2af-404">Applies non-bold/bright blue to background</span></span>                         |
| <span data-ttu-id="6a2af-405">45</span><span class="sxs-lookup"><span data-stu-id="6a2af-405">45</span></span>    | <span data-ttu-id="6a2af-406">Sfondo Magenta</span><span class="sxs-lookup"><span data-stu-id="6a2af-406">Background Magenta</span></span>        | <span data-ttu-id="6a2af-407">Applica il magenta non grassetto/luminoso a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-407">Applies non-bold/bright magenta to background</span></span>                      |
| <span data-ttu-id="6a2af-408">46</span><span class="sxs-lookup"><span data-stu-id="6a2af-408">46</span></span>    | <span data-ttu-id="6a2af-409">Ciano sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-409">Background Cyan</span></span>           | <span data-ttu-id="6a2af-410">Applica lo sfondo al ciano non grassetto/luminoso</span><span class="sxs-lookup"><span data-stu-id="6a2af-410">Applies non-bold/bright cyan to background</span></span>                         |
| <span data-ttu-id="6a2af-411">47</span><span class="sxs-lookup"><span data-stu-id="6a2af-411">47</span></span>    | <span data-ttu-id="6a2af-412">Sfondo bianco</span><span class="sxs-lookup"><span data-stu-id="6a2af-412">Background White</span></span>          | <span data-ttu-id="6a2af-413">Applica lo sfondo al bianco non grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-413">Applies non-bold/bright white to background</span></span>                        |
| <span data-ttu-id="6a2af-414">48</span><span class="sxs-lookup"><span data-stu-id="6a2af-414">48</span></span>    | <span data-ttu-id="6a2af-415">Sfondo esteso</span><span class="sxs-lookup"><span data-stu-id="6a2af-415">Background Extended</span></span>       | <span data-ttu-id="6a2af-416">Applica il valore di colore esteso allo sfondo (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="6a2af-416">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="6a2af-417">49</span><span class="sxs-lookup"><span data-stu-id="6a2af-417">49</span></span>    | <span data-ttu-id="6a2af-418">Impostazione predefinita sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-418">Background Default</span></span>        | <span data-ttu-id="6a2af-419">Applica solo la parte in background delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="6a2af-419">Applies only the background portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="6a2af-420">90</span><span class="sxs-lookup"><span data-stu-id="6a2af-420">90</span></span>    | <span data-ttu-id="6a2af-421">Lucido nero in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-421">Bright Foreground Black</span></span>   | <span data-ttu-id="6a2af-422">Applica grassetto/nero brillante a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-422">Applies bold/bright black to foreground</span></span>                            |
| <span data-ttu-id="6a2af-423">91</span><span class="sxs-lookup"><span data-stu-id="6a2af-423">91</span></span>    | <span data-ttu-id="6a2af-424">Rosso in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-424">Bright Foreground Red</span></span>     | <span data-ttu-id="6a2af-425">Applica grassetto/rosso chiaro a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-425">Applies bold/bright red to foreground</span></span>                              |
| <span data-ttu-id="6a2af-426">92</span><span class="sxs-lookup"><span data-stu-id="6a2af-426">92</span></span>    | <span data-ttu-id="6a2af-427">Verde chiaro in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-427">Bright Foreground Green</span></span>   | <span data-ttu-id="6a2af-428">Applica grassetto/verde chiaro a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-428">Applies bold/bright green to foreground</span></span>                            |
| <span data-ttu-id="6a2af-429">93</span><span class="sxs-lookup"><span data-stu-id="6a2af-429">93</span></span>    | <span data-ttu-id="6a2af-430">Giallo chiaro in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-430">Bright Foreground Yellow</span></span>  | <span data-ttu-id="6a2af-431">Viene applicato in grassetto/giallo chiaro a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-431">Applies bold/bright yellow to foreground</span></span>                           |
| <span data-ttu-id="6a2af-432">94</span><span class="sxs-lookup"><span data-stu-id="6a2af-432">94</span></span>    | <span data-ttu-id="6a2af-433">Blu lucido in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-433">Bright Foreground Blue</span></span>    | <span data-ttu-id="6a2af-434">Applica grassetto/blu chiaro a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-434">Applies bold/bright blue to foreground</span></span>                             |
| <span data-ttu-id="6a2af-435">95</span><span class="sxs-lookup"><span data-stu-id="6a2af-435">95</span></span>    | <span data-ttu-id="6a2af-436">Magenta chiaro in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-436">Bright Foreground Magenta</span></span> | <span data-ttu-id="6a2af-437">Applica il magenta in grassetto o luminoso a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-437">Applies bold/bright magenta to foreground</span></span>                          |
| <span data-ttu-id="6a2af-438">96</span><span class="sxs-lookup"><span data-stu-id="6a2af-438">96</span></span>    | <span data-ttu-id="6a2af-439">Ciano in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-439">Bright Foreground Cyan</span></span>    | <span data-ttu-id="6a2af-440">Applica in primo piano grassetto/chiaro ciano</span><span class="sxs-lookup"><span data-stu-id="6a2af-440">Applies bold/bright cyan to foreground</span></span>                             |
| <span data-ttu-id="6a2af-441">97</span><span class="sxs-lookup"><span data-stu-id="6a2af-441">97</span></span>    | <span data-ttu-id="6a2af-442">Bianco in primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-442">Bright Foreground White</span></span>   | <span data-ttu-id="6a2af-443">Applica in grassetto/chiaro bianco a primo piano</span><span class="sxs-lookup"><span data-stu-id="6a2af-443">Applies bold/bright white to foreground</span></span>                            |
| <span data-ttu-id="6a2af-444">100</span><span class="sxs-lookup"><span data-stu-id="6a2af-444">100</span></span>   | <span data-ttu-id="6a2af-445">Sfondo luminoso nero</span><span class="sxs-lookup"><span data-stu-id="6a2af-445">Bright Background Black</span></span>   | <span data-ttu-id="6a2af-446">Applica il nero in grassetto/chiaro a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-446">Applies bold/bright black to background</span></span>                            |
| <span data-ttu-id="6a2af-447">101</span><span class="sxs-lookup"><span data-stu-id="6a2af-447">101</span></span>   | <span data-ttu-id="6a2af-448">Rosso sfondo chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-448">Bright Background Red</span></span>     | <span data-ttu-id="6a2af-449">Applica lo sfondo al rosso grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-449">Applies bold/bright red to background</span></span>                              |
| <span data-ttu-id="6a2af-450">102</span><span class="sxs-lookup"><span data-stu-id="6a2af-450">102</span></span>   | <span data-ttu-id="6a2af-451">Verde sfondo luminoso</span><span class="sxs-lookup"><span data-stu-id="6a2af-451">Bright Background Green</span></span>   | <span data-ttu-id="6a2af-452">Applica in grassetto/chiaro verde a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-452">Applies bold/bright green to background</span></span>                            |
| <span data-ttu-id="6a2af-453">103</span><span class="sxs-lookup"><span data-stu-id="6a2af-453">103</span></span>   | <span data-ttu-id="6a2af-454">Sfondo luminoso giallo</span><span class="sxs-lookup"><span data-stu-id="6a2af-454">Bright Background Yellow</span></span>  | <span data-ttu-id="6a2af-455">Applica in grassetto/giallo chiaro a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-455">Applies bold/bright yellow to background</span></span>                           |
| <span data-ttu-id="6a2af-456">104</span><span class="sxs-lookup"><span data-stu-id="6a2af-456">104</span></span>   | <span data-ttu-id="6a2af-457">Blu sfondo chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-457">Bright Background Blue</span></span>    | <span data-ttu-id="6a2af-458">Applica lo sfondo al blu grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-458">Applies bold/bright blue to background</span></span>                             |
| <span data-ttu-id="6a2af-459">105</span><span class="sxs-lookup"><span data-stu-id="6a2af-459">105</span></span>   | <span data-ttu-id="6a2af-460">Sfondo chiaro magenta</span><span class="sxs-lookup"><span data-stu-id="6a2af-460">Bright Background Magenta</span></span> | <span data-ttu-id="6a2af-461">Applica il magenta in grassetto/chiaro a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-461">Applies bold/bright magenta to background</span></span>                          |
| <span data-ttu-id="6a2af-462">106</span><span class="sxs-lookup"><span data-stu-id="6a2af-462">106</span></span>   | <span data-ttu-id="6a2af-463">Ciano sfondo chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-463">Bright Background Cyan</span></span>    | <span data-ttu-id="6a2af-464">Applica in grassetto/chiaro ciano a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-464">Applies bold/bright cyan to background</span></span>                             |
| <span data-ttu-id="6a2af-465">107</span><span class="sxs-lookup"><span data-stu-id="6a2af-465">107</span></span>   | <span data-ttu-id="6a2af-466">Bianco sfondo chiaro</span><span class="sxs-lookup"><span data-stu-id="6a2af-466">Bright Background White</span></span>   | <span data-ttu-id="6a2af-467">Applica in grassetto/chiaro bianco a sfondo</span><span class="sxs-lookup"><span data-stu-id="6a2af-467">Applies bold/bright white to background</span></span>                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="6a2af-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colori estesi</span><span class="sxs-lookup"><span data-stu-id="6a2af-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="6a2af-469">Alcuni emulatori di terminali virtuali supportano una tavolozza di colori maggiore dei 16 colori forniti dalla console di Windows.</span><span class="sxs-lookup"><span data-stu-id="6a2af-469">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="6a2af-470">Per questi colori estesi, la console di Windows sceglierà il colore appropriato più vicino dalla tabella 16 colori esistente per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-470">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="6a2af-471">A differenza dei valori di SGR tipici precedenti, i valori estesi utilizzeranno parametri aggiuntivi dopo l'indicatore iniziale in base alla tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-471">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="6a2af-472">Sottosequenza SGR</span><span class="sxs-lookup"><span data-stu-id="6a2af-472">SGR Subsequence</span></span>                            | <span data-ttu-id="6a2af-473">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-473">Description</span></span>                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-474">38; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-474">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="6a2af-475">Imposta il colore di primo piano sul valore RGB specificato nei &lt; &gt; parametri r, &lt; g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-475">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="6a2af-476">48; 2 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-476">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="6a2af-477">Imposta il colore di sfondo sul valore RGB specificato nei &lt; &gt; parametri r, &lt; g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-477">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="6a2af-478">38; 5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-478">38 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="6a2af-479">Imposta il colore di primo piano sull' &lt; &gt; Indice s nella tabella colori 88 o 256\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-479">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |
| <span data-ttu-id="6a2af-480">48; 5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-480">48 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="6a2af-481">Imposta il colore di sfondo sull' &lt; &gt; Indice s nella tabella colori 88 o 256\*</span><span class="sxs-lookup"><span data-stu-id="6a2af-481">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |



<span data-ttu-id="6a2af-482">\*Le tavolozze dei colori 88 e 256 gestite internamente per il confronto sono basate sull'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="6a2af-482">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="6a2af-483">Impossibile modificare le tabelle di confronto o di arrotondamento in questo momento.</span><span class="sxs-lookup"><span data-stu-id="6a2af-483">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="6a2af-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colori dello schermo</span><span class="sxs-lookup"><span data-stu-id="6a2af-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="6a2af-485">Il comando seguente consente all'applicazione di impostare i valori della tavolozza dei colori dello schermo su qualsiasi valore RGB.</span><span class="sxs-lookup"><span data-stu-id="6a2af-485">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="6a2af-486">I valori RGB devono essere valori esadecimali compresi tra `0` e `ff` e separati dal carattere barra rovesciata (ad esempio `rgb:1/24/86` ).</span><span class="sxs-lookup"><span data-stu-id="6a2af-486">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="6a2af-487">Si noti che questa sequenza è una sequenza di "comando del sistema operativo" OSC, non un CSI come molte delle altre sequenze elencate e che inizia con " \\ X1B \] ", non con " \\ X1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="6a2af-487">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="6a2af-488">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-488">Sequence</span></span>                                                           | <span data-ttu-id="6a2af-489">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-489">Description</span></span>          | <span data-ttu-id="6a2af-490">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-490">Behavior</span></span>                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-491">ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="6a2af-491">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="6a2af-492">Modificare i colori della schermata</span><span class="sxs-lookup"><span data-stu-id="6a2af-492">Modify Screen Colors</span></span> | <span data-ttu-id="6a2af-493">Imposta l'indice della tavolozza dei colori della schermata sui &lt; &gt; valori RGB specificati in &lt; r &gt; , &lt; g &gt; , &lt; b&gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-493">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="6a2af-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifiche della modalità</span><span class="sxs-lookup"><span data-stu-id="6a2af-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="6a2af-495">Si tratta di sequenze che controllano le modalità di input.</span><span class="sxs-lookup"><span data-stu-id="6a2af-495">These are sequences that control the input modes.</span></span> <span data-ttu-id="6a2af-496">Esistono due diversi set di modalità di input, ovvero la modalità dei tasti di cursore e la modalità dei tasti della tastiera.</span><span class="sxs-lookup"><span data-stu-id="6a2af-496">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="6a2af-497">La modalità dei tasti cursore controlla le sequenze generate dai tasti di direzione, nonché da Home e da fine, mentre la modalità tasti di tastiera controlla le sequenze emesse dalle chiavi del tastierino numerico principalmente, nonché i tasti funzione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-497">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="6a2af-498">Ognuna di queste modalità è una semplice impostazione booleana: la modalità di tasti cursore è normale (impostazione predefinita) o applicazione e la modalità tasti di tastiera è numerica (impostazione predefinita) o applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-498">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="6a2af-499">Vedere le sezioni tasti di cursore e tastierino numerico & tasti funzione per le sequenze emesse in queste modalità.</span><span class="sxs-lookup"><span data-stu-id="6a2af-499">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="6a2af-500">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-500">Sequence</span></span>     | <span data-ttu-id="6a2af-501">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-501">Code</span></span>    | <span data-ttu-id="6a2af-502">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-502">Description</span></span>                                            | <span data-ttu-id="6a2af-503">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-503">Behavior</span></span>                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="6a2af-504">ESC =</span><span class="sxs-lookup"><span data-stu-id="6a2af-504">ESC =</span></span>        | <span data-ttu-id="6a2af-505">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="6a2af-505">DECKPAM</span></span> | <span data-ttu-id="6a2af-506">Abilitare la modalità applicazione del tastierino</span><span class="sxs-lookup"><span data-stu-id="6a2af-506">Enable Keypad Application Mode</span></span>                         | <span data-ttu-id="6a2af-507">I tasti del tastierino emetteranno le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-507">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="6a2af-508">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="6a2af-508">ESC &gt;</span></span>     | <span data-ttu-id="6a2af-509">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="6a2af-509">DECKPNM</span></span> | <span data-ttu-id="6a2af-510">Abilita modalità numerica tastierino</span><span class="sxs-lookup"><span data-stu-id="6a2af-510">Enable Keypad Numeric Mode</span></span>                             | <span data-ttu-id="6a2af-511">I tasti della tastiera emetteranno le sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="6a2af-511">Keypad keys will emit their Numeric Mode sequences.</span></span>     |
| <span data-ttu-id="6a2af-512">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-512">ESC \[ ?</span></span> <span data-ttu-id="6a2af-513">1 ora</span><span class="sxs-lookup"><span data-stu-id="6a2af-513">1 h</span></span> | <span data-ttu-id="6a2af-514">DECCKM</span><span class="sxs-lookup"><span data-stu-id="6a2af-514">DECCKM</span></span>  | <span data-ttu-id="6a2af-515">Abilitare la modalità di applicazione delle chiavi del cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-515">Enable Cursor Keys Application Mode</span></span>                    | <span data-ttu-id="6a2af-516">I tasti del tastierino emetteranno le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-516">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="6a2af-517">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-517">ESC \[ ?</span></span> <span data-ttu-id="6a2af-518">1 l</span><span class="sxs-lookup"><span data-stu-id="6a2af-518">1 l</span></span> | <span data-ttu-id="6a2af-519">DECCKM</span><span class="sxs-lookup"><span data-stu-id="6a2af-519">DECCKM</span></span>  | <span data-ttu-id="6a2af-520">Disabilitare la modalità di applicazione delle chiavi del cursore (usare la modalità normale)</span><span class="sxs-lookup"><span data-stu-id="6a2af-520">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="6a2af-521">I tasti della tastiera emetteranno le sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="6a2af-521">Keypad keys will emit their Numeric Mode sequences.</span></span>     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="6a2af-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Stato query</span><span class="sxs-lookup"><span data-stu-id="6a2af-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="6a2af-523">Tutti i comandi in questa sezione sono in genere equivalenti alla chiamata di Get \* console API per recuperare informazioni sullo stato corrente del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="6a2af-523">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

<span data-ttu-id="6a2af-524">**Nota**  Queste query emetteranno le risposte nel flusso di input della console immediatamente dopo essere state riconosciute nel flusso di output mentre è stata ABILITAta l' \_ \_ elaborazione del terminale virtuale \_ .</span><span class="sxs-lookup"><span data-stu-id="6a2af-524">**Note**  These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="6a2af-525">Il \_ flag Enable virtual \_ Terminal input non \_ si applica ai comandi di query perché si presuppone che un'applicazione che esegue la query desideri ricevere sempre la risposta.</span><span class="sxs-lookup"><span data-stu-id="6a2af-525">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="6a2af-526">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-526">Sequence</span></span>   | <span data-ttu-id="6a2af-527">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-527">Code</span></span>    | <span data-ttu-id="6a2af-528">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-528">Description</span></span>            | <span data-ttu-id="6a2af-529">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-529">Behavior</span></span>                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-530">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="6a2af-530">ESC \[ 6 n</span></span> | <span data-ttu-id="6a2af-531">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="6a2af-531">DECXCPR</span></span> | <span data-ttu-id="6a2af-532">Posizione del cursore del report</span><span class="sxs-lookup"><span data-stu-id="6a2af-532">Report Cursor Position</span></span> | <span data-ttu-id="6a2af-533">Creare la posizione del cursore come: ESC \[ &lt; r &gt; ; &lt; c &gt; r dove &lt; R &gt; = riga cursore e &lt; c &gt; = colonna cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-533">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="6a2af-534">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="6a2af-534">ESC \[ 0 c</span></span> | <span data-ttu-id="6a2af-535">DA</span><span class="sxs-lookup"><span data-stu-id="6a2af-535">DA</span></span>      | <span data-ttu-id="6a2af-536">Attributi del dispositivo</span><span class="sxs-lookup"><span data-stu-id="6a2af-536">Device Attributes</span></span>      | <span data-ttu-id="6a2af-537">Segnala l'identità del terminale.</span><span class="sxs-lookup"><span data-stu-id="6a2af-537">Report the terminal identity.</span></span> <span data-ttu-id="6a2af-538">Emetterà " \\ X1B \[ ? 1; 0C", che indica "VT101 senza opzioni".</span><span class="sxs-lookup"><span data-stu-id="6a2af-538">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span>                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="6a2af-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Schede</span><span class="sxs-lookup"><span data-stu-id="6a2af-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="6a2af-540">Sebbene la console di Windows usi tradizionalmente le schede in modo da avere una larghezza esclusiva di otto caratteri, le \* applicazioni nix che usano determinate sequenze possono modificare il punto in cui si trovano le tabulazioni all'interno delle finestre della console per ottimizzare lo spostamento del cursore da parte dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-540">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="6a2af-541">Le sequenze seguenti consentono a un'applicazione di impostare i percorsi di tabulazione nella finestra della console, rimuoverli e spostarsi tra di essi.</span><span class="sxs-lookup"><span data-stu-id="6a2af-541">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="6a2af-542">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-542">Sequence</span></span>           | <span data-ttu-id="6a2af-543">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-543">Code</span></span> | <span data-ttu-id="6a2af-544">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-544">Description</span></span>                     | <span data-ttu-id="6a2af-545">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-545">Behavior</span></span>                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6a2af-546">ESC H</span><span class="sxs-lookup"><span data-stu-id="6a2af-546">ESC H</span></span>              | <span data-ttu-id="6a2af-547">HTS</span><span class="sxs-lookup"><span data-stu-id="6a2af-547">HTS</span></span>  | <span data-ttu-id="6a2af-548">Set di schede orizzontali</span><span class="sxs-lookup"><span data-stu-id="6a2af-548">Horizontal Tab Set</span></span>              | <span data-ttu-id="6a2af-549">Imposta un punto di tabulazione nella colonna corrente in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-549">Sets a tab stop in the current column the cursor is in.</span></span>                                                                                                                                                                     |
| <span data-ttu-id="6a2af-550">ESC \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="6a2af-550">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="6a2af-551">CHT</span><span class="sxs-lookup"><span data-stu-id="6a2af-551">CHT</span></span>  | <span data-ttu-id="6a2af-552">Scheda cursore orizzontale (in poi)</span><span class="sxs-lookup"><span data-stu-id="6a2af-552">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="6a2af-553">Spostare il cursore sulla colonna successiva (nella stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-553">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="6a2af-554">Se non sono presenti altre tabulazioni, passare all'ultima colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="6a2af-554">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="6a2af-555">Se il cursore si trova nell'ultima colonna, passare alla prima colonna della riga successiva.</span><span class="sxs-lookup"><span data-stu-id="6a2af-555">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="6a2af-556">ESC \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="6a2af-556">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="6a2af-557">CBT</span><span class="sxs-lookup"><span data-stu-id="6a2af-557">CBT</span></span>  | <span data-ttu-id="6a2af-558">Scheda cursore indietro</span><span class="sxs-lookup"><span data-stu-id="6a2af-558">Cursor Backwards Tab</span></span>            | <span data-ttu-id="6a2af-559">Spostare il cursore sulla colonna precedente (nella stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-559">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="6a2af-560">Se non sono presenti altre tabulazioni, sposta il cursore sulla prima colonna.</span><span class="sxs-lookup"><span data-stu-id="6a2af-560">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="6a2af-561">Se il cursore si trova nella prima colonna, il cursore non viene spostato.</span><span class="sxs-lookup"><span data-stu-id="6a2af-561">If the cursor is in the first column, doesn’t move the cursor.</span></span>              |
| <span data-ttu-id="6a2af-562">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="6a2af-562">ESC \[ 0 g</span></span>         | <span data-ttu-id="6a2af-563">TBC</span><span class="sxs-lookup"><span data-stu-id="6a2af-563">TBC</span></span>  | <span data-ttu-id="6a2af-564">Tabulazione cancellata (colonna corrente)</span><span class="sxs-lookup"><span data-stu-id="6a2af-564">Tab Clear (current column)</span></span>      | <span data-ttu-id="6a2af-565">Cancella la tabulazione nella colonna corrente, se presente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-565">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="6a2af-566">In caso contrario, non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-566">Otherwise does nothing.</span></span>                                                                                                                                         |
| <span data-ttu-id="6a2af-567">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="6a2af-567">ESC \[ 3 g</span></span>         | <span data-ttu-id="6a2af-568">TBC</span><span class="sxs-lookup"><span data-stu-id="6a2af-568">TBC</span></span>  | <span data-ttu-id="6a2af-569">Cancellazione tabulazione (tutte le colonne)</span><span class="sxs-lookup"><span data-stu-id="6a2af-569">Tab Clear (all columns)</span></span>         | <span data-ttu-id="6a2af-570">Cancella tutte le tabulazioni attualmente impostate.</span><span class="sxs-lookup"><span data-stu-id="6a2af-570">Clears all currently set tab stops.</span></span>                                                                                                                                                                                         |



- <span data-ttu-id="6a2af-571">Per CHT e CBT, &lt; n &gt; è un parametro facoltativo che (valore predefinito = 1) indica il numero di volte in cui avanzare il cursore nella direzione specificata.</span><span class="sxs-lookup"><span data-stu-id="6a2af-571">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="6a2af-572">Se non sono presenti interruzioni di tabulazioni impostate tramite HTS, CHT e CBT tratteranno la prima e l'ultima colonna della finestra come le uniche due schede arrestate.</span><span class="sxs-lookup"><span data-stu-id="6a2af-572">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="6a2af-573">Se si usa HTS per impostare una tabulazione, la console passa alla successiva tabulazione nell'output di un carattere di TABULAzione (0x09, " \\ t"), nello stesso modo in cui si configura cht.</span><span class="sxs-lookup"><span data-stu-id="6a2af-573">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="6a2af-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designare il set di caratteri</span><span class="sxs-lookup"><span data-stu-id="6a2af-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="6a2af-575">Le sequenze seguenti consentono a un programma di modificare il mapping del set di caratteri attivo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-575">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="6a2af-576">In questo modo un programma può emettere caratteri ASCII a 7 bit, ma è possibile visualizzarli come altri glifi nella schermata finale.</span><span class="sxs-lookup"><span data-stu-id="6a2af-576">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="6a2af-577">Attualmente, gli unici due set di caratteri supportati sono ASCII (impostazione predefinita) e il set di caratteri grafici DEC Special.</span><span class="sxs-lookup"><span data-stu-id="6a2af-577">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="6a2af-578"><http://vt100.net/docs/vt220-rm/table2-4.html>Per un elenco di tutti i caratteri rappresentati dal set di caratteri grafici Dec speciale, vedere.</span><span class="sxs-lookup"><span data-stu-id="6a2af-578">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="6a2af-579">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-579">Sequence</span></span> | <span data-ttu-id="6a2af-580">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-580">Description</span></span>                                | <span data-ttu-id="6a2af-581">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-581">Behavior</span></span>                      |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="6a2af-582">ESC (0</span><span class="sxs-lookup"><span data-stu-id="6a2af-582">ESC ( 0</span></span>  | <span data-ttu-id="6a2af-583">Designare il set di caratteri – disegno linea DEC</span><span class="sxs-lookup"><span data-stu-id="6a2af-583">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="6a2af-584">Abilita la modalità di disegno linea DEC</span><span class="sxs-lookup"><span data-stu-id="6a2af-584">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="6a2af-585">ESC (B</span><span class="sxs-lookup"><span data-stu-id="6a2af-585">ESC ( B</span></span>  | <span data-ttu-id="6a2af-586">Designare set di caratteri – US ASCII</span><span class="sxs-lookup"><span data-stu-id="6a2af-586">Designate Character Set – US ASCII</span></span>         | <span data-ttu-id="6a2af-587">Abilita la modalità ASCII (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="6a2af-587">Enables ASCII Mode (Default)</span></span>  |



<span data-ttu-id="6a2af-588">In particolare, la modalità di disegno linea DEC viene utilizzata per disegnare i bordi nelle applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="6a2af-588">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="6a2af-589">Nella tabella seguente viene illustrato il mapping di caratteri ASCII a cui è associato il carattere di disegno a linee.</span><span class="sxs-lookup"><span data-stu-id="6a2af-589">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="6a2af-590">Hex</span><span class="sxs-lookup"><span data-stu-id="6a2af-590">Hex</span></span>  | <span data-ttu-id="6a2af-591">ASCII</span><span class="sxs-lookup"><span data-stu-id="6a2af-591">ASCII</span></span> | <span data-ttu-id="6a2af-592">Disegno linea DEC</span><span class="sxs-lookup"><span data-stu-id="6a2af-592">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="6a2af-593">0x6A</span><span class="sxs-lookup"><span data-stu-id="6a2af-593">0x6a</span></span> | <span data-ttu-id="6a2af-594">j</span><span class="sxs-lookup"><span data-stu-id="6a2af-594">j</span></span>     | <span data-ttu-id="6a2af-595">┘</span><span class="sxs-lookup"><span data-stu-id="6a2af-595">┘</span></span>                |
| <span data-ttu-id="6a2af-596">0x6b</span><span class="sxs-lookup"><span data-stu-id="6a2af-596">0x6b</span></span> | <span data-ttu-id="6a2af-597">k</span><span class="sxs-lookup"><span data-stu-id="6a2af-597">k</span></span>     | <span data-ttu-id="6a2af-598">┐</span><span class="sxs-lookup"><span data-stu-id="6a2af-598">┐</span></span>                |
| <span data-ttu-id="6a2af-599">0x6C</span><span class="sxs-lookup"><span data-stu-id="6a2af-599">0x6c</span></span> | <span data-ttu-id="6a2af-600">l</span><span class="sxs-lookup"><span data-stu-id="6a2af-600">l</span></span>     | <span data-ttu-id="6a2af-601">┌</span><span class="sxs-lookup"><span data-stu-id="6a2af-601">┌</span></span>                |
| <span data-ttu-id="6a2af-602">0x6d</span><span class="sxs-lookup"><span data-stu-id="6a2af-602">0x6d</span></span> | <span data-ttu-id="6a2af-603">m</span><span class="sxs-lookup"><span data-stu-id="6a2af-603">m</span></span>     | <span data-ttu-id="6a2af-604">└</span><span class="sxs-lookup"><span data-stu-id="6a2af-604">└</span></span>                |
| <span data-ttu-id="6a2af-605">0x6e</span><span class="sxs-lookup"><span data-stu-id="6a2af-605">0x6e</span></span> | <span data-ttu-id="6a2af-606">n</span><span class="sxs-lookup"><span data-stu-id="6a2af-606">n</span></span>     | <span data-ttu-id="6a2af-607">┼</span><span class="sxs-lookup"><span data-stu-id="6a2af-607">┼</span></span>                |
| <span data-ttu-id="6a2af-608">0x71</span><span class="sxs-lookup"><span data-stu-id="6a2af-608">0x71</span></span> | <span data-ttu-id="6a2af-609">q</span><span class="sxs-lookup"><span data-stu-id="6a2af-609">q</span></span>     | <span data-ttu-id="6a2af-610">─</span><span class="sxs-lookup"><span data-stu-id="6a2af-610">─</span></span>                |
| <span data-ttu-id="6a2af-611">0x74</span><span class="sxs-lookup"><span data-stu-id="6a2af-611">0x74</span></span> | <span data-ttu-id="6a2af-612">t</span><span class="sxs-lookup"><span data-stu-id="6a2af-612">t</span></span>     | <span data-ttu-id="6a2af-613">├</span><span class="sxs-lookup"><span data-stu-id="6a2af-613">├</span></span>                |
| <span data-ttu-id="6a2af-614">0x75</span><span class="sxs-lookup"><span data-stu-id="6a2af-614">0x75</span></span> | <span data-ttu-id="6a2af-615">u</span><span class="sxs-lookup"><span data-stu-id="6a2af-615">u</span></span>     | <span data-ttu-id="6a2af-616">┤</span><span class="sxs-lookup"><span data-stu-id="6a2af-616">┤</span></span>                |
| <span data-ttu-id="6a2af-617">0x76</span><span class="sxs-lookup"><span data-stu-id="6a2af-617">0x76</span></span> | <span data-ttu-id="6a2af-618">v</span><span class="sxs-lookup"><span data-stu-id="6a2af-618">v</span></span>     | <span data-ttu-id="6a2af-619">┴</span><span class="sxs-lookup"><span data-stu-id="6a2af-619">┴</span></span>                |
| <span data-ttu-id="6a2af-620">0x77</span><span class="sxs-lookup"><span data-stu-id="6a2af-620">0x77</span></span> | <span data-ttu-id="6a2af-621">w</span><span class="sxs-lookup"><span data-stu-id="6a2af-621">w</span></span>     | <span data-ttu-id="6a2af-622">┬</span><span class="sxs-lookup"><span data-stu-id="6a2af-622">┬</span></span>                |
| <span data-ttu-id="6a2af-623">0x78</span><span class="sxs-lookup"><span data-stu-id="6a2af-623">0x78</span></span> | <span data-ttu-id="6a2af-624">x</span><span class="sxs-lookup"><span data-stu-id="6a2af-624">x</span></span>     | <span data-ttu-id="6a2af-625">│</span><span class="sxs-lookup"><span data-stu-id="6a2af-625">│</span></span>                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="6a2af-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scorrimento di margini</span><span class="sxs-lookup"><span data-stu-id="6a2af-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="6a2af-627">Le sequenze seguenti consentono a un programma di configurare la "regione di scorrimento" della schermata interessata dalle operazioni di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="6a2af-627">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="6a2af-628">Si tratta di un subset delle righe che vengono modificate quando lo scorrimento dello schermo viene eseguito, ad esempio, in un' \\ n'o un ri.</span><span class="sxs-lookup"><span data-stu-id="6a2af-628">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="6a2af-629">Questi margini influiscono anche sulle righe modificate da Inserisci riga (IL) e Elimina riga (DL), scorri verso l'alto (SU) e scorri verso il basso (SD).</span><span class="sxs-lookup"><span data-stu-id="6a2af-629">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="6a2af-630">I margini di scorrimento possono essere particolarmente utili per avere una parte dello schermo che non scorre quando il resto dello schermo viene riempito, ad esempio con una barra del titolo nella parte superiore o una barra di stato nella parte inferiore dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-630">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="6a2af-631">Per DECSTBM sono disponibili due parametri facoltativi, &lt; t &gt; e &lt; b &gt; , che vengono usati per specificare le righe che rappresentano le righe superiore e inferiore dell'area di scorrimento, incluse.</span><span class="sxs-lookup"><span data-stu-id="6a2af-631">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="6a2af-632">Se i parametri vengono omessi, per impostazione predefinita viene impostato su &lt; &gt; 1 e &lt; b &gt; l'altezza del viewport corrente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-632">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="6a2af-633">I margini di scorrimento sono per buffer, quindi è importante che il buffer alternativo e il buffer principale gestiscano le impostazioni dei margini di scorrimento separati (pertanto un'applicazione a schermo intero nel buffer alternativo non avvelena i margini del buffer principale).</span><span class="sxs-lookup"><span data-stu-id="6a2af-633">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="6a2af-634">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-634">Sequence</span></span>                       | <span data-ttu-id="6a2af-635">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-635">Code</span></span>    | <span data-ttu-id="6a2af-636">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-636">Description</span></span>          | <span data-ttu-id="6a2af-637">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-637">Behavior</span></span>                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="6a2af-638">ESC \[ &lt; t &gt; ; &lt; b &gt; r</span><span class="sxs-lookup"><span data-stu-id="6a2af-638">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="6a2af-639">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="6a2af-639">DECSTBM</span></span> | <span data-ttu-id="6a2af-640">Imposta area di scorrimento</span><span class="sxs-lookup"><span data-stu-id="6a2af-640">Set Scrolling Region</span></span> | <span data-ttu-id="6a2af-641">Imposta i margini di scorrimento del VT del viewport.</span><span class="sxs-lookup"><span data-stu-id="6a2af-641">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="6a2af-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titolo della finestra</span><span class="sxs-lookup"><span data-stu-id="6a2af-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="6a2af-643">I comandi seguenti consentono all'applicazione di impostare il titolo della finestra della console sul parametro di &lt; stringa specificato &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-643">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="6a2af-644">Per essere accettata, la stringa deve contenere meno di 255 caratteri.</span><span class="sxs-lookup"><span data-stu-id="6a2af-644">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="6a2af-645">Equivale a chiamare SetConsoleTitle con la stringa specificata.</span><span class="sxs-lookup"><span data-stu-id="6a2af-645">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="6a2af-646">Si noti che queste sequenze sono "Command del sistema operativo" e non un CSI come molte delle altre sequenze elencate e che inizia con " \\ X1B \] ", non con " \\ X1B \[ ".</span><span class="sxs-lookup"><span data-stu-id="6a2af-646">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="6a2af-647">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-647">Sequence</span></span>                      | <span data-ttu-id="6a2af-648">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-648">Description</span></span>               | <span data-ttu-id="6a2af-649">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-649">Behavior</span></span>                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="6a2af-650">ESC \] 0; &lt; stringa &gt; bel</span><span class="sxs-lookup"><span data-stu-id="6a2af-650">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="6a2af-651">Imposta icona e titolo finestra</span><span class="sxs-lookup"><span data-stu-id="6a2af-651">Set Icon and Window Title</span></span> | <span data-ttu-id="6a2af-652">Imposta il titolo della finestra della console su &lt; stringa &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-652">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="6a2af-653">ESC \] 2; &lt; stringa &gt; bel</span><span class="sxs-lookup"><span data-stu-id="6a2af-653">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="6a2af-654">Imposta titolo finestra</span><span class="sxs-lookup"><span data-stu-id="6a2af-654">Set Window Title</span></span>          | <span data-ttu-id="6a2af-655">Imposta il titolo della finestra della console su &lt; stringa &gt; .</span><span class="sxs-lookup"><span data-stu-id="6a2af-655">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="6a2af-656">Il carattere di terminazione qui è il carattere "campanello", " \\ x07"</span><span class="sxs-lookup"><span data-stu-id="6a2af-656">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="6a2af-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Buffer dello schermo alternativo</span><span class="sxs-lookup"><span data-stu-id="6a2af-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="6a2af-658">\*Le applicazioni in stile nix spesso utilizzano un buffer dello schermo alternativo, in modo che possano modificare l'intero contenuto del buffer, senza influire sull'applicazione che l'ha avviata.</span><span class="sxs-lookup"><span data-stu-id="6a2af-658">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="6a2af-659">Il buffer alternativo è esattamente le dimensioni della finestra, senza alcuna area scrollback.</span><span class="sxs-lookup"><span data-stu-id="6a2af-659">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="6a2af-660">Per un esempio di questo comportamento, si prenda in considerazione quando VIM viene avviato da bash.</span><span class="sxs-lookup"><span data-stu-id="6a2af-660">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="6a2af-661">Vim usa l'intero schermo per modificare il file e quindi il ritorno a bash lascia invariato il buffer originale.</span><span class="sxs-lookup"><span data-stu-id="6a2af-661">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="6a2af-662">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-662">Sequence</span></span>           | <span data-ttu-id="6a2af-663">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-663">Description</span></span>                 | <span data-ttu-id="6a2af-664">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-664">Behavior</span></span>                                   |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="6a2af-665">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-665">ESC \[ ?</span></span> <span data-ttu-id="6a2af-666">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="6a2af-666">1 0 4 9 h</span></span> | <span data-ttu-id="6a2af-667">Usa buffer schermato alternativo</span><span class="sxs-lookup"><span data-stu-id="6a2af-667">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="6a2af-668">Passa a un nuovo buffer dello schermo alternativo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-668">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="6a2af-669">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-669">ESC \[ ?</span></span> <span data-ttu-id="6a2af-670">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="6a2af-670">1 0 4 9 l</span></span> | <span data-ttu-id="6a2af-671">Usa buffer dello schermo principale</span><span class="sxs-lookup"><span data-stu-id="6a2af-671">Use Main Screen Buffer</span></span>      | <span data-ttu-id="6a2af-672">Passa al buffer principale.</span><span class="sxs-lookup"><span data-stu-id="6a2af-672">Switches to the main buffer.</span></span>               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="6a2af-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Larghezza finestra</span><span class="sxs-lookup"><span data-stu-id="6a2af-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="6a2af-674">Le sequenze seguenti possono essere utilizzate per controllare la larghezza della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="6a2af-674">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="6a2af-675">Sono approssimativamente equivalenti al chiamante dell'API della console SetConsoleScreenBufferInfoEx per impostare la larghezza della finestra.</span><span class="sxs-lookup"><span data-stu-id="6a2af-675">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="6a2af-676">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-676">Sequence</span></span>     | <span data-ttu-id="6a2af-677">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-677">Code</span></span>    | <span data-ttu-id="6a2af-678">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-678">Description</span></span>                  | <span data-ttu-id="6a2af-679">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-679">Behavior</span></span>                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="6a2af-680">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-680">ESC \[ ?</span></span> <span data-ttu-id="6a2af-681">3 ore</span><span class="sxs-lookup"><span data-stu-id="6a2af-681">3 h</span></span> | <span data-ttu-id="6a2af-682">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="6a2af-682">DECCOLM</span></span> | <span data-ttu-id="6a2af-683">Imposta il numero di colonne su 132</span><span class="sxs-lookup"><span data-stu-id="6a2af-683">Set Number of Columns to 132</span></span> | <span data-ttu-id="6a2af-684">Imposta la larghezza della console su una larghezza di 132 colonne.</span><span class="sxs-lookup"><span data-stu-id="6a2af-684">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="6a2af-685">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="6a2af-685">ESC \[ ?</span></span> <span data-ttu-id="6a2af-686">3 l</span><span class="sxs-lookup"><span data-stu-id="6a2af-686">3 l</span></span> | <span data-ttu-id="6a2af-687">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="6a2af-687">DECCOLM</span></span> | <span data-ttu-id="6a2af-688">Imposta il numero di colonne su 80</span><span class="sxs-lookup"><span data-stu-id="6a2af-688">Set Number of Columns to 80</span></span>  | <span data-ttu-id="6a2af-689">Imposta la larghezza della console su una larghezza di 80 colonne.</span><span class="sxs-lookup"><span data-stu-id="6a2af-689">Sets the console width to 80 columns wide.</span></span>  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="6a2af-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Ripristino soft</span><span class="sxs-lookup"><span data-stu-id="6a2af-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="6a2af-691">La sequenza seguente può essere utilizzata per reimpostare i valori predefiniti di determinate proprietà. Le proprietà seguenti vengono reimpostate sui valori predefiniti seguenti (sono elencate anche le sequenze che controllano tali proprietà):</span><span class="sxs-lookup"><span data-stu-id="6a2af-691">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="6a2af-692">Visibilità cursore: visibile (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="6a2af-692">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="6a2af-693">Tastierino numerico: modalità numerica (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="6a2af-693">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="6a2af-694">Modalità tasti di cursore: modalità normale (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="6a2af-694">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="6a2af-695">Margini superiore e inferiore: superiore = 1, inferiore = altezza Console (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="6a2af-695">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="6a2af-696">Set di caratteri: US ASCII</span><span class="sxs-lookup"><span data-stu-id="6a2af-696">Character Set: US ASCII</span></span>
- <span data-ttu-id="6a2af-697">Rendering della grafica: default/off (SGR)</span><span class="sxs-lookup"><span data-stu-id="6a2af-697">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="6a2af-698">Salva stato cursore: posizione Home (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="6a2af-698">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="6a2af-699">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-699">Sequence</span></span>   | <span data-ttu-id="6a2af-700">Codice</span><span class="sxs-lookup"><span data-stu-id="6a2af-700">Code</span></span>   | <span data-ttu-id="6a2af-701">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6a2af-701">Description</span></span> | <span data-ttu-id="6a2af-702">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a2af-702">Behavior</span></span>                                           |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="6a2af-703">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="6a2af-703">ESC \[ !</span></span> <span data-ttu-id="6a2af-704">p</span><span class="sxs-lookup"><span data-stu-id="6a2af-704">p</span></span> | <span data-ttu-id="6a2af-705">DECSTR</span><span class="sxs-lookup"><span data-stu-id="6a2af-705">DECSTR</span></span> | <span data-ttu-id="6a2af-706">Ripristino soft</span><span class="sxs-lookup"><span data-stu-id="6a2af-706">Soft Reset</span></span>  | <span data-ttu-id="6a2af-707">Ripristinare le impostazioni predefinite di determinate impostazioni del terminale.</span><span class="sxs-lookup"><span data-stu-id="6a2af-707">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="6a2af-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Sequenze di input</span><span class="sxs-lookup"><span data-stu-id="6a2af-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="6a2af-709">Le sequenze di terminali seguenti vengono emesse dall'host della console nel flusso di input se il flag di ABILITAzione del \_ terminale virtuale di input \_ \_ viene impostato sull'handle del buffer di input usando il flag SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="6a2af-709">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="6a2af-710">Sono disponibili due modalità interne che controllano le sequenze emesse per le chiavi di input specificate, la modalità dei tasti di cursore e la modalità dei tasti della tastiera.</span><span class="sxs-lookup"><span data-stu-id="6a2af-710">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="6a2af-711">Questi sono descritti nella sezione modifiche della modalità.</span><span class="sxs-lookup"><span data-stu-id="6a2af-711">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="6a2af-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Tasti di cursore</span><span class="sxs-lookup"><span data-stu-id="6a2af-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="6a2af-713">Chiave</span><span class="sxs-lookup"><span data-stu-id="6a2af-713">Key</span></span>         | <span data-ttu-id="6a2af-714">Modalità normale</span><span class="sxs-lookup"><span data-stu-id="6a2af-714">Normal Mode</span></span> | <span data-ttu-id="6a2af-715">Modalità applicazione</span><span class="sxs-lookup"><span data-stu-id="6a2af-715">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="6a2af-716">Freccia SU</span><span class="sxs-lookup"><span data-stu-id="6a2af-716">Up Arrow</span></span>    | <span data-ttu-id="6a2af-717">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="6a2af-717">ESC \[ A</span></span>    | <span data-ttu-id="6a2af-718">ESC O A</span><span class="sxs-lookup"><span data-stu-id="6a2af-718">ESC O A</span></span>          |
| <span data-ttu-id="6a2af-719">Freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="6a2af-719">Down Arrow</span></span>  | <span data-ttu-id="6a2af-720">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="6a2af-720">ESC \[ B</span></span>    | <span data-ttu-id="6a2af-721">ESC O B</span><span class="sxs-lookup"><span data-stu-id="6a2af-721">ESC O B</span></span>          |
| <span data-ttu-id="6a2af-722">Freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="6a2af-722">Right Arrow</span></span> | <span data-ttu-id="6a2af-723">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="6a2af-723">ESC \[ C</span></span>    | <span data-ttu-id="6a2af-724">ESC O C</span><span class="sxs-lookup"><span data-stu-id="6a2af-724">ESC O C</span></span>          |
| <span data-ttu-id="6a2af-725">Freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="6a2af-725">Left Arrow</span></span>  | <span data-ttu-id="6a2af-726">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="6a2af-726">ESC \[ D</span></span>    | <span data-ttu-id="6a2af-727">ESC O D</span><span class="sxs-lookup"><span data-stu-id="6a2af-727">ESC O D</span></span>          |
| <span data-ttu-id="6a2af-728">Home page</span><span class="sxs-lookup"><span data-stu-id="6a2af-728">Home</span></span>        | <span data-ttu-id="6a2af-729">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="6a2af-729">ESC \[ H</span></span>    | <span data-ttu-id="6a2af-730">ESC O H</span><span class="sxs-lookup"><span data-stu-id="6a2af-730">ESC O H</span></span>          |
| <span data-ttu-id="6a2af-731">Fine</span><span class="sxs-lookup"><span data-stu-id="6a2af-731">End</span></span>         | <span data-ttu-id="6a2af-732">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="6a2af-732">ESC \[ F</span></span>    | <span data-ttu-id="6a2af-733">ESC O F</span><span class="sxs-lookup"><span data-stu-id="6a2af-733">ESC O F</span></span>          |



<span data-ttu-id="6a2af-734">Inoltre, se si preme CTRL con una qualsiasi di queste chiavi, vengono generate le sequenze seguenti, indipendentemente dalla modalità dei tasti di cursore:</span><span class="sxs-lookup"><span data-stu-id="6a2af-734">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="6a2af-735">Chiave</span><span class="sxs-lookup"><span data-stu-id="6a2af-735">Key</span></span>                | <span data-ttu-id="6a2af-736">Qualsiasi modalità</span><span class="sxs-lookup"><span data-stu-id="6a2af-736">Any Mode</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="6a2af-737">CTRL + freccia su</span><span class="sxs-lookup"><span data-stu-id="6a2af-737">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="6a2af-738">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="6a2af-738">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="6a2af-739">CTRL + freccia giù</span><span class="sxs-lookup"><span data-stu-id="6a2af-739">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="6a2af-740">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="6a2af-740">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="6a2af-741">CTRL + freccia destra</span><span class="sxs-lookup"><span data-stu-id="6a2af-741">Ctrl + Right Arrow</span></span> | <span data-ttu-id="6a2af-742">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="6a2af-742">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="6a2af-743">CTRL + freccia sinistra</span><span class="sxs-lookup"><span data-stu-id="6a2af-743">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="6a2af-744">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="6a2af-744">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="6a2af-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Tastierino numerico & tasti funzione</span><span class="sxs-lookup"><span data-stu-id="6a2af-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="6a2af-746">Chiave</span><span class="sxs-lookup"><span data-stu-id="6a2af-746">Key</span></span>       | <span data-ttu-id="6a2af-747">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-747">Sequence</span></span>     |
|-----------|--------------|
| <span data-ttu-id="6a2af-748">Backspace</span><span class="sxs-lookup"><span data-stu-id="6a2af-748">Backspace</span></span> | <span data-ttu-id="6a2af-749">0x7F (CANC)</span><span class="sxs-lookup"><span data-stu-id="6a2af-749">0x7f (DEL)</span></span>   |
| <span data-ttu-id="6a2af-750">Sospendi</span><span class="sxs-lookup"><span data-stu-id="6a2af-750">Pause</span></span>     | <span data-ttu-id="6a2af-751">0x1A (SUB)</span><span class="sxs-lookup"><span data-stu-id="6a2af-751">0x1a (SUB)</span></span>   |
| <span data-ttu-id="6a2af-752">Carattere speciale di escape</span><span class="sxs-lookup"><span data-stu-id="6a2af-752">Escape</span></span>    | <span data-ttu-id="6a2af-753">0x1B (ESC)</span><span class="sxs-lookup"><span data-stu-id="6a2af-753">0x1b (ESC)</span></span>   |
| <span data-ttu-id="6a2af-754">Insert</span><span class="sxs-lookup"><span data-stu-id="6a2af-754">Insert</span></span>    | <span data-ttu-id="6a2af-755">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-755">ESC \[ 2 ~</span></span>   |
| <span data-ttu-id="6a2af-756">Elimina</span><span class="sxs-lookup"><span data-stu-id="6a2af-756">Delete</span></span>    | <span data-ttu-id="6a2af-757">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-757">ESC \[ 3 ~</span></span>   |
| <span data-ttu-id="6a2af-758">PGSU</span><span class="sxs-lookup"><span data-stu-id="6a2af-758">Page Up</span></span>   | <span data-ttu-id="6a2af-759">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-759">ESC \[ 5 ~</span></span>   |
| <span data-ttu-id="6a2af-760">PGGIÙ</span><span class="sxs-lookup"><span data-stu-id="6a2af-760">Page Down</span></span> | <span data-ttu-id="6a2af-761">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-761">ESC \[ 6 ~</span></span>   |
| <span data-ttu-id="6a2af-762">F1</span><span class="sxs-lookup"><span data-stu-id="6a2af-762">F1</span></span>        | <span data-ttu-id="6a2af-763">ESC O P</span><span class="sxs-lookup"><span data-stu-id="6a2af-763">ESC O P</span></span>      |
| <span data-ttu-id="6a2af-764">F2</span><span class="sxs-lookup"><span data-stu-id="6a2af-764">F2</span></span>        | <span data-ttu-id="6a2af-765">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="6a2af-765">ESC O Q</span></span>      |
| <span data-ttu-id="6a2af-766">F3</span><span class="sxs-lookup"><span data-stu-id="6a2af-766">F3</span></span>        | <span data-ttu-id="6a2af-767">ESC O R</span><span class="sxs-lookup"><span data-stu-id="6a2af-767">ESC O R</span></span>      |
| <span data-ttu-id="6a2af-768">F4</span><span class="sxs-lookup"><span data-stu-id="6a2af-768">F4</span></span>        | <span data-ttu-id="6a2af-769">ESC O S</span><span class="sxs-lookup"><span data-stu-id="6a2af-769">ESC O S</span></span>      |
| <span data-ttu-id="6a2af-770">F5</span><span class="sxs-lookup"><span data-stu-id="6a2af-770">F5</span></span>        | <span data-ttu-id="6a2af-771">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-771">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="6a2af-772">F6</span><span class="sxs-lookup"><span data-stu-id="6a2af-772">F6</span></span>        | <span data-ttu-id="6a2af-773">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-773">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="6a2af-774">F7</span><span class="sxs-lookup"><span data-stu-id="6a2af-774">F7</span></span>        | <span data-ttu-id="6a2af-775">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-775">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="6a2af-776">F8</span><span class="sxs-lookup"><span data-stu-id="6a2af-776">F8</span></span>        | <span data-ttu-id="6a2af-777">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-777">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="6a2af-778">F9</span><span class="sxs-lookup"><span data-stu-id="6a2af-778">F9</span></span>        | <span data-ttu-id="6a2af-779">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-779">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="6a2af-780">F10</span><span class="sxs-lookup"><span data-stu-id="6a2af-780">F10</span></span>       | <span data-ttu-id="6a2af-781">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-781">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="6a2af-782">F11</span><span class="sxs-lookup"><span data-stu-id="6a2af-782">F11</span></span>       | <span data-ttu-id="6a2af-783">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-783">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="6a2af-784">F12</span><span class="sxs-lookup"><span data-stu-id="6a2af-784">F12</span></span>       | <span data-ttu-id="6a2af-785">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="6a2af-785">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="6a2af-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificatori</span><span class="sxs-lookup"><span data-stu-id="6a2af-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="6a2af-787">ALT viene trattato anteponendo la sequenza con un carattere di escape: ESC &lt; c &gt; dove &lt; c &gt; è il carattere passato dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-787">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="6a2af-788">ALT + CTRL viene gestito allo stesso modo, ad eccezione del fatto che il sistema operativo avrà già spostato &lt; il &gt; tasto c sul carattere di controllo appropriato che verrà inoltrato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-788">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="6a2af-789">La combinazione di tasti CTRL viene in genere passata esattamente come ricevuta dal sistema.</span><span class="sxs-lookup"><span data-stu-id="6a2af-789">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="6a2af-790">Si tratta in genere di un singolo carattere spostato nello spazio riservato dei caratteri di controllo (0x0-0x1F).</span><span class="sxs-lookup"><span data-stu-id="6a2af-790">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="6a2af-791">Ad esempio, Ctrl + @ (0x40) diventa NUL (0x00), CTRL + \[ (0x5b) diventa ESC (0x1B) e così via. Alcune combinazioni di tasti CTRL vengono trattate in modo speciale in base alla tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="6a2af-791">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="6a2af-792">Chiave</span><span class="sxs-lookup"><span data-stu-id="6a2af-792">Key</span></span>                | <span data-ttu-id="6a2af-793">Sequenza</span><span class="sxs-lookup"><span data-stu-id="6a2af-793">Sequence</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="6a2af-794">CTRL+BARRA SPAZIATRICE</span><span class="sxs-lookup"><span data-stu-id="6a2af-794">Ctrl + Space</span></span>       | <span data-ttu-id="6a2af-795">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="6a2af-795">0x00 (NUL)</span></span>     |
| <span data-ttu-id="6a2af-796">CTRL + freccia su</span><span class="sxs-lookup"><span data-stu-id="6a2af-796">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="6a2af-797">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="6a2af-797">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="6a2af-798">CTRL + freccia giù</span><span class="sxs-lookup"><span data-stu-id="6a2af-798">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="6a2af-799">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="6a2af-799">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="6a2af-800">CTRL + freccia destra</span><span class="sxs-lookup"><span data-stu-id="6a2af-800">Ctrl + Right Arrow</span></span> | <span data-ttu-id="6a2af-801">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="6a2af-801">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="6a2af-802">CTRL + freccia sinistra</span><span class="sxs-lookup"><span data-stu-id="6a2af-802">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="6a2af-803">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="6a2af-803">ESC \[ 1 ; 5 D</span></span> |



<span data-ttu-id="6a2af-804">**Nota**  Il tasto CTRL + freccia destra viene considerato come AltGr.</span><span class="sxs-lookup"><span data-stu-id="6a2af-804">**Note**  Left Ctrl + Right Alt is treated as AltGr.</span></span> <span data-ttu-id="6a2af-805">Quando entrambi gli elementi vengono visualizzati insieme, verranno rimossi e il valore Unicode del carattere presentato dal sistema verrà passato nella destinazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-805">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="6a2af-806">Il sistema effettuerà la pre-conversione dei valori di AltGr in base alle impostazioni di input di sistema correnti.</span><span class="sxs-lookup"><span data-stu-id="6a2af-806">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="6a2af-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Campioni</span><span class="sxs-lookup"><span data-stu-id="6a2af-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="6a2af-808"><span id="example"></span><span id="EXAMPLE"></span>Esempio di sequenze di terminali SGR</span><span class="sxs-lookup"><span data-stu-id="6a2af-808"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="6a2af-809">Nel codice riportato di seguito vengono forniti alcuni esempi di formattazione del testo.</span><span class="sxs-lookup"><span data-stu-id="6a2af-809">The following code provides several examples of text formatting.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return GetLastError();
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return GetLastError();
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return GetLastError();
    }

    // Try some Set Graphics Rendition (SGR) terminal escape sequences
    wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
    wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
    wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
    wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
    wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
    wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
    wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
    wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

    return 0;
}
```

<span data-ttu-id="6a2af-810">**Nota**  Nell'esempio precedente, la stringa ' `\x1b[31m` ' è l'implementazione di **ESC \[ &lt; n &gt; m** con &lt; n &gt; è 31.</span><span class="sxs-lookup"><span data-stu-id="6a2af-810">**Note**  In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="6a2af-811">Il grafico seguente mostra l'output dell'esempio di codice precedente.</span><span class="sxs-lookup"><span data-stu-id="6a2af-811">The following graphic shows the output of the previous code example.</span></span>

![output della console con il comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="6a2af-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Esempio di abilitazione dell'elaborazione di terminali virtuali</span><span class="sxs-lookup"><span data-stu-id="6a2af-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="6a2af-814">Il codice seguente fornisce un esempio della modalità consigliata per abilitare l'elaborazione di terminali virtuali per un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6a2af-814">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="6a2af-815">Lo scopo dell'esempio è illustrare:</span><span class="sxs-lookup"><span data-stu-id="6a2af-815">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="6a2af-816">La modalità esistente deve sempre essere recuperata tramite GetConsoleMode e analizzata prima di essere impostata con SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="6a2af-816">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="6a2af-817">Il controllo della restituzione `0` di SetConsoleMode e di GetLastError restituisce uno stato \_ non valido \_ del parametro è il meccanismo corrente per determinare quando viene eseguito in un sistema di livello inferiore.</span><span class="sxs-lookup"><span data-stu-id="6a2af-817">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="6a2af-818">Un parametro dell'applicazione che riceve lo stato \_ non valido \_ con uno dei flag della modalità console più recenti nel campo di bit dovrebbe ridurre normalmente il comportamento e riprovare.</span><span class="sxs-lookup"><span data-stu-id="6a2af-818">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }
    HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
    if (hIn == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwOriginalOutMode = 0;
    DWORD dwOriginalInMode = 0;
    if (!GetConsoleMode(hOut, &dwOriginalOutMode))
    {
        return false;
    }
    if (!GetConsoleMode(hIn, &dwOriginalInMode))
    {
        return false;
    }

    DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
    DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

    DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
    if (!SetConsoleMode(hOut, dwOutMode))
    {
        // we failed to set both modes, try to step down mode gracefully.
        dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
        dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
        if (!SetConsoleMode(hOut, dwOutMode))
        {
            // Failed to set any VT mode, can't do anything here.
            return -1;
        }
    }

    DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
    if (!SetConsoleMode(hIn, dwInMode))
    {
        // Failed to set VT input mode, can't do anything here.
        return -1;
    }

    return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="6a2af-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Esempio di funzionalità di aggiornamento dell'anniversario selezionato</span><span class="sxs-lookup"><span data-stu-id="6a2af-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="6a2af-820">L'esempio seguente è destinato a essere un esempio più affidabile di codice che usa una serie di sequenze di escape per modificare il buffer, con particolare attenzione alle funzionalità aggiunte nell'aggiornamento dell'anniversario per Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6a2af-820">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="6a2af-821">Questo esempio usa il buffer dello schermo alternativo, la modifica delle tabulazioni, l'impostazione dei margini di scorrimento e la modifica del set di caratteri.</span><span class="sxs-lookup"><span data-stu-id="6a2af-821">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
//    Copyright (C) Microsoft.  All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return false;
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return false;
    }
    return true;
}

void PrintVerticalBorder()
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");   // bright yellow on bright blue
    printf("x");            // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m");       // restore color
    printf(ESC "(B");       // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");  // Make the border bright yellow on bright blue
    printf(fIsTop? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++) 
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B");       // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
{
    printf(CSI "%d;1H", Size.Y);
    printf(CSI "K"); // clear the line
    printf(pszMessage);  
}

int __cdecl wmain(int argc, WCHAR* argv[])
{   
    argc; // unused
    argv; // unused
    //First, enable VT mode
    bool fSuccess = EnableVTMode();
    if (!fSuccess)
    {
        printf("Unable to enter VT processing mode. Quitting.\n");
        return -1;
    }
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        printf("Couldn't get the console handle. Quitting.\n");
        return -1;
    }

    CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
    GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
    COORD Size;
    Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
    Size.Y = ScreenBufferInfo.srWindow.Bottom -  ScreenBufferInfo.srWindow.Top + 1;

    // Enter the alternate buffer
    printf(CSI "?1049h");

    // Clear screen, tab stops, set, stop at columns 16, 32
    printf(CSI "1;1H");
    printf(CSI "2J"); // Clear screen

    int iNumTabStops = 4; // (0, 20, 40, width)
    printf(CSI "3g"); // clear all tab stops
    printf(CSI "1;20H"); // Move to column 20
    printf(ESC "H"); // set a tab stop

    printf(CSI "1;40H"); // Move to column 40
    printf(ESC "H"); // set a tab stop

    // Set scrolling margins to 3, h-2
    printf(CSI "3;%dr", Size.Y-2);
    int iNumLines = Size.Y - 4;

    printf(CSI "1;1H");
    printf(CSI "102;30m");
    printf("Windows 10 Anniversary Update - VT Example"); 
    printf(CSI "0m");

    // Print a top border - Yellow
    printf(CSI "2;1H");
    PrintHorizontalBorder(Size, true);

    // // Print a bottom border
    printf(CSI "%d;1H", Size.Y-1);
    PrintHorizontalBorder(Size, false);

    wchar_t wch;

    // draw columns
    printf(CSI "3;1H"); 
    int line = 0;
    for (line = 0; line < iNumLines * iNumTabStops; line++)
    {
        PrintVerticalBorder();
        if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
            printf("\t"); // advance to next tab stop

    }

    PrintStatusLine("Press any key to see text printed between tab stops.", Size);
    wch = _getwch();

    // Fill columns with output
    printf(CSI "3;1H"); 
    for (line = 0; line < iNumLines; line++)
    {
        int tab = 0;
        for (tab = 0; tab < iNumTabStops-1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder();// print border at right side
        if (line+1 != iNumLines)
            printf("\t"); // advance to next tab stop, (on the next line)
    }

    PrintStatusLine("Press any key to demonstrate scroll margins", Size);
    wch = _getwch();

    printf(CSI "3;1H"); 
    for (line = 0; line < iNumLines * 2; line++)
    {
        printf(CSI "K"); // clear the line
        int tab = 0;
        for (tab = 0; tab < iNumTabStops-1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder(); // print border at right side
        if (line+1 != iNumLines * 2)
        {
            printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
            printf("\r"); //return to first col in buffer
        }
    }

    PrintStatusLine("Press any key to exit", Size);
    wch = _getwch();

    // Exit the alternate buffer
    printf(CSI "?1049l");

}
```








