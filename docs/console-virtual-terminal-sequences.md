---
title: Sequenze del terminale virtuale della console
description: Le sequenze di terminale virtuale sono sequenze di caratteri di controllo in grado di controllare lo spostamento del cursore, la modalità colore/tipo di carattere e altre operazioni quando vengono scritte nel flusso di output.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 29c1cc65db5e20c35ca0aaf6dc58c6e485d0edc6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358131"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="2ab27-104">Sequenze del terminale virtuale della console</span><span class="sxs-lookup"><span data-stu-id="2ab27-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="2ab27-105">Le sequenze di terminale virtuale sono sequenze di caratteri di controllo in grado di controllare lo spostamento del cursore, la modalità colore/tipo di carattere e altre operazioni quando vengono scritte nel flusso di output.</span><span class="sxs-lookup"><span data-stu-id="2ab27-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="2ab27-106">Le sequenze possono anche essere ricevute nel flusso di input in risposta a una sequenza di informazioni di query del flusso di output o come codifica dell'input utente quando viene impostata la modalità appropriata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="2ab27-107">Per configurare questo comportamento, è possibile usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="2ab27-108">Alla fine di questo documento è incluso un esempio della modalità consigliata per abilitare i comportamenti del terminale virtuale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="2ab27-109">Il comportamento delle sequenze seguenti si basa su VT100 e sulle tecnologie dell'emulatore di terminale derivate, in particolare sull'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="2ab27-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="2ab27-110">Per altre informazioni sulle sequenze di terminale, visitare i siti Web agli indirizzi <http://vt100.net> e <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span><span class="sxs-lookup"><span data-stu-id="2ab27-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="2ab27-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Sequenze di output</span><span class="sxs-lookup"><span data-stu-id="2ab27-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="2ab27-112">Le sequenze di terminale seguenti vengono intercettate dall'host della console quando vengono scritte nel flusso di output se il flag ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING viene impostato sull'handle del buffer dello schermo usando la funzione [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="2ab27-113">Si noti che il flag DISABLE\_NEWLINE\_AUTO\_RETURN può essere utile anche per emulare il posizionamento del cursore e il comportamento di scorrimento di altri emulatori di terminale in relazione ai caratteri scritti nella colonna finale di qualsiasi riga.</span><span class="sxs-lookup"><span data-stu-id="2ab27-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="2ab27-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posizionamento semplice del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="2ab27-115">In tutte le descrizioni seguenti ESC è sempre rappresentato dal valore esadecimale 0x1B.</span><span class="sxs-lookup"><span data-stu-id="2ab27-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="2ab27-116">Non è necessario includere spazi nelle sequenze di terminale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="2ab27-117">Per informazioni su come vengono usate in pratica le sequenze, vedere l'[esempio](#example) alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="2ab27-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="2ab27-118">Nella tabella seguente vengono descritte le sequenze di escape semplici con un solo comando di azione subito dopo il carattere ESC.</span><span class="sxs-lookup"><span data-stu-id="2ab27-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="2ab27-119">Queste sequenze non hanno parametri e hanno effetto immediato.</span><span class="sxs-lookup"><span data-stu-id="2ab27-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="2ab27-120">Tutti i comandi inclusi in questa tabella sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) per posizionare il cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="2ab27-121">Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="2ab27-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="2ab27-122">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="2ab27-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="2ab27-123">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-123">Sequence</span></span> | <span data-ttu-id="2ab27-124">Sintassi abbreviata</span><span class="sxs-lookup"><span data-stu-id="2ab27-124">Shorthand</span></span> | <span data-ttu-id="2ab27-125">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="2ab27-126">ESC A</span></span> | <span data-ttu-id="2ab27-127">CUU</span><span class="sxs-lookup"><span data-stu-id="2ab27-127">CUU</span></span> | <span data-ttu-id="2ab27-128">Cursore su di 1</span><span class="sxs-lookup"><span data-stu-id="2ab27-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="2ab27-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="2ab27-129">ESC B</span></span> | <span data-ttu-id="2ab27-130">CUD</span><span class="sxs-lookup"><span data-stu-id="2ab27-130">CUD</span></span> | <span data-ttu-id="2ab27-131">Cursore giù di 1</span><span class="sxs-lookup"><span data-stu-id="2ab27-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="2ab27-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="2ab27-132">ESC C</span></span> | <span data-ttu-id="2ab27-133">CUF</span><span class="sxs-lookup"><span data-stu-id="2ab27-133">CUF</span></span> | <span data-ttu-id="2ab27-134">Cursore avanti (verso destra) di 1</span><span class="sxs-lookup"><span data-stu-id="2ab27-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="2ab27-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="2ab27-135">ESC D</span></span> | <span data-ttu-id="2ab27-136">CUB</span><span class="sxs-lookup"><span data-stu-id="2ab27-136">CUB</span></span> | <span data-ttu-id="2ab27-137">Cursore indietro (verso sinistra) di 1</span><span class="sxs-lookup"><span data-stu-id="2ab27-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="2ab27-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="2ab27-138">ESC M</span></span> | <span data-ttu-id="2ab27-139">RI</span><span class="sxs-lookup"><span data-stu-id="2ab27-139">RI</span></span> | <span data-ttu-id="2ab27-140">Indice inverso: esegue l'operazione inversa di \\n, sposta il cursore verso l'alto di una riga, mantiene la posizione orizzontale, scorre il buffer se necessario\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="2ab27-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="2ab27-141">ESC 7</span></span> | <span data-ttu-id="2ab27-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="2ab27-142">DECSC</span></span> | <span data-ttu-id="2ab27-143">Salva la posizione del cursore in memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="2ab27-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="2ab27-144">ESC 8</span></span> | <span data-ttu-id="2ab27-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="2ab27-145">DECSR</span></span> | <span data-ttu-id="2ab27-146">Ripristina la posizione del cursore dalla memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="2ab27-147">\* Se sono impostati i margini di scorrimento, RI all'interno dei margini scorrerà solo il contenuto dei margini e lascerà invariato il riquadro di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="2ab27-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="2ab27-148">(vedere Margini di scorrimento).</span><span class="sxs-lookup"><span data-stu-id="2ab27-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="2ab27-149">\*\*Non sarà presente alcun valore salvato in memoria fino al primo utilizzo del comando di salvataggop.</span><span class="sxs-lookup"><span data-stu-id="2ab27-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="2ab27-150">L'unico modo per accedere al valore salvato è tramite il comando di ripristino.</span><span class="sxs-lookup"><span data-stu-id="2ab27-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="2ab27-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posizionamento del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="2ab27-152">Le tabelle seguenti includono le sequenze di tipo CSI (Control Sequence Introducer).</span><span class="sxs-lookup"><span data-stu-id="2ab27-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="2ab27-153">Tutte le sequenze CSI iniziano con ESC (0x1B) seguito da \[ (parentesi quadra aperta, 0x5B) e possono contenere parametri di lunghezza variabile per specificare altre informazioni per ogni operazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="2ab27-154">Tali informazioni saranno rappresentate dalla sintassi abbreviata &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="2ab27-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="2ab27-155">Ogni tabella riportata di seguito è raggruppata per funzionalità, con note sotto ogni tabella che illustrano il funzionamento del gruppo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="2ab27-156">Se non diversamente specificato, le regole seguenti si applicano a tutti i parametri:</span><span class="sxs-lookup"><span data-stu-id="2ab27-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="2ab27-157">&lt;n&gt; rappresenta la distanza di spostamento ed è un parametro facoltativo</span><span class="sxs-lookup"><span data-stu-id="2ab27-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="2ab27-158">Se &lt;n&gt; viene omesso o è uguale a 0, verrà considerato come 1</span><span class="sxs-lookup"><span data-stu-id="2ab27-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="2ab27-159">&lt;n&gt; non può essere maggiore di 32.767 (valore short massimo)</span><span class="sxs-lookup"><span data-stu-id="2ab27-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="2ab27-160">&lt;n&gt; non può essere un valore negativo</span><span class="sxs-lookup"><span data-stu-id="2ab27-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="2ab27-161">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="2ab27-162">Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="2ab27-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="2ab27-163">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="2ab27-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="2ab27-164">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-164">Sequence</span></span> | <span data-ttu-id="2ab27-165">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-165">Code</span></span> | <span data-ttu-id="2ab27-166">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-166">Description</span></span> | <span data-ttu-id="2ab27-167">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="2ab27-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="2ab27-169">CUU</span><span class="sxs-lookup"><span data-stu-id="2ab27-169">CUU</span></span> | <span data-ttu-id="2ab27-170">Cursore su</span><span class="sxs-lookup"><span data-stu-id="2ab27-170">Cursor Up</span></span> | <span data-ttu-id="2ab27-171">Cursore su di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="2ab27-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="2ab27-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="2ab27-173">CUD</span><span class="sxs-lookup"><span data-stu-id="2ab27-173">CUD</span></span> | <span data-ttu-id="2ab27-174">Cursore giù</span><span class="sxs-lookup"><span data-stu-id="2ab27-174">Cursor Down</span></span> | <span data-ttu-id="2ab27-175">Cursore giù di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="2ab27-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="2ab27-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="2ab27-177">CUF</span><span class="sxs-lookup"><span data-stu-id="2ab27-177">CUF</span></span> | <span data-ttu-id="2ab27-178">Cursore avanti</span><span class="sxs-lookup"><span data-stu-id="2ab27-178">Cursor Forward</span></span> | <span data-ttu-id="2ab27-179">Cursore avanti (verso destra) di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="2ab27-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="2ab27-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="2ab27-181">CUB</span><span class="sxs-lookup"><span data-stu-id="2ab27-181">CUB</span></span> | <span data-ttu-id="2ab27-182">Cursore indietro</span><span class="sxs-lookup"><span data-stu-id="2ab27-182">Cursor Backward</span></span> | <span data-ttu-id="2ab27-183">Cursore indietro (verso sinistra) di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="2ab27-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="2ab27-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="2ab27-185">CNL</span><span class="sxs-lookup"><span data-stu-id="2ab27-185">CNL</span></span> | <span data-ttu-id="2ab27-186">Cursore riga successiva</span><span class="sxs-lookup"><span data-stu-id="2ab27-186">Cursor Next Line</span></span> | <span data-ttu-id="2ab27-187">Cursore giù di &lt;n&gt; righe dalla posizione corrente</span><span class="sxs-lookup"><span data-stu-id="2ab27-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="2ab27-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="2ab27-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="2ab27-189">CPL</span><span class="sxs-lookup"><span data-stu-id="2ab27-189">CPL</span></span> | <span data-ttu-id="2ab27-190">Cursore riga precedente</span><span class="sxs-lookup"><span data-stu-id="2ab27-190">Cursor Previous Line</span></span> | <span data-ttu-id="2ab27-191">Cursore su &lt;n&gt; righe dalla posizione corrente</span><span class="sxs-lookup"><span data-stu-id="2ab27-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="2ab27-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="2ab27-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="2ab27-193">CHA</span><span class="sxs-lookup"><span data-stu-id="2ab27-193">CHA</span></span> | <span data-ttu-id="2ab27-194">Cursore assoluto orizzontale</span><span class="sxs-lookup"><span data-stu-id="2ab27-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="2ab27-195">Il cursore si sposta orizzontalmente alla posizione &lt;n&gt; nella riga corrente</span><span class="sxs-lookup"><span data-stu-id="2ab27-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="2ab27-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="2ab27-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="2ab27-197">VPA</span><span class="sxs-lookup"><span data-stu-id="2ab27-197">VPA</span></span> | <span data-ttu-id="2ab27-198">Assoluto posizione riga verticale</span><span class="sxs-lookup"><span data-stu-id="2ab27-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="2ab27-199">Il cursore si sposta verticalmente alla posizione &lt;n&gt; nella colonna corrente</span><span class="sxs-lookup"><span data-stu-id="2ab27-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="2ab27-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="2ab27-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="2ab27-201">CUP</span><span class="sxs-lookup"><span data-stu-id="2ab27-201">CUP</span></span> | <span data-ttu-id="2ab27-202">Posizione cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-202">Cursor Position</span></span> | <span data-ttu-id="2ab27-203">\*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="2ab27-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="2ab27-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="2ab27-205">HVP</span><span class="sxs-lookup"><span data-stu-id="2ab27-205">HVP</span></span> | <span data-ttu-id="2ab27-206">Posizione verticale orizzontale</span><span class="sxs-lookup"><span data-stu-id="2ab27-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="2ab27-207">\*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="2ab27-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="2ab27-208">ESC \[ s</span></span> | <span data-ttu-id="2ab27-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="2ab27-209">ANSISYSSC</span></span> | <span data-ttu-id="2ab27-210">Salvataggio cursore - Emulazione Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="2ab27-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="2ab27-211">\*\*Senza parametri, esegue un'operazione di salvataggio del cursore come DECSC</span><span class="sxs-lookup"><span data-stu-id="2ab27-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="2ab27-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="2ab27-212">ESC \[ u</span></span> | <span data-ttu-id="2ab27-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="2ab27-213">ANSISYSSC</span></span> | <span data-ttu-id="2ab27-214">Ripristino cursore - Emulazione Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="2ab27-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="2ab27-215">\*\*Senza parametri, esegue un'operazione di ripristino del cursore come DECRC</span><span class="sxs-lookup"><span data-stu-id="2ab27-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="2ab27-216">\*I parametri &lt;x&gt; e &lt;y&gt; hanno le stesse limitazioni del valore &lt;n&gt; sopraindicato.</span><span class="sxs-lookup"><span data-stu-id="2ab27-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="2ab27-217">Se &lt;x&gt; e &lt;y&gt; vengono omessi, verranno impostati su 1;1.</span><span class="sxs-lookup"><span data-stu-id="2ab27-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="2ab27-218">\*\*La documentazione cronologica relativa ad ANSI.sys è disponibile nel sito Web all'indirizzo <https://msdn.microsoft.com/library/cc722862.aspx> e viene implementata per praticità e/o compatibilità.</span><span class="sxs-lookup"><span data-stu-id="2ab27-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="2ab27-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilità del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="2ab27-220">I comandi seguenti controllano la visibilità del cursore e del relativo stato intermittente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="2ab27-221">Le sequenze DECTCEM sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) per attivare o disattivare la visibilità del cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="2ab27-222">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-222">Sequence</span></span> | <span data-ttu-id="2ab27-223">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-223">Code</span></span> | <span data-ttu-id="2ab27-224">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-224">Description</span></span> | <span data-ttu-id="2ab27-225">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="2ab27-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-226">ESC \[ ?</span></span> <span data-ttu-id="2ab27-227">12 h</span><span class="sxs-lookup"><span data-stu-id="2ab27-227">12 h</span></span> | <span data-ttu-id="2ab27-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="2ab27-228">ATT160</span></span> | <span data-ttu-id="2ab27-229">Abilitazione cursore di testo intermittente</span><span class="sxs-lookup"><span data-stu-id="2ab27-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="2ab27-230">Avvia lo stato intermittente del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="2ab27-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-231">ESC \[ ?</span></span> <span data-ttu-id="2ab27-232">12 l</span><span class="sxs-lookup"><span data-stu-id="2ab27-232">12 l</span></span> | <span data-ttu-id="2ab27-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="2ab27-233">ATT160</span></span> | <span data-ttu-id="2ab27-234">Disabilitazione cursore di testo intermittente</span><span class="sxs-lookup"><span data-stu-id="2ab27-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="2ab27-235">Interrompe lo stato intermittente del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="2ab27-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-236">ESC \[ ?</span></span> <span data-ttu-id="2ab27-237">25 h</span><span class="sxs-lookup"><span data-stu-id="2ab27-237">25 h</span></span> | <span data-ttu-id="2ab27-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="2ab27-238">DECTCEM</span></span> | <span data-ttu-id="2ab27-239">Abilitazione cursore di testo in modalità Mostra</span><span class="sxs-lookup"><span data-stu-id="2ab27-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="2ab27-240">Mostra il cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-240">Show the cursor</span></span> |
| <span data-ttu-id="2ab27-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-241">ESC \[ ?</span></span> <span data-ttu-id="2ab27-242">25 l</span><span class="sxs-lookup"><span data-stu-id="2ab27-242">25 l</span></span> | <span data-ttu-id="2ab27-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="2ab27-243">DECTCEM</span></span> | <span data-ttu-id="2ab27-244">Abilitazione cursore di testo in modalità Nascondi</span><span class="sxs-lookup"><span data-stu-id="2ab27-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="2ab27-245">Nasconde il cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="2ab27-246">Le sequenze di abilitazione terminano con un carattere H minuscolo (`h`), mentre le sequenze di disabilitazione terminano con un carattere L minuscolo (`l`).</span><span class="sxs-lookup"><span data-stu-id="2ab27-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="2ab27-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posizionamento del riquadro di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="2ab27-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="2ab27-248">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per spostare il contenuto del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="2ab27-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="2ab27-249">**Attenzione** I nomi dei comandi sono fuorvianti.</span><span class="sxs-lookup"><span data-stu-id="2ab27-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="2ab27-250">Il termine "scorrere" si riferisce alla direzione di spostamento del testo durante l'operazione, non alla modalità di spostamento del riquadro di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="2ab27-251">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-251">Sequence</span></span> | <span data-ttu-id="2ab27-252">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-252">Code</span></span> | <span data-ttu-id="2ab27-253">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-253">Description</span></span> | <span data-ttu-id="2ab27-254">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="2ab27-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="2ab27-256">Unità di streaming (SU)</span><span class="sxs-lookup"><span data-stu-id="2ab27-256">SU</span></span> | <span data-ttu-id="2ab27-257">Scorrimento verso l'alto</span><span class="sxs-lookup"><span data-stu-id="2ab27-257">Scroll Up</span></span> | <span data-ttu-id="2ab27-258">Scorrimento del testo verso l'alto di &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="2ab27-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="2ab27-259">Operazione nota anche come "panoramica in basso", dove le nuove righe vengono compilate a partire dalla parte inferiore dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="2ab27-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="2ab27-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="2ab27-261">DS</span><span class="sxs-lookup"><span data-stu-id="2ab27-261">SD</span></span> | <span data-ttu-id="2ab27-262">Scorrimento verso il basso</span><span class="sxs-lookup"><span data-stu-id="2ab27-262">Scroll Down</span></span> | <span data-ttu-id="2ab27-263">Scorrimento verso il basso di &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="2ab27-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="2ab27-264">Operazione nota anche come "panoramica in alto", dove le nuove righe vengono compilate a partire dalla parte superiore dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="2ab27-265">Il testo viene spostato a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="2ab27-266">Se il cursore si trova nella riga centrale del riquadro di visualizzazione, lo scorrimento verso l'alto determinerà lo spostamento della metà inferiore del riquadro e l'inserimento di righe vuote in fondo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="2ab27-267">Lo scorrimento verso il basso determinerà lo spostamento della metà superiore delle righe del riquadro di visualizzazione e l'inserimento di nuove righe in cima.</span><span class="sxs-lookup"><span data-stu-id="2ab27-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="2ab27-268">È inoltre importante notare che lo scorrimento verso l'alto e lo scorrimento verso il basso dipendono anche dai margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="2ab27-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="2ab27-269">Lo scorrimento verso l'alto e lo scorrimento verso il basso non influiranno sulle righe esterne ai margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="2ab27-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="2ab27-270">Il valore predefinito per &lt;n&gt; è 1 che facoltativamente può essere omesso.</span><span class="sxs-lookup"><span data-stu-id="2ab27-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="2ab27-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modifica del testo</span><span class="sxs-lookup"><span data-stu-id="2ab27-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="2ab27-272">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) e [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per modificare il contenuto del buffer di testo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="2ab27-273">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-273">Sequence</span></span> | <span data-ttu-id="2ab27-274">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-274">Code</span></span> | <span data-ttu-id="2ab27-275">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-275">Description</span></span> | <span data-ttu-id="2ab27-276">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="2ab27-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="2ab27-278">ICH</span><span class="sxs-lookup"><span data-stu-id="2ab27-278">ICH</span></span> | <span data-ttu-id="2ab27-279">Inserimento carattere</span><span class="sxs-lookup"><span data-stu-id="2ab27-279">Insert Character</span></span> | <span data-ttu-id="2ab27-280">Inserisce &lt;n&gt; spazi nella posizione corrente del cursore, spostando tutto il testo esistente verso destra.</span><span class="sxs-lookup"><span data-stu-id="2ab27-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="2ab27-281">All'uscita dallo schermo, il testo a destra viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="2ab27-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="2ab27-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="2ab27-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="2ab27-283">DCH</span><span class="sxs-lookup"><span data-stu-id="2ab27-283">DCH</span></span> | <span data-ttu-id="2ab27-284">Eliminazione carattere</span><span class="sxs-lookup"><span data-stu-id="2ab27-284">Delete Character</span></span> | <span data-ttu-id="2ab27-285">Elimina &lt;n&gt; caratteri nella posizione corrente del cursore, scalando gli spazi dal bordo destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="2ab27-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="2ab27-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="2ab27-287">ECH</span><span class="sxs-lookup"><span data-stu-id="2ab27-287">ECH</span></span> | <span data-ttu-id="2ab27-288">Cancellazione carattere</span><span class="sxs-lookup"><span data-stu-id="2ab27-288">Erase Character</span></span> | <span data-ttu-id="2ab27-289">Cancella &lt;n&gt; caratteri dalla posizione corrente del cursore sovrascrivendoli con uno spazio.</span><span class="sxs-lookup"><span data-stu-id="2ab27-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="2ab27-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="2ab27-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="2ab27-291">IL</span><span class="sxs-lookup"><span data-stu-id="2ab27-291">IL</span></span> | <span data-ttu-id="2ab27-292">Inserisci riga</span><span class="sxs-lookup"><span data-stu-id="2ab27-292">Insert Line</span></span> | <span data-ttu-id="2ab27-293">Inserisce &lt;n&gt; righe nel buffer in corrispondenza della posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="2ab27-294">La riga in cui si trova il cursore e le righe sottostanti verranno spostate verso il basso.</span><span class="sxs-lookup"><span data-stu-id="2ab27-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="2ab27-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="2ab27-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="2ab27-296">DL</span><span class="sxs-lookup"><span data-stu-id="2ab27-296">DL</span></span> | <span data-ttu-id="2ab27-297">Elimina riga</span><span class="sxs-lookup"><span data-stu-id="2ab27-297">Delete Line</span></span> | <span data-ttu-id="2ab27-298">Elimina &lt;n&gt; righe dal buffer, a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="2ab27-299">Per IL e DL sono interessate solo le righe incluse nei margini di scorrimento (vedere Margini di scorrimento).</span><span class="sxs-lookup"><span data-stu-id="2ab27-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="2ab27-300">Se non è impostato alcun margine, i bordi predefiniti corrispondono al riquadro di visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="2ab27-301">Se le righe vengono spostate sotto i margini, vengono rimosse.</span><span class="sxs-lookup"><span data-stu-id="2ab27-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="2ab27-302">Quando le righe vengono eliminate, vengono inserite righe vuote in fondo ai margini. Le linee esterne al riquadro di visualizzazione non sono mai interessate.</span><span class="sxs-lookup"><span data-stu-id="2ab27-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="2ab27-303">Per ognuna delle sequenze, il valore predefinito di &lt;n&gt;, se omesso, è 0.</span><span class="sxs-lookup"><span data-stu-id="2ab27-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="2ab27-304">Per i comandi seguenti il parametro &lt;n&gt; ha 3 valori validi:</span><span class="sxs-lookup"><span data-stu-id="2ab27-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="2ab27-305">0 cancella il contenuto dalla posizione corrente del cursore (inclusa) alla fine della riga o del display</span><span class="sxs-lookup"><span data-stu-id="2ab27-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="2ab27-306">1 cancella il contenuto dall'inizio della riga o del display fino alla posizione corrente del cursore inclusa</span><span class="sxs-lookup"><span data-stu-id="2ab27-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="2ab27-307">2 cancella il contenuto di tutta la riga o di tutto il display</span><span class="sxs-lookup"><span data-stu-id="2ab27-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="2ab27-308">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-308">Sequence</span></span> | <span data-ttu-id="2ab27-309">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-309">Code</span></span> | <span data-ttu-id="2ab27-310">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-310">Description</span></span> | <span data-ttu-id="2ab27-311">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="2ab27-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="2ab27-313">ED</span><span class="sxs-lookup"><span data-stu-id="2ab27-313">ED</span></span> | <span data-ttu-id="2ab27-314">Cancellazione nel display</span><span class="sxs-lookup"><span data-stu-id="2ab27-314">Erase in Display</span></span> | <span data-ttu-id="2ab27-315">Sostituisce tutto il testo presente nel riquadro di visualizzazione o nello schermo, specificato da &lt;n&gt; con spazi</span><span class="sxs-lookup"><span data-stu-id="2ab27-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="2ab27-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="2ab27-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="2ab27-317">EL</span><span class="sxs-lookup"><span data-stu-id="2ab27-317">EL</span></span> | <span data-ttu-id="2ab27-318">Cancellazione nella riga</span><span class="sxs-lookup"><span data-stu-id="2ab27-318">Erase in Line</span></span> | <span data-ttu-id="2ab27-319">Sostituisce tutto il testo presente nella riga con il cursore specificato da &lt;n&gt; con spazi</span><span class="sxs-lookup"><span data-stu-id="2ab27-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="2ab27-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formattazione del testo</span><span class="sxs-lookup"><span data-stu-id="2ab27-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="2ab27-321">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**SetConsoleTextAttribute**](setconsoletextattribute.md) per regolare la formattazione di tutte le operazioni di scrittura future nel buffer di testo di output della console.</span><span class="sxs-lookup"><span data-stu-id="2ab27-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="2ab27-322">Questo comando è speciale in quanto la posizione &lt;n&gt; indicata di seguito può accettare da 0 a 16 parametri separati da punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="2ab27-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="2ab27-323">Se non è specificato alcun parametro, si considera come se fosse specificato un singolo parametro 0.</span><span class="sxs-lookup"><span data-stu-id="2ab27-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="2ab27-324">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-324">Sequence</span></span> | <span data-ttu-id="2ab27-325">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-325">Code</span></span> | <span data-ttu-id="2ab27-326">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-326">Description</span></span> | <span data-ttu-id="2ab27-327">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="2ab27-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="2ab27-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="2ab27-329">SGR</span><span class="sxs-lookup"><span data-stu-id="2ab27-329">SGR</span></span> | <span data-ttu-id="2ab27-330">Impostazione rendering grafica</span><span class="sxs-lookup"><span data-stu-id="2ab27-330">Set Graphics Rendition</span></span> | <span data-ttu-id="2ab27-331">Imposta il formato dello schermo e del testo come specificato da &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="2ab27-332">La seguente tabella di valori può essere usata in &lt;n&gt; per rappresentare modalità di formattazione diverse.</span><span class="sxs-lookup"><span data-stu-id="2ab27-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="2ab27-333">Le modalità di formattazione vengono applicate da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="2ab27-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="2ab27-334">Se si applicano opzioni di formattazione concorrenti, l'opzione più a destra avrà la precedenza.</span><span class="sxs-lookup"><span data-stu-id="2ab27-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="2ab27-335">Per le opzioni che specificano i colori, i colori verranno usati come definito nella tabella dei colori della console, che può essere modificata usando l'API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="2ab27-336">Se la tabella viene modificata in modo che la posizione "blu" visualizzi una sfumatura di rosso RGB, tutte le chiamate a **Blu primo piano** visualizzeranno il colore rosso fino a quando questa opzione non viene modificata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="2ab27-337">Valore</span><span class="sxs-lookup"><span data-stu-id="2ab27-337">Value</span></span> | <span data-ttu-id="2ab27-338">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-338">Description</span></span> | <span data-ttu-id="2ab27-339">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="2ab27-340">0</span><span class="sxs-lookup"><span data-stu-id="2ab27-340">0</span></span> | <span data-ttu-id="2ab27-341">Predefinito</span><span class="sxs-lookup"><span data-stu-id="2ab27-341">Default</span></span> | <span data-ttu-id="2ab27-342">Ripristina lo stato predefinito di tutti gli attributi precedente alla modifica</span><span class="sxs-lookup"><span data-stu-id="2ab27-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="2ab27-343">1</span><span class="sxs-lookup"><span data-stu-id="2ab27-343">1</span></span> | <span data-ttu-id="2ab27-344">Grassetto/Brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-344">Bold/Bright</span></span> | <span data-ttu-id="2ab27-345">Applica il flag di luminosità/intensità al colore di primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="2ab27-346">22</span><span class="sxs-lookup"><span data-stu-id="2ab27-346">22</span></span> | <span data-ttu-id="2ab27-347">Nessun grassetto/chiaro</span><span class="sxs-lookup"><span data-stu-id="2ab27-347">No bold/bright</span></span> | <span data-ttu-id="2ab27-348">Rimuove il flag di luminosità/intensità dal colore primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-348">Removes brightness/intensity flag from foreground color</span></span> |
| <span data-ttu-id="2ab27-349">4</span><span class="sxs-lookup"><span data-stu-id="2ab27-349">4</span></span> | <span data-ttu-id="2ab27-350">Sottolineato</span><span class="sxs-lookup"><span data-stu-id="2ab27-350">Underline</span></span> | <span data-ttu-id="2ab27-351">Aggiunge la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="2ab27-351">Adds underline</span></span> |
| <span data-ttu-id="2ab27-352">24</span><span class="sxs-lookup"><span data-stu-id="2ab27-352">24</span></span> | <span data-ttu-id="2ab27-353">Nessuna sottolineatura</span><span class="sxs-lookup"><span data-stu-id="2ab27-353">No underline</span></span> | <span data-ttu-id="2ab27-354">Rimuove la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="2ab27-354">Removes underline</span></span> |
| <span data-ttu-id="2ab27-355">7</span><span class="sxs-lookup"><span data-stu-id="2ab27-355">7</span></span> | <span data-ttu-id="2ab27-356">Negativo</span><span class="sxs-lookup"><span data-stu-id="2ab27-356">Negative</span></span> | <span data-ttu-id="2ab27-357">Scambia i colori di primo piano e di sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-357">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="2ab27-358">27</span><span class="sxs-lookup"><span data-stu-id="2ab27-358">27</span></span> | <span data-ttu-id="2ab27-359">Positivo (non negativo)</span><span class="sxs-lookup"><span data-stu-id="2ab27-359">Positive (No negative)</span></span> | <span data-ttu-id="2ab27-360">Ripristina il valore normale di primo piano/sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-360">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="2ab27-361">30</span><span class="sxs-lookup"><span data-stu-id="2ab27-361">30</span></span> | <span data-ttu-id="2ab27-362">Nero primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-362">Foreground Black</span></span> | <span data-ttu-id="2ab27-363">Applica il colore nero non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-363">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="2ab27-364">31</span><span class="sxs-lookup"><span data-stu-id="2ab27-364">31</span></span> | <span data-ttu-id="2ab27-365">Rosso primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-365">Foreground Red</span></span> | <span data-ttu-id="2ab27-366">Applica il colore rosso non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-366">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="2ab27-367">32</span><span class="sxs-lookup"><span data-stu-id="2ab27-367">32</span></span> | <span data-ttu-id="2ab27-368">Verde primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-368">Foreground Green</span></span> | <span data-ttu-id="2ab27-369">Applica il colore verde non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-369">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="2ab27-370">33</span><span class="sxs-lookup"><span data-stu-id="2ab27-370">33</span></span> | <span data-ttu-id="2ab27-371">Giallo primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-371">Foreground Yellow</span></span> | <span data-ttu-id="2ab27-372">Applica il colore giallo non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-372">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="2ab27-373">34</span><span class="sxs-lookup"><span data-stu-id="2ab27-373">34</span></span> | <span data-ttu-id="2ab27-374">Blu primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-374">Foreground Blue</span></span> | <span data-ttu-id="2ab27-375">Applica il colore blu non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-375">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="2ab27-376">35</span><span class="sxs-lookup"><span data-stu-id="2ab27-376">35</span></span> | <span data-ttu-id="2ab27-377">Magenta primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-377">Foreground Magenta</span></span> | <span data-ttu-id="2ab27-378">Applica il color magenta non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-378">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="2ab27-379">36</span><span class="sxs-lookup"><span data-stu-id="2ab27-379">36</span></span> | <span data-ttu-id="2ab27-380">Ciano primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-380">Foreground Cyan</span></span> | <span data-ttu-id="2ab27-381">Applica il color ciano non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-381">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="2ab27-382">37</span><span class="sxs-lookup"><span data-stu-id="2ab27-382">37</span></span> | <span data-ttu-id="2ab27-383">Bianco primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-383">Foreground White</span></span> | <span data-ttu-id="2ab27-384">Applica il colore bianco non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-384">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="2ab27-385">38</span><span class="sxs-lookup"><span data-stu-id="2ab27-385">38</span></span> | <span data-ttu-id="2ab27-386">Valore esteso primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-386">Foreground Extended</span></span> | <span data-ttu-id="2ab27-387">Applica il valore di colore esteso al primo piano (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="2ab27-387">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="2ab27-388">39</span><span class="sxs-lookup"><span data-stu-id="2ab27-388">39</span></span> | <span data-ttu-id="2ab27-389">Valore predefinito primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-389">Foreground Default</span></span> | <span data-ttu-id="2ab27-390">Applica solo la parte in primo piano delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="2ab27-390">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="2ab27-391">40</span><span class="sxs-lookup"><span data-stu-id="2ab27-391">40</span></span> | <span data-ttu-id="2ab27-392">Nero sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-392">Background Black</span></span> | <span data-ttu-id="2ab27-393">Applica il colore nero non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-393">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="2ab27-394">41</span><span class="sxs-lookup"><span data-stu-id="2ab27-394">41</span></span> | <span data-ttu-id="2ab27-395">Rosso sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-395">Background Red</span></span> | <span data-ttu-id="2ab27-396">Applica il colore rosso non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-396">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="2ab27-397">42</span><span class="sxs-lookup"><span data-stu-id="2ab27-397">42</span></span> | <span data-ttu-id="2ab27-398">Verde sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-398">Background Green</span></span> | <span data-ttu-id="2ab27-399">Applica il colore verde non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-399">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="2ab27-400">43</span><span class="sxs-lookup"><span data-stu-id="2ab27-400">43</span></span> | <span data-ttu-id="2ab27-401">Giallo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-401">Background Yellow</span></span> | <span data-ttu-id="2ab27-402">Applica il colore giallo non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-402">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="2ab27-403">44</span><span class="sxs-lookup"><span data-stu-id="2ab27-403">44</span></span> | <span data-ttu-id="2ab27-404">Blu sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-404">Background Blue</span></span> | <span data-ttu-id="2ab27-405">Applica il colore blu non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-405">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="2ab27-406">45</span><span class="sxs-lookup"><span data-stu-id="2ab27-406">45</span></span> | <span data-ttu-id="2ab27-407">Magenta sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-407">Background Magenta</span></span> | <span data-ttu-id="2ab27-408">Applica il color magenta non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-408">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="2ab27-409">46</span><span class="sxs-lookup"><span data-stu-id="2ab27-409">46</span></span> | <span data-ttu-id="2ab27-410">Ciano sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-410">Background Cyan</span></span> | <span data-ttu-id="2ab27-411">Applica il color ciano non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-411">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="2ab27-412">47</span><span class="sxs-lookup"><span data-stu-id="2ab27-412">47</span></span> | <span data-ttu-id="2ab27-413">Bianco sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-413">Background White</span></span> | <span data-ttu-id="2ab27-414">Applica il colore bianco non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-414">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="2ab27-415">48</span><span class="sxs-lookup"><span data-stu-id="2ab27-415">48</span></span> | <span data-ttu-id="2ab27-416">Valore esteso sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-416">Background Extended</span></span> | <span data-ttu-id="2ab27-417">Applica il valore di colore esteso allo sfondo (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="2ab27-417">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="2ab27-418">49</span><span class="sxs-lookup"><span data-stu-id="2ab27-418">49</span></span> | <span data-ttu-id="2ab27-419">Valore predefinito sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-419">Background Default</span></span> | <span data-ttu-id="2ab27-420">Applica solo la parte dello sfondo delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="2ab27-420">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="2ab27-421">90</span><span class="sxs-lookup"><span data-stu-id="2ab27-421">90</span></span> | <span data-ttu-id="2ab27-422">Nero primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-422">Bright Foreground Black</span></span> | <span data-ttu-id="2ab27-423">Applica il colore nero grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-423">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="2ab27-424">91</span><span class="sxs-lookup"><span data-stu-id="2ab27-424">91</span></span> | <span data-ttu-id="2ab27-425">Rosso primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-425">Bright Foreground Red</span></span> | <span data-ttu-id="2ab27-426">Applica il colore rosso grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-426">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="2ab27-427">92</span><span class="sxs-lookup"><span data-stu-id="2ab27-427">92</span></span> | <span data-ttu-id="2ab27-428">Verde primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-428">Bright Foreground Green</span></span> | <span data-ttu-id="2ab27-429">Applica il colore verde grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-429">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="2ab27-430">93</span><span class="sxs-lookup"><span data-stu-id="2ab27-430">93</span></span> | <span data-ttu-id="2ab27-431">Giallo primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-431">Bright Foreground Yellow</span></span> | <span data-ttu-id="2ab27-432">Applica il colore giallo grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-432">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="2ab27-433">94</span><span class="sxs-lookup"><span data-stu-id="2ab27-433">94</span></span> | <span data-ttu-id="2ab27-434">Blu primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-434">Bright Foreground Blue</span></span> | <span data-ttu-id="2ab27-435">Applica il colore blu grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-435">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="2ab27-436">95</span><span class="sxs-lookup"><span data-stu-id="2ab27-436">95</span></span> | <span data-ttu-id="2ab27-437">Magenta primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-437">Bright Foreground Magenta</span></span> | <span data-ttu-id="2ab27-438">Applica il color magenta grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-438">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="2ab27-439">96</span><span class="sxs-lookup"><span data-stu-id="2ab27-439">96</span></span> | <span data-ttu-id="2ab27-440">Ciano primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-440">Bright Foreground Cyan</span></span> | <span data-ttu-id="2ab27-441">Applica il color ciano grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="2ab27-441">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="2ab27-442">97</span><span class="sxs-lookup"><span data-stu-id="2ab27-442">97</span></span> | <span data-ttu-id="2ab27-443">Bianco primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-443">Bright Foreground White</span></span> | <span data-ttu-id="2ab27-444">Applica il colore bianco grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-444">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="2ab27-445">100</span><span class="sxs-lookup"><span data-stu-id="2ab27-445">100</span></span> | <span data-ttu-id="2ab27-446">Nero sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-446">Bright Background Black</span></span> | <span data-ttu-id="2ab27-447">Applica il colore nero grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-447">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="2ab27-448">101</span><span class="sxs-lookup"><span data-stu-id="2ab27-448">101</span></span> | <span data-ttu-id="2ab27-449">Rosso sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-449">Bright Background Red</span></span> | <span data-ttu-id="2ab27-450">Applica il colore rosso grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-450">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="2ab27-451">102</span><span class="sxs-lookup"><span data-stu-id="2ab27-451">102</span></span> | <span data-ttu-id="2ab27-452">Verde sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-452">Bright Background Green</span></span> | <span data-ttu-id="2ab27-453">Applica il colore verde grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-453">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="2ab27-454">103</span><span class="sxs-lookup"><span data-stu-id="2ab27-454">103</span></span> | <span data-ttu-id="2ab27-455">Giallo sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-455">Bright Background Yellow</span></span> | <span data-ttu-id="2ab27-456">Applica il colore giallo grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-456">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="2ab27-457">104</span><span class="sxs-lookup"><span data-stu-id="2ab27-457">104</span></span> | <span data-ttu-id="2ab27-458">Blu sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-458">Bright Background Blue</span></span> | <span data-ttu-id="2ab27-459">Applica il colore blu grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-459">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="2ab27-460">105</span><span class="sxs-lookup"><span data-stu-id="2ab27-460">105</span></span> | <span data-ttu-id="2ab27-461">Magenta sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-461">Bright Background Magenta</span></span> | <span data-ttu-id="2ab27-462">Applica il color magenta grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-462">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="2ab27-463">106</span><span class="sxs-lookup"><span data-stu-id="2ab27-463">106</span></span> | <span data-ttu-id="2ab27-464">Ciano sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-464">Bright Background Cyan</span></span> | <span data-ttu-id="2ab27-465">Applica il color ciano grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-465">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="2ab27-466">107</span><span class="sxs-lookup"><span data-stu-id="2ab27-466">107</span></span> | <span data-ttu-id="2ab27-467">Bianco sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="2ab27-467">Bright Background White</span></span> | <span data-ttu-id="2ab27-468">Applica il colore bianco grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="2ab27-468">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="2ab27-469"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colori estesi</span><span class="sxs-lookup"><span data-stu-id="2ab27-469"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="2ab27-470">Alcuni emulatori di terminale virtuale supportano una tavolozza di colori più estesa dei 16 colori forniti dalla console di Windows.</span><span class="sxs-lookup"><span data-stu-id="2ab27-470">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="2ab27-471">Per questi colori estesi, la console di Windows sceglierà il colore appropriato più vicino dalla tavola dei 16 colori esistente per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-471">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="2ab27-472">Diversamente dai valori SGR tipici sopraindicati, i valori estesi utilizzano parametri aggiuntivi dopo l'indicatore iniziale, in base alle informazioni riportate nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-472">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="2ab27-473">Sottosequenza SGR</span><span class="sxs-lookup"><span data-stu-id="2ab27-473">SGR Subsequence</span></span> | <span data-ttu-id="2ab27-474">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-474">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-475">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-475">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="2ab27-476">Imposta il colore di primo piano sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-476">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="2ab27-477">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-477">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="2ab27-478">Imposta il colore di sfondo sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-478">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="2ab27-479">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-479">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="2ab27-480">Imposta il colore di primo piano sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-480">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="2ab27-481">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-481">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="2ab27-482">Imposta il colore di sfondo sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\*</span><span class="sxs-lookup"><span data-stu-id="2ab27-482">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="2ab27-483">\*Le tavolozze da 88 e 256 colori gestite internamente per il confronto sono basate sull'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="2ab27-483">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="2ab27-484">Non è possibile modificare le tabelle di confronto o di arrotondamento in questa fase.</span><span class="sxs-lookup"><span data-stu-id="2ab27-484">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="2ab27-485"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colori dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-485"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="2ab27-486">Il comando seguente consente all'applicazione di impostare i valori della tavolozza dei colori dello schermo su qualsiasi valore RGB.</span><span class="sxs-lookup"><span data-stu-id="2ab27-486">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="2ab27-487">I valori RGB devono essere valori esadecimali compresi tra `0` e `ff` e separati dal carattere barra (ad esempio, `rgb:1/24/86`).</span><span class="sxs-lookup"><span data-stu-id="2ab27-487">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="2ab27-488">Si noti che questa sequenza è di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza inizia con "\\x1b\]", non con "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="2ab27-488">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="2ab27-489">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-489">Sequence</span></span> | <span data-ttu-id="2ab27-490">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-490">Description</span></span> | <span data-ttu-id="2ab27-491">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-491">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-492">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="2ab27-492">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="2ab27-493">Modifica colori schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-493">Modify Screen Colors</span></span> | <span data-ttu-id="2ab27-494">Imposta l'indice &lt;i&gt; della tavolozza dei colori dello schermo sui valori RGB specificati in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-494">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="2ab27-495"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifiche della modalità</span><span class="sxs-lookup"><span data-stu-id="2ab27-495"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="2ab27-496">Si tratta di sequenze che controllano le modalità di input.</span><span class="sxs-lookup"><span data-stu-id="2ab27-496">These are sequences that control the input modes.</span></span> <span data-ttu-id="2ab27-497">Esistono due diversi set di modalità di input, ovvero la modalità tasti cursore e la modalità tasti del tastierino.</span><span class="sxs-lookup"><span data-stu-id="2ab27-497">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="2ab27-498">La modalità tasti cursore controlla le sequenze generate dai tasti di direzione, nonché da Home e Fine, mentre la modalità tasti del tastierino controlla le sequenze generate principalmente dai tasti sul tastierino numerico, nonché dai tasti funzione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-498">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="2ab27-499">Ognuna di queste modalità è una semplice impostazione booleana. La modalità tasti cursore è impostata su normale (impostazione predefinita) o applicazione e la modalità tasti del tastierino è impostata su numerica (impostazione predefinita) o applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-499">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="2ab27-500">Per le sequenze generate in queste modalità, vedere le sezioni Tasti cursore e Tastierino numerico.</span><span class="sxs-lookup"><span data-stu-id="2ab27-500">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="2ab27-501">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-501">Sequence</span></span> | <span data-ttu-id="2ab27-502">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-502">Code</span></span> | <span data-ttu-id="2ab27-503">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-503">Description</span></span> | <span data-ttu-id="2ab27-504">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-504">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="2ab27-505">ESC =</span><span class="sxs-lookup"><span data-stu-id="2ab27-505">ESC =</span></span> | <span data-ttu-id="2ab27-506">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="2ab27-506">DECKPAM</span></span> | <span data-ttu-id="2ab27-507">Abilitazione modalità applicazione tastierino</span><span class="sxs-lookup"><span data-stu-id="2ab27-507">Enable Keypad Application Mode</span></span> | <span data-ttu-id="2ab27-508">I tasti del tastierino generano le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-508">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="2ab27-509">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="2ab27-509">ESC &gt;</span></span> | <span data-ttu-id="2ab27-510">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="2ab27-510">DECKPNM</span></span> | <span data-ttu-id="2ab27-511">Abilitazione modalità numerica tastierino</span><span class="sxs-lookup"><span data-stu-id="2ab27-511">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="2ab27-512">I tasti del tastierino genereranno le relative sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="2ab27-512">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="2ab27-513">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-513">ESC \[ ?</span></span> <span data-ttu-id="2ab27-514">1 ora</span><span class="sxs-lookup"><span data-stu-id="2ab27-514">1 h</span></span> | <span data-ttu-id="2ab27-515">DECCKM</span><span class="sxs-lookup"><span data-stu-id="2ab27-515">DECCKM</span></span> | <span data-ttu-id="2ab27-516">Abilitazione modalità applicazione tasti cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-516">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="2ab27-517">I tasti del tastierino generano le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-517">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="2ab27-518">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-518">ESC \[ ?</span></span> <span data-ttu-id="2ab27-519">1 l</span><span class="sxs-lookup"><span data-stu-id="2ab27-519">1 l</span></span> | <span data-ttu-id="2ab27-520">DECCKM</span><span class="sxs-lookup"><span data-stu-id="2ab27-520">DECCKM</span></span> | <span data-ttu-id="2ab27-521">Disabilitazione modalità applicazione tasti cursore (usare la modalità normale)</span><span class="sxs-lookup"><span data-stu-id="2ab27-521">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="2ab27-522">I tasti del tastierino genereranno le relative sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="2ab27-522">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="2ab27-523"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Stato delle query</span><span class="sxs-lookup"><span data-stu-id="2ab27-523"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="2ab27-524">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console Get\* per recuperare informazioni sullo stato corrente del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="2ab27-524">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="2ab27-525">Queste query generano le risposte nel flusso di input della console subito dopo essere state riconosciute nel flusso di output durante l'impostazione di ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING.</span><span class="sxs-lookup"><span data-stu-id="2ab27-525">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="2ab27-526">Il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT non si applica ai comandi di query perché si presuppone che un'applicazione che esegue la query voglia sempre ricevere la risposta.</span><span class="sxs-lookup"><span data-stu-id="2ab27-526">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="2ab27-527">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-527">Sequence</span></span> | <span data-ttu-id="2ab27-528">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-528">Code</span></span> | <span data-ttu-id="2ab27-529">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-529">Description</span></span> | <span data-ttu-id="2ab27-530">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-530">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-531">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="2ab27-531">ESC \[ 6 n</span></span> | <span data-ttu-id="2ab27-532">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="2ab27-532">DECXCPR</span></span> | <span data-ttu-id="2ab27-533">Segnalazione posizione cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-533">Report Cursor Position</span></span> | <span data-ttu-id="2ab27-534">Genera la posizione del cursore come: ESC \[ &lt;r&gt; ; &lt;c&gt; R dove &lt;r&gt; = riga del cursore e &lt;c&gt; = colonna del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-534">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="2ab27-535">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="2ab27-535">ESC \[ 0 c</span></span> | <span data-ttu-id="2ab27-536">DA</span><span class="sxs-lookup"><span data-stu-id="2ab27-536">DA</span></span> | <span data-ttu-id="2ab27-537">Attributi dispositivo</span><span class="sxs-lookup"><span data-stu-id="2ab27-537">Device Attributes</span></span> | <span data-ttu-id="2ab27-538">Segnala l'identità del terminale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-538">Report the terminal identity.</span></span> <span data-ttu-id="2ab27-539">Genera "\\x1b\[?1;0c", per indicare "VT101 senza opzioni".</span><span class="sxs-lookup"><span data-stu-id="2ab27-539">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="2ab27-540"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabulazioni</span><span class="sxs-lookup"><span data-stu-id="2ab27-540"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="2ab27-541">Benché la console di Windows preveda tradizionalmente che la larghezza delle tabulazioni sia di otto caratteri, le applicazioni \*nix che utilizzano determinate sequenze possono modificare il punto in cui si trovano le tabulazioni nelle finestre della console per ottimizzare lo spostamento del cursore in base all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-541">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="2ab27-542">Le sequenze seguenti consentono a un'applicazione di impostare le posizioni delle tabulazioni nella finestra della console, rimuoverle e spostarsi da una posizione all'altra.</span><span class="sxs-lookup"><span data-stu-id="2ab27-542">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="2ab27-543">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-543">Sequence</span></span> | <span data-ttu-id="2ab27-544">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-544">Code</span></span> | <span data-ttu-id="2ab27-545">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-545">Description</span></span> | <span data-ttu-id="2ab27-546">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-546">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab27-547">ESC H</span><span class="sxs-lookup"><span data-stu-id="2ab27-547">ESC H</span></span> | <span data-ttu-id="2ab27-548">HTS</span><span class="sxs-lookup"><span data-stu-id="2ab27-548">HTS</span></span> | <span data-ttu-id="2ab27-549">Tabulazione orizzontale impostata</span><span class="sxs-lookup"><span data-stu-id="2ab27-549">Horizontal Tab Set</span></span> | <span data-ttu-id="2ab27-550">Imposta una tabulazione nella colonna corrente in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-550">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="2ab27-551">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="2ab27-551">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="2ab27-552">CHT</span><span class="sxs-lookup"><span data-stu-id="2ab27-552">CHT</span></span> | <span data-ttu-id="2ab27-553">Tabulazione orizzontale (in avanti) del cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-553">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="2ab27-554">Sposta il cursore nella colonna successiva (stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-554">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="2ab27-555">Se non sono presenti altre tabulazioni, il cursore si sposta nell'ultima colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="2ab27-555">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="2ab27-556">Se il cursore si trova nell'ultima colonna, passa alla prima colonna della riga successiva.</span><span class="sxs-lookup"><span data-stu-id="2ab27-556">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="2ab27-557">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="2ab27-557">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="2ab27-558">CBT</span><span class="sxs-lookup"><span data-stu-id="2ab27-558">CBT</span></span> | <span data-ttu-id="2ab27-559">Tabulazione cursore indietro</span><span class="sxs-lookup"><span data-stu-id="2ab27-559">Cursor Backwards Tab</span></span> | <span data-ttu-id="2ab27-560">Sposta il cursore nella colonna precedente (stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-560">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="2ab27-561">Se non sono presenti altre tabulazioni, sposta il cursore nella prima colonna.</span><span class="sxs-lookup"><span data-stu-id="2ab27-561">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="2ab27-562">Se il cursore si trova nella prima colonna, non viene spostato.</span><span class="sxs-lookup"><span data-stu-id="2ab27-562">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="2ab27-563">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="2ab27-563">ESC \[ 0 g</span></span> | <span data-ttu-id="2ab27-564">TBC</span><span class="sxs-lookup"><span data-stu-id="2ab27-564">TBC</span></span> | <span data-ttu-id="2ab27-565">Cancellazione tabulazione (colonna corrente)</span><span class="sxs-lookup"><span data-stu-id="2ab27-565">Tab Clear (current column)</span></span> | <span data-ttu-id="2ab27-566">Cancella la tabulazione, se presente, nella colonna corrente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-566">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="2ab27-567">In caso contrario, non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-567">Otherwise does nothing.</span></span> |
| <span data-ttu-id="2ab27-568">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="2ab27-568">ESC \[ 3 g</span></span> | <span data-ttu-id="2ab27-569">TBC</span><span class="sxs-lookup"><span data-stu-id="2ab27-569">TBC</span></span> | <span data-ttu-id="2ab27-570">Cancellazione tabulazione (tutte le colonne)</span><span class="sxs-lookup"><span data-stu-id="2ab27-570">Tab Clear (all columns)</span></span> | <span data-ttu-id="2ab27-571">Cancella tutte le tabulazioni attualmente impostate.</span><span class="sxs-lookup"><span data-stu-id="2ab27-571">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="2ab27-572">Per CHT e CBT, &lt;n&gt; è un parametro facoltativo (valore predefinito = 1) che indica il numero di volte in cui spostare il cursore nella direzione specificata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-572">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="2ab27-573">Se non sono presenti tabulazioni impostate tramite HTS, CHT e CBT, la prima e l'ultima colonna della finestra verranno considerate come le uniche due tabulazioni.</span><span class="sxs-lookup"><span data-stu-id="2ab27-573">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="2ab27-574">Se si usa HTS per impostare una tabulazione, la console passerà alla successiva tabulazione nell'output di un carattere di tabulazione (0x09,'\\t'), come avviene quando si usa CHT.</span><span class="sxs-lookup"><span data-stu-id="2ab27-574">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="2ab27-575"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designare il set di caratteri</span><span class="sxs-lookup"><span data-stu-id="2ab27-575"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="2ab27-576">Le sequenze seguenti consentono a un programma di modificare il mapping del set di caratteri attivo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-576">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="2ab27-577">In questo modo un programma può generare caratteri ASCII a 7 bit, ma visualizzarli come altri glifi nello schermo del terminale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-577">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="2ab27-578">Attualmente gli unici due set di caratteri supportati sono ASCII (impostazione predefinita) e il set di caratteri grafici speciali DEC.</span><span class="sxs-lookup"><span data-stu-id="2ab27-578">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="2ab27-579">Per un elenco di tutti i caratteri rappresentati dal set di caratteri grafici speciali DEC, visitare il sito Web all'indirizzo <http://vt100.net/docs/vt220-rm/table2-4.html>.</span><span class="sxs-lookup"><span data-stu-id="2ab27-579">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="2ab27-580">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-580">Sequence</span></span> | <span data-ttu-id="2ab27-581">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-581">Description</span></span> | <span data-ttu-id="2ab27-582">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-582">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="2ab27-583">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="2ab27-583">ESC ( 0</span></span> | <span data-ttu-id="2ab27-584">Designazione set di caratteri DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="2ab27-584">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="2ab27-585">Abilita la modalità DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="2ab27-585">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="2ab27-586">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="2ab27-586">ESC ( B</span></span> | <span data-ttu-id="2ab27-587">Designazione set di caratteri ASCII Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="2ab27-587">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="2ab27-588">Abilita la modalità ASCII (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="2ab27-588">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="2ab27-589">In particolare, la modalità DEC Line Drawing viene usata per disegnare i bordi nelle applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="2ab27-589">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="2ab27-590">La tabella seguente illustra il mapping tra caratteri ASCII e caratteri DEC Line Drawing.</span><span class="sxs-lookup"><span data-stu-id="2ab27-590">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="2ab27-591">Hex</span><span class="sxs-lookup"><span data-stu-id="2ab27-591">Hex</span></span> | <span data-ttu-id="2ab27-592">ASCII</span><span class="sxs-lookup"><span data-stu-id="2ab27-592">ASCII</span></span> | <span data-ttu-id="2ab27-593">DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="2ab27-593">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="2ab27-594">0x6a</span><span class="sxs-lookup"><span data-stu-id="2ab27-594">0x6a</span></span> | <span data-ttu-id="2ab27-595">j</span><span class="sxs-lookup"><span data-stu-id="2ab27-595">j</span></span> | <span data-ttu-id="2ab27-596">┘</span><span class="sxs-lookup"><span data-stu-id="2ab27-596">┘</span></span> |
| <span data-ttu-id="2ab27-597">0x6b</span><span class="sxs-lookup"><span data-stu-id="2ab27-597">0x6b</span></span> | <span data-ttu-id="2ab27-598">k</span><span class="sxs-lookup"><span data-stu-id="2ab27-598">k</span></span> | <span data-ttu-id="2ab27-599">┐</span><span class="sxs-lookup"><span data-stu-id="2ab27-599">┐</span></span> |
| <span data-ttu-id="2ab27-600">0x6c</span><span class="sxs-lookup"><span data-stu-id="2ab27-600">0x6c</span></span> | <span data-ttu-id="2ab27-601">l</span><span class="sxs-lookup"><span data-stu-id="2ab27-601">l</span></span> | <span data-ttu-id="2ab27-602">┌</span><span class="sxs-lookup"><span data-stu-id="2ab27-602">┌</span></span> |
| <span data-ttu-id="2ab27-603">0x6d</span><span class="sxs-lookup"><span data-stu-id="2ab27-603">0x6d</span></span> | <span data-ttu-id="2ab27-604">m</span><span class="sxs-lookup"><span data-stu-id="2ab27-604">m</span></span> | <span data-ttu-id="2ab27-605">└</span><span class="sxs-lookup"><span data-stu-id="2ab27-605">└</span></span> |
| <span data-ttu-id="2ab27-606">0x6e</span><span class="sxs-lookup"><span data-stu-id="2ab27-606">0x6e</span></span> | <span data-ttu-id="2ab27-607">n</span><span class="sxs-lookup"><span data-stu-id="2ab27-607">n</span></span> | <span data-ttu-id="2ab27-608">┼</span><span class="sxs-lookup"><span data-stu-id="2ab27-608">┼</span></span> |
| <span data-ttu-id="2ab27-609">0x71</span><span class="sxs-lookup"><span data-stu-id="2ab27-609">0x71</span></span> | <span data-ttu-id="2ab27-610">q</span><span class="sxs-lookup"><span data-stu-id="2ab27-610">q</span></span> | <span data-ttu-id="2ab27-611">─</span><span class="sxs-lookup"><span data-stu-id="2ab27-611">─</span></span> |
| <span data-ttu-id="2ab27-612">0x74</span><span class="sxs-lookup"><span data-stu-id="2ab27-612">0x74</span></span> | <span data-ttu-id="2ab27-613">u</span><span class="sxs-lookup"><span data-stu-id="2ab27-613">t</span></span> | <span data-ttu-id="2ab27-614">├</span><span class="sxs-lookup"><span data-stu-id="2ab27-614">├</span></span> |
| <span data-ttu-id="2ab27-615">0x75</span><span class="sxs-lookup"><span data-stu-id="2ab27-615">0x75</span></span> | <span data-ttu-id="2ab27-616">u</span><span class="sxs-lookup"><span data-stu-id="2ab27-616">u</span></span> | <span data-ttu-id="2ab27-617">┤</span><span class="sxs-lookup"><span data-stu-id="2ab27-617">┤</span></span> |
| <span data-ttu-id="2ab27-618">0x76</span><span class="sxs-lookup"><span data-stu-id="2ab27-618">0x76</span></span> | <span data-ttu-id="2ab27-619">v</span><span class="sxs-lookup"><span data-stu-id="2ab27-619">v</span></span> | <span data-ttu-id="2ab27-620">┴</span><span class="sxs-lookup"><span data-stu-id="2ab27-620">┴</span></span> |
| <span data-ttu-id="2ab27-621">0x77</span><span class="sxs-lookup"><span data-stu-id="2ab27-621">0x77</span></span> | <span data-ttu-id="2ab27-622">w</span><span class="sxs-lookup"><span data-stu-id="2ab27-622">w</span></span> | <span data-ttu-id="2ab27-623">┬</span><span class="sxs-lookup"><span data-stu-id="2ab27-623">┬</span></span> |
| <span data-ttu-id="2ab27-624">0x78</span><span class="sxs-lookup"><span data-stu-id="2ab27-624">0x78</span></span> | <span data-ttu-id="2ab27-625">x</span><span class="sxs-lookup"><span data-stu-id="2ab27-625">x</span></span> | <span data-ttu-id="2ab27-626">│</span><span class="sxs-lookup"><span data-stu-id="2ab27-626">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="2ab27-627"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Margini di scorrimento</span><span class="sxs-lookup"><span data-stu-id="2ab27-627"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="2ab27-628">Le sequenze seguenti consentono a un programma di configurare l'"area di scorrimento" dello schermo interessata dalle operazioni di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="2ab27-628">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="2ab27-629">Si tratta di un subset di righe che vengono regolate quando altrimenti lo schermo scorrerebbe, ad esempio per una sequenza '\\n' o RI.</span><span class="sxs-lookup"><span data-stu-id="2ab27-629">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="2ab27-630">Questi margini influiscono anche sulle righe modificate da Inserimento riga (IL) ed Eliminazione riga (DL), Scorrimento verso l'alto (SU) e Scorrimento verso il basso (SD).</span><span class="sxs-lookup"><span data-stu-id="2ab27-630">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="2ab27-631">I margini di scorrimento possono essere utili soprattutto per fare in modo che una parte dello schermo non scorra quando il resto dello schermo viene riempito, ad esempio con una barra del titolo nella parte superiore o una barra di stato nella parte inferiore dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-631">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="2ab27-632">Per DECSTBM sono disponibili due parametri facoltativi, &lt;t&gt; e &lt;b&gt;, usati per specificare le righe che rappresentano la riga superiore e quella inferiore dell'area di scorrimento incluse.</span><span class="sxs-lookup"><span data-stu-id="2ab27-632">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="2ab27-633">Se i parametri vengono omessi, &lt;t&gt; viene impostato automaticamente su 1 e &lt;b&gt; sull'altezza del riquadro di visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-633">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="2ab27-634">I margini di scorrimento vanno considerati per buffer. È quindi importante che il buffer alternativo e il buffer principale mantengano impostazioni separate dei margini di scorrimento (di conseguenza, un'applicazione a schermo intero nel buffer alternativo non comprometterà i margini del buffer principale).</span><span class="sxs-lookup"><span data-stu-id="2ab27-634">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="2ab27-635">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-635">Sequence</span></span> | <span data-ttu-id="2ab27-636">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-636">Code</span></span> | <span data-ttu-id="2ab27-637">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-637">Description</span></span> | <span data-ttu-id="2ab27-638">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-638">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="2ab27-639">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="2ab27-639">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="2ab27-640">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="2ab27-640">DECSTBM</span></span> | <span data-ttu-id="2ab27-641">Impostazione area di scorrimento</span><span class="sxs-lookup"><span data-stu-id="2ab27-641">Set Scrolling Region</span></span> | <span data-ttu-id="2ab27-642">Imposta i margini di scorrimento VT del riquadro di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-642">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="2ab27-643"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titolo della finestra</span><span class="sxs-lookup"><span data-stu-id="2ab27-643"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="2ab27-644">I comandi seguenti consentono all'applicazione di impostare il titolo della finestra della console sul parametro &lt;stringa&gt; specificato.</span><span class="sxs-lookup"><span data-stu-id="2ab27-644">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="2ab27-645">Per essere accettata, la stringa deve contenere meno di 255 caratteri.</span><span class="sxs-lookup"><span data-stu-id="2ab27-645">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="2ab27-646">L'operazione è equivalente alla chiamata di SetConsoleTitle con la stringa specificata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-646">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="2ab27-647">Si noti che queste sequenze sono di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza iniziano con "\\x1b\]", non con "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="2ab27-647">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="2ab27-648">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-648">Sequence</span></span> | <span data-ttu-id="2ab27-649">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-649">Description</span></span> | <span data-ttu-id="2ab27-650">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-650">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="2ab27-651">ESC \] 0 ; &lt;stringa&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="2ab27-651">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="2ab27-652">Impostazione icona e titolo finestra</span><span class="sxs-lookup"><span data-stu-id="2ab27-652">Set Icon and Window Title</span></span> | <span data-ttu-id="2ab27-653">Imposta il titolo della finestra della console su &lt;stringa&gt;.</span><span class="sxs-lookup"><span data-stu-id="2ab27-653">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="2ab27-654">ESC \] 2 ; &lt;stringa&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="2ab27-654">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="2ab27-655">Impostazione titolo finestra</span><span class="sxs-lookup"><span data-stu-id="2ab27-655">Set Window Title</span></span> | <span data-ttu-id="2ab27-656">Imposta il titolo della finestra della console su &lt;stringa&gt;.</span><span class="sxs-lookup"><span data-stu-id="2ab27-656">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="2ab27-657">Il carattere finale in queste sequenze è il carattere "Bell", '\\x07'</span><span class="sxs-lookup"><span data-stu-id="2ab27-657">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="2ab27-658"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Buffer alternativo dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-658"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="2ab27-659">Le applicazioni di tipo \*nix utilizzano spesso un buffer alternativo dello schermo, in modo da poter modificare l'intero contenuto del buffer senza influire sull'applicazione che le ha avviate.</span><span class="sxs-lookup"><span data-stu-id="2ab27-659">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="2ab27-660">Il buffer alternativo è esattamente delle dimensioni della finestra, senza area di scrollback.</span><span class="sxs-lookup"><span data-stu-id="2ab27-660">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="2ab27-661">Per un esempio di questo comportamento, si prenda in considerazione quando vim viene avviato da bash.</span><span class="sxs-lookup"><span data-stu-id="2ab27-661">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="2ab27-662">Vim usa l'intero schermo per modificare il file e quindi, tornando a bash, lascia invariato il buffer originale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-662">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="2ab27-663">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-663">Sequence</span></span> | <span data-ttu-id="2ab27-664">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-664">Description</span></span> | <span data-ttu-id="2ab27-665">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-665">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="2ab27-666">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-666">ESC \[ ?</span></span> <span data-ttu-id="2ab27-667">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="2ab27-667">1 0 4 9 h</span></span> | <span data-ttu-id="2ab27-668">Uso buffer alternativo dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-668">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="2ab27-669">Passa a un nuovo buffer alternativo dello schermo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-669">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="2ab27-670">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-670">ESC \[ ?</span></span> <span data-ttu-id="2ab27-671">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="2ab27-671">1 0 4 9 l</span></span> | <span data-ttu-id="2ab27-672">Uso buffer principale dello schermo</span><span class="sxs-lookup"><span data-stu-id="2ab27-672">Use Main Screen Buffer</span></span> | <span data-ttu-id="2ab27-673">Passa al buffer principale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-673">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="2ab27-674"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Larghezza della finestra</span><span class="sxs-lookup"><span data-stu-id="2ab27-674"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="2ab27-675">Le sequenze seguenti possono essere usate per controllare la larghezza della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="2ab27-675">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="2ab27-676">Sono approssimativamente equivalenti alla chiamata dell'API della console SetConsoleScreenBufferInfoEx per impostare la larghezza della finestra.</span><span class="sxs-lookup"><span data-stu-id="2ab27-676">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="2ab27-677">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-677">Sequence</span></span> | <span data-ttu-id="2ab27-678">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-678">Code</span></span> | <span data-ttu-id="2ab27-679">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-679">Description</span></span> | <span data-ttu-id="2ab27-680">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-680">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="2ab27-681">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-681">ESC \[ ?</span></span> <span data-ttu-id="2ab27-682">3 h</span><span class="sxs-lookup"><span data-stu-id="2ab27-682">3 h</span></span> | <span data-ttu-id="2ab27-683">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="2ab27-683">DECCOLM</span></span> | <span data-ttu-id="2ab27-684">Impostazione numero di colonne su 132</span><span class="sxs-lookup"><span data-stu-id="2ab27-684">Set Number of Columns to 132</span></span> | <span data-ttu-id="2ab27-685">Imposta la larghezza della console su una larghezza pari a 132 colonne.</span><span class="sxs-lookup"><span data-stu-id="2ab27-685">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="2ab27-686">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="2ab27-686">ESC \[ ?</span></span> <span data-ttu-id="2ab27-687">3 l</span><span class="sxs-lookup"><span data-stu-id="2ab27-687">3 l</span></span> | <span data-ttu-id="2ab27-688">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="2ab27-688">DECCOLM</span></span> | <span data-ttu-id="2ab27-689">Impostazione numero di colonne su 80</span><span class="sxs-lookup"><span data-stu-id="2ab27-689">Set Number of Columns to 80</span></span> | <span data-ttu-id="2ab27-690">Imposta la larghezza della console su una larghezza pari a 80 colonne.</span><span class="sxs-lookup"><span data-stu-id="2ab27-690">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="2ab27-691"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft reset</span><span class="sxs-lookup"><span data-stu-id="2ab27-691"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="2ab27-692">La sequenza seguente può essere usata per reimpostare i valori predefiniti di determinate proprietà. Le proprietà seguenti vengono reimpostate sui valori predefiniti indicati di seguito (sono elencate anche le sequenze che controllano tali proprietà):</span><span class="sxs-lookup"><span data-stu-id="2ab27-692">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="2ab27-693">Visibilità cursore: visibile (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-693">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="2ab27-694">Tastierino numerico: modalità numerica (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-694">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="2ab27-695">Modalità tasti cursore: modalità normale (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-695">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="2ab27-696">Margini superiore e inferiore: superiore = 1, inferiore = altezza console (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-696">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="2ab27-697">Set di caratteri: ASCII Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="2ab27-697">Character Set: US ASCII</span></span>
- <span data-ttu-id="2ab27-698">Rendering grafica: predefinito/off (SGR)</span><span class="sxs-lookup"><span data-stu-id="2ab27-698">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="2ab27-699">Salvataggio stato cursore: posizione Home (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="2ab27-699">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="2ab27-700">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-700">Sequence</span></span> | <span data-ttu-id="2ab27-701">Codice</span><span class="sxs-lookup"><span data-stu-id="2ab27-701">Code</span></span> | <span data-ttu-id="2ab27-702">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2ab27-702">Description</span></span> | <span data-ttu-id="2ab27-703">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ab27-703">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="2ab27-704">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="2ab27-704">ESC \[ !</span></span> <span data-ttu-id="2ab27-705">p</span><span class="sxs-lookup"><span data-stu-id="2ab27-705">p</span></span> | <span data-ttu-id="2ab27-706">DECSTR</span><span class="sxs-lookup"><span data-stu-id="2ab27-706">DECSTR</span></span> | <span data-ttu-id="2ab27-707">Soft reset</span><span class="sxs-lookup"><span data-stu-id="2ab27-707">Soft Reset</span></span> | <span data-ttu-id="2ab27-708">Ripristina i valori predefiniti di determinate impostazioni del terminale.</span><span class="sxs-lookup"><span data-stu-id="2ab27-708">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="2ab27-709"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Sequenze di input</span><span class="sxs-lookup"><span data-stu-id="2ab27-709"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="2ab27-710">Le sequenze di terminale seguenti vengono generate dall'host della console nel flusso di input se il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT viene impostato sull'handle del buffer di input usando il flag SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="2ab27-710">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="2ab27-711">Sono disponibili due modalità interne che controllano le sequenze generate per i tasti di input specificati: la modalità tasti cursore e la modalità tasti del tastierino.</span><span class="sxs-lookup"><span data-stu-id="2ab27-711">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="2ab27-712">Queste modalità sono descritte nella sezione Modifiche della modalità.</span><span class="sxs-lookup"><span data-stu-id="2ab27-712">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="2ab27-713"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Tasti cursore</span><span class="sxs-lookup"><span data-stu-id="2ab27-713"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="2ab27-714">Chiave</span><span class="sxs-lookup"><span data-stu-id="2ab27-714">Key</span></span> | <span data-ttu-id="2ab27-715">Modalità normale</span><span class="sxs-lookup"><span data-stu-id="2ab27-715">Normal Mode</span></span> | <span data-ttu-id="2ab27-716">Modalità applicazione</span><span class="sxs-lookup"><span data-stu-id="2ab27-716">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="2ab27-717">Freccia SU</span><span class="sxs-lookup"><span data-stu-id="2ab27-717">Up Arrow</span></span> | <span data-ttu-id="2ab27-718">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="2ab27-718">ESC \[ A</span></span> | <span data-ttu-id="2ab27-719">ESC O A</span><span class="sxs-lookup"><span data-stu-id="2ab27-719">ESC O A</span></span> |
| <span data-ttu-id="2ab27-720">Freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="2ab27-720">Down Arrow</span></span> | <span data-ttu-id="2ab27-721">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="2ab27-721">ESC \[ B</span></span> | <span data-ttu-id="2ab27-722">ESC O B</span><span class="sxs-lookup"><span data-stu-id="2ab27-722">ESC O B</span></span> |
| <span data-ttu-id="2ab27-723">Freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-723">Right Arrow</span></span> | <span data-ttu-id="2ab27-724">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="2ab27-724">ESC \[ C</span></span> | <span data-ttu-id="2ab27-725">ESC O C</span><span class="sxs-lookup"><span data-stu-id="2ab27-725">ESC O C</span></span> |
| <span data-ttu-id="2ab27-726">Freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-726">Left Arrow</span></span> | <span data-ttu-id="2ab27-727">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="2ab27-727">ESC \[ D</span></span> | <span data-ttu-id="2ab27-728">ESC O D</span><span class="sxs-lookup"><span data-stu-id="2ab27-728">ESC O D</span></span> |
| <span data-ttu-id="2ab27-729">Home</span><span class="sxs-lookup"><span data-stu-id="2ab27-729">Home</span></span> | <span data-ttu-id="2ab27-730">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="2ab27-730">ESC \[ H</span></span> | <span data-ttu-id="2ab27-731">ESC O H</span><span class="sxs-lookup"><span data-stu-id="2ab27-731">ESC O H</span></span> |
| <span data-ttu-id="2ab27-732">Fine</span><span class="sxs-lookup"><span data-stu-id="2ab27-732">End</span></span> | <span data-ttu-id="2ab27-733">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="2ab27-733">ESC \[ F</span></span> | <span data-ttu-id="2ab27-734">ESC O F</span><span class="sxs-lookup"><span data-stu-id="2ab27-734">ESC O F</span></span> |



<span data-ttu-id="2ab27-735">Inoltre, se si preme CTRL con uno qualsiasi di questi tasti, vengono generate le sequenze seguenti, indipendentemente dalla modalità tasti cursore:</span><span class="sxs-lookup"><span data-stu-id="2ab27-735">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="2ab27-736">Chiave</span><span class="sxs-lookup"><span data-stu-id="2ab27-736">Key</span></span> | <span data-ttu-id="2ab27-737">Qualsiasi modalità</span><span class="sxs-lookup"><span data-stu-id="2ab27-737">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="2ab27-738">CTRL + freccia SU</span><span class="sxs-lookup"><span data-stu-id="2ab27-738">Ctrl + Up Arrow</span></span> | <span data-ttu-id="2ab27-739">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="2ab27-739">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="2ab27-740">CTRL + freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="2ab27-740">Ctrl + Down Arrow</span></span> | <span data-ttu-id="2ab27-741">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="2ab27-741">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="2ab27-742">CTRL + freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-742">Ctrl + Right Arrow</span></span> | <span data-ttu-id="2ab27-743">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="2ab27-743">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="2ab27-744">CTRL + freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-744">Ctrl + Left Arrow</span></span> | <span data-ttu-id="2ab27-745">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="2ab27-745">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="2ab27-746"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Tastierino numerico e tasti funzione</span><span class="sxs-lookup"><span data-stu-id="2ab27-746"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="2ab27-747">Chiave</span><span class="sxs-lookup"><span data-stu-id="2ab27-747">Key</span></span> | <span data-ttu-id="2ab27-748">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-748">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="2ab27-749">Backspace</span><span class="sxs-lookup"><span data-stu-id="2ab27-749">Backspace</span></span> | <span data-ttu-id="2ab27-750">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="2ab27-750">0x7f (DEL)</span></span> |
| <span data-ttu-id="2ab27-751">Sospendi</span><span class="sxs-lookup"><span data-stu-id="2ab27-751">Pause</span></span> | <span data-ttu-id="2ab27-752">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="2ab27-752">0x1a (SUB)</span></span> |
| <span data-ttu-id="2ab27-753">Carattere speciale di escape</span><span class="sxs-lookup"><span data-stu-id="2ab27-753">Escape</span></span> | <span data-ttu-id="2ab27-754">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="2ab27-754">0x1b (ESC)</span></span> |
| <span data-ttu-id="2ab27-755">Insert</span><span class="sxs-lookup"><span data-stu-id="2ab27-755">Insert</span></span> | <span data-ttu-id="2ab27-756">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-756">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="2ab27-757">Elimina</span><span class="sxs-lookup"><span data-stu-id="2ab27-757">Delete</span></span> | <span data-ttu-id="2ab27-758">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-758">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="2ab27-759">PGSU</span><span class="sxs-lookup"><span data-stu-id="2ab27-759">Page Up</span></span> | <span data-ttu-id="2ab27-760">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-760">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="2ab27-761">PGGIÙ</span><span class="sxs-lookup"><span data-stu-id="2ab27-761">Page Down</span></span> | <span data-ttu-id="2ab27-762">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-762">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="2ab27-763">F1</span><span class="sxs-lookup"><span data-stu-id="2ab27-763">F1</span></span> | <span data-ttu-id="2ab27-764">ESC O P</span><span class="sxs-lookup"><span data-stu-id="2ab27-764">ESC O P</span></span> |
| <span data-ttu-id="2ab27-765">F2</span><span class="sxs-lookup"><span data-stu-id="2ab27-765">F2</span></span> | <span data-ttu-id="2ab27-766">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="2ab27-766">ESC O Q</span></span> |
| <span data-ttu-id="2ab27-767">F3</span><span class="sxs-lookup"><span data-stu-id="2ab27-767">F3</span></span> | <span data-ttu-id="2ab27-768">ESC O R</span><span class="sxs-lookup"><span data-stu-id="2ab27-768">ESC O R</span></span> |
| <span data-ttu-id="2ab27-769">F4</span><span class="sxs-lookup"><span data-stu-id="2ab27-769">F4</span></span> | <span data-ttu-id="2ab27-770">ESC O S</span><span class="sxs-lookup"><span data-stu-id="2ab27-770">ESC O S</span></span> |
| <span data-ttu-id="2ab27-771">F5</span><span class="sxs-lookup"><span data-stu-id="2ab27-771">F5</span></span> | <span data-ttu-id="2ab27-772">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-772">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="2ab27-773">F6</span><span class="sxs-lookup"><span data-stu-id="2ab27-773">F6</span></span> | <span data-ttu-id="2ab27-774">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-774">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="2ab27-775">F7</span><span class="sxs-lookup"><span data-stu-id="2ab27-775">F7</span></span> | <span data-ttu-id="2ab27-776">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-776">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="2ab27-777">F8</span><span class="sxs-lookup"><span data-stu-id="2ab27-777">F8</span></span> | <span data-ttu-id="2ab27-778">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-778">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="2ab27-779">F9</span><span class="sxs-lookup"><span data-stu-id="2ab27-779">F9</span></span> | <span data-ttu-id="2ab27-780">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-780">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="2ab27-781">F10</span><span class="sxs-lookup"><span data-stu-id="2ab27-781">F10</span></span> | <span data-ttu-id="2ab27-782">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-782">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="2ab27-783">F11</span><span class="sxs-lookup"><span data-stu-id="2ab27-783">F11</span></span> | <span data-ttu-id="2ab27-784">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-784">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="2ab27-785">F12</span><span class="sxs-lookup"><span data-stu-id="2ab27-785">F12</span></span> | <span data-ttu-id="2ab27-786">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="2ab27-786">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="2ab27-787"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificatori</span><span class="sxs-lookup"><span data-stu-id="2ab27-787"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="2ab27-788">Il tasto ALT viene trattato anteponendo alla sequenza un carattere di escape: ESC &lt;c&gt; dove &lt;c&gt; è il carattere passato dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-788">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="2ab27-789">La combinazione di tasti ALT + CTRL viene gestita allo stesso modo, tranne per il fatto che il sistema operativo avrà preliminarmente spostato il tasto &lt;c&gt; sul carattere di controllo appropriato che verrà inoltrato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-789">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="2ab27-790">Il tasto CTRL viene in genere passato esattamente come viene ricevuto dal sistema.</span><span class="sxs-lookup"><span data-stu-id="2ab27-790">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="2ab27-791">Si tratta in genere di un singolo carattere spostato nello spazio riservato al carattere di controllo (0x0-0x1f).</span><span class="sxs-lookup"><span data-stu-id="2ab27-791">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="2ab27-792">Ad esempio, CTRL + @ (0x40) diventa NUL (0x00), CTRL + \[ (0x5b) diventa ESC (0x1b) e così via. Alcune combinazioni con il tasto CTRL vengono trattate in modo speciale in base alla tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="2ab27-792">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="2ab27-793">Chiave</span><span class="sxs-lookup"><span data-stu-id="2ab27-793">Key</span></span> | <span data-ttu-id="2ab27-794">Sequenza</span><span class="sxs-lookup"><span data-stu-id="2ab27-794">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="2ab27-795">CTRL+BARRA SPAZIATRICE</span><span class="sxs-lookup"><span data-stu-id="2ab27-795">Ctrl + Space</span></span> | <span data-ttu-id="2ab27-796">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="2ab27-796">0x00 (NUL)</span></span> |
| <span data-ttu-id="2ab27-797">CTRL + freccia SU</span><span class="sxs-lookup"><span data-stu-id="2ab27-797">Ctrl + Up Arrow</span></span> | <span data-ttu-id="2ab27-798">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="2ab27-798">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="2ab27-799">CTRL + freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="2ab27-799">Ctrl + Down Arrow</span></span> | <span data-ttu-id="2ab27-800">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="2ab27-800">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="2ab27-801">CTRL + freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-801">Ctrl + Right Arrow</span></span> | <span data-ttu-id="2ab27-802">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="2ab27-802">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="2ab27-803">CTRL + freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="2ab27-803">Ctrl + Left Arrow</span></span> | <span data-ttu-id="2ab27-804">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="2ab27-804">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="2ab27-805">La combinazione <kbd>CTRL</kbd> sinistra + <kbd>ALT</kbd> destra viene trattata come ALT GR.</span><span class="sxs-lookup"><span data-stu-id="2ab27-805">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="2ab27-806">Quando entrambi gli elementi vengono visualizzati insieme, vengono rimossi e il valore Unicode del carattere presentato dal sistema viene passato nella destinazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-806">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="2ab27-807">Il sistema eseguirà la conversione preliminare dei valori di ALT GR in base alle impostazioni di input di sistema correnti.</span><span class="sxs-lookup"><span data-stu-id="2ab27-807">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="2ab27-808"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Esempi</span><span class="sxs-lookup"><span data-stu-id="2ab27-808"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="2ab27-809"><span id="example"></span><span id="EXAMPLE"></span>Esempio di sequenze di terminale SGR</span><span class="sxs-lookup"><span data-stu-id="2ab27-809"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="2ab27-810">Il codice seguente fornisce alcuni esempi di formattazione del testo.</span><span class="sxs-lookup"><span data-stu-id="2ab27-810">The following code provides several examples of text formatting.</span></span>

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

> [!NOTE]
><span data-ttu-id="2ab27-811">Nell'esempio precedente la stringa '`\x1b[31m`' è l'implementazione di **ESC \[ &lt;n&gt; m** dove &lt;n&gt; è uguale a 31.</span><span class="sxs-lookup"><span data-stu-id="2ab27-811">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="2ab27-812">La figura seguente mostra l'output dell'esempio di codice precedente.</span><span class="sxs-lookup"><span data-stu-id="2ab27-812">The following graphic shows the output of the previous code example.</span></span>

![output della console con il comando sgr](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="2ab27-814"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Esempio di abilitazione dell'elaborazione del terminale virtuale</span><span class="sxs-lookup"><span data-stu-id="2ab27-814"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="2ab27-815">Il codice seguente fornisce un esempio della modalità consigliata per abilitare l'elaborazione del terminale virtuale per un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2ab27-815">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="2ab27-816">Lo scopo dell'esempio è dimostrare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="2ab27-816">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="2ab27-817">La modalità esistente deve sempre essere recuperata tramite GetConsoleMode e analizzata prima di essere impostata con SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="2ab27-817">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="2ab27-818">Verificare se SetConsoleMode restituisce `0` e GetLastError restituisce STATUS\_INVALID\_PARAMETER è il meccanismo corrente per determinare l'esecuzione in un sistema di livello inferiore.</span><span class="sxs-lookup"><span data-stu-id="2ab27-818">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="2ab27-819">Un'applicazione che riceve STATUS\_INVALID\_PARAMETER con uno dei flag di modalità della console più recenti nel campo bit dovrebbe scalare automaticamente il comportamento e riprovare.</span><span class="sxs-lookup"><span data-stu-id="2ab27-819">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="2ab27-820"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Esempio di alcune funzionalità dell'aggiornamento dell'anniversario</span><span class="sxs-lookup"><span data-stu-id="2ab27-820"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="2ab27-821">L'esempio seguente è destinato a essere un esempio di codice più affidabile che usa una serie di sequenze di escape per modificare il buffer, con particolare attenzione alle funzionalità aggiunte nell'aggiornamento dell'anniversario per Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2ab27-821">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="2ab27-822">Questo esempio usa il buffer alternativo dello schermo, la modifica delle tabulazioni, l'impostazione dei margini di scorrimento e la modifica del set di caratteri.</span><span class="sxs-lookup"><span data-stu-id="2ab27-822">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
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
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // bright yellow on bright blue
    printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m"); // restore color
    printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // Make the border bright yellow on bright blue
    printf(fIsTop ? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++)
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop ? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(const char* const pszMessage, COORD const Size)
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
    Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

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
    printf(CSI "3;%dr", Size.Y - 2);
    int iNumLines = Size.Y - 4;

    printf(CSI "1;1H");
    printf(CSI "102;30m");
    printf("Windows 10 Anniversary Update - VT Example");
    printf(CSI "0m");

    // Print a top border - Yellow
    printf(CSI "2;1H");
    PrintHorizontalBorder(Size, true);

    // // Print a bottom border
    printf(CSI "%d;1H", Size.Y - 1);
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
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder();// print border at right side
        if (line + 1 != iNumLines)
            printf("\t"); // advance to next tab stop, (on the next line)
    }

    PrintStatusLine("Press any key to demonstrate scroll margins", Size);
    wch = _getwch();

    printf(CSI "3;1H");
    for (line = 0; line < iNumLines * 2; line++)
    {
        printf(CSI "K"); // clear the line
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder(); // print border at right side
        if (line + 1 != iNumLines * 2)
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
