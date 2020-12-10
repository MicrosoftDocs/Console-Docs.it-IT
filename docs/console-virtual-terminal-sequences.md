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
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "93039149"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="9dcde-104">Sequenze del terminale virtuale della console</span><span class="sxs-lookup"><span data-stu-id="9dcde-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="9dcde-105">Le sequenze di terminale virtuale sono sequenze di caratteri di controllo in grado di controllare lo spostamento del cursore, la modalità colore/tipo di carattere e altre operazioni quando vengono scritte nel flusso di output.</span><span class="sxs-lookup"><span data-stu-id="9dcde-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="9dcde-106">Le sequenze possono anche essere ricevute nel flusso di input in risposta a una sequenza di informazioni di query del flusso di output o come codifica dell'input utente quando viene impostata la modalità appropriata.</span><span class="sxs-lookup"><span data-stu-id="9dcde-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="9dcde-107">Per configurare questo comportamento, è possibile usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="9dcde-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="9dcde-108">Alla fine di questo documento è incluso un esempio della modalità consigliata per abilitare i comportamenti del terminale virtuale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="9dcde-109">Il comportamento delle sequenze seguenti si basa su VT100 e sulle tecnologie dell'emulatore di terminale derivate, in particolare sull'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="9dcde-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="9dcde-110">Per altre informazioni sulle sequenze di terminale, visitare i siti Web agli indirizzi <http://vt100.net> e <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span><span class="sxs-lookup"><span data-stu-id="9dcde-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="9dcde-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Sequenze di output</span><span class="sxs-lookup"><span data-stu-id="9dcde-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="9dcde-112">Le sequenze di terminale seguenti vengono intercettate dall'host della console quando vengono scritte nel flusso di output se il flag ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING viene impostato sull'handle del buffer dello schermo usando la funzione [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="9dcde-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="9dcde-113">Si noti che il flag DISABLE\_NEWLINE\_AUTO\_RETURN può essere utile anche per emulare il posizionamento del cursore e il comportamento di scorrimento di altri emulatori di terminale in relazione ai caratteri scritti nella colonna finale di qualsiasi riga.</span><span class="sxs-lookup"><span data-stu-id="9dcde-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="9dcde-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posizionamento semplice del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="9dcde-115">In tutte le descrizioni seguenti ESC è sempre rappresentato dal valore esadecimale 0x1B.</span><span class="sxs-lookup"><span data-stu-id="9dcde-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="9dcde-116">Non è necessario includere spazi nelle sequenze di terminale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="9dcde-117">Per informazioni su come vengono usate in pratica le sequenze, vedere l'[esempio](#example) alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="9dcde-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="9dcde-118">Nella tabella seguente vengono descritte le sequenze di escape semplici con un solo comando di azione subito dopo il carattere ESC.</span><span class="sxs-lookup"><span data-stu-id="9dcde-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="9dcde-119">Queste sequenze non hanno parametri e hanno effetto immediato.</span><span class="sxs-lookup"><span data-stu-id="9dcde-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="9dcde-120">Tutti i comandi inclusi in questa tabella sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md) per posizionare il cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="9dcde-121">Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="9dcde-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="9dcde-122">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="9dcde-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="9dcde-123">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-123">Sequence</span></span> | <span data-ttu-id="9dcde-124">Sintassi abbreviata</span><span class="sxs-lookup"><span data-stu-id="9dcde-124">Shorthand</span></span> | <span data-ttu-id="9dcde-125">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="9dcde-126">ESC A</span></span> | <span data-ttu-id="9dcde-127">CUU</span><span class="sxs-lookup"><span data-stu-id="9dcde-127">CUU</span></span> | <span data-ttu-id="9dcde-128">Cursore su di 1</span><span class="sxs-lookup"><span data-stu-id="9dcde-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="9dcde-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="9dcde-129">ESC B</span></span> | <span data-ttu-id="9dcde-130">CUD</span><span class="sxs-lookup"><span data-stu-id="9dcde-130">CUD</span></span> | <span data-ttu-id="9dcde-131">Cursore giù di 1</span><span class="sxs-lookup"><span data-stu-id="9dcde-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="9dcde-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="9dcde-132">ESC C</span></span> | <span data-ttu-id="9dcde-133">CUF</span><span class="sxs-lookup"><span data-stu-id="9dcde-133">CUF</span></span> | <span data-ttu-id="9dcde-134">Cursore avanti (verso destra) di 1</span><span class="sxs-lookup"><span data-stu-id="9dcde-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="9dcde-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="9dcde-135">ESC D</span></span> | <span data-ttu-id="9dcde-136">CUB</span><span class="sxs-lookup"><span data-stu-id="9dcde-136">CUB</span></span> | <span data-ttu-id="9dcde-137">Cursore indietro (verso sinistra) di 1</span><span class="sxs-lookup"><span data-stu-id="9dcde-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="9dcde-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="9dcde-138">ESC M</span></span> | <span data-ttu-id="9dcde-139">RI</span><span class="sxs-lookup"><span data-stu-id="9dcde-139">RI</span></span> | <span data-ttu-id="9dcde-140">Indice inverso: esegue l'operazione inversa di \\n, sposta il cursore verso l'alto di una riga, mantiene la posizione orizzontale, scorre il buffer se necessario\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="9dcde-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="9dcde-141">ESC 7</span></span> | <span data-ttu-id="9dcde-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="9dcde-142">DECSC</span></span> | <span data-ttu-id="9dcde-143">Salva la posizione del cursore in memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="9dcde-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="9dcde-144">ESC 8</span></span> | <span data-ttu-id="9dcde-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="9dcde-145">DECSR</span></span> | <span data-ttu-id="9dcde-146">Ripristina la posizione del cursore dalla memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="9dcde-147">\* Se sono impostati i margini di scorrimento, RI all'interno dei margini scorrerà solo il contenuto dei margini e lascerà invariato il riquadro di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="9dcde-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="9dcde-148">(vedere Margini di scorrimento).</span><span class="sxs-lookup"><span data-stu-id="9dcde-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="9dcde-149">\*\*Non sarà presente alcun valore salvato in memoria fino al primo utilizzo del comando di salvataggop.</span><span class="sxs-lookup"><span data-stu-id="9dcde-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="9dcde-150">L'unico modo per accedere al valore salvato è tramite il comando di ripristino.</span><span class="sxs-lookup"><span data-stu-id="9dcde-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="9dcde-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posizionamento del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="9dcde-152">Le tabelle seguenti includono le sequenze di tipo CSI (Control Sequence Introducer).</span><span class="sxs-lookup"><span data-stu-id="9dcde-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="9dcde-153">Tutte le sequenze CSI iniziano con ESC (0x1B) seguito da \[ (parentesi quadra aperta, 0x5B) e possono contenere parametri di lunghezza variabile per specificare altre informazioni per ogni operazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="9dcde-154">Tali informazioni saranno rappresentate dalla sintassi abbreviata &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="9dcde-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="9dcde-155">Ogni tabella riportata di seguito è raggruppata per funzionalità, con note sotto ogni tabella che illustrano il funzionamento del gruppo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="9dcde-156">Se non diversamente specificato, le regole seguenti si applicano a tutti i parametri:</span><span class="sxs-lookup"><span data-stu-id="9dcde-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="9dcde-157">&lt;n&gt; rappresenta la distanza di spostamento ed è un parametro facoltativo</span><span class="sxs-lookup"><span data-stu-id="9dcde-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="9dcde-158">Se &lt;n&gt; viene omesso o è uguale a 0, verrà considerato come 1</span><span class="sxs-lookup"><span data-stu-id="9dcde-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="9dcde-159">&lt;n&gt; non può essere maggiore di 32.767 (valore short massimo)</span><span class="sxs-lookup"><span data-stu-id="9dcde-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="9dcde-160">&lt;n&gt; non può essere un valore negativo</span><span class="sxs-lookup"><span data-stu-id="9dcde-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="9dcde-161">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorPosition**](setconsolecursorposition.md).</span><span class="sxs-lookup"><span data-stu-id="9dcde-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="9dcde-162">Lo spostamento del cursore verrà limitato dal riquadro di visualizzazione corrente nel buffer.</span><span class="sxs-lookup"><span data-stu-id="9dcde-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="9dcde-163">Lo scorrimento, se disponibile, non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="9dcde-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="9dcde-164">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-164">Sequence</span></span> | <span data-ttu-id="9dcde-165">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-165">Code</span></span> | <span data-ttu-id="9dcde-166">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-166">Description</span></span> | <span data-ttu-id="9dcde-167">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="9dcde-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="9dcde-169">CUU</span><span class="sxs-lookup"><span data-stu-id="9dcde-169">CUU</span></span> | <span data-ttu-id="9dcde-170">Cursore su</span><span class="sxs-lookup"><span data-stu-id="9dcde-170">Cursor Up</span></span> | <span data-ttu-id="9dcde-171">Cursore su di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="9dcde-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="9dcde-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="9dcde-173">CUD</span><span class="sxs-lookup"><span data-stu-id="9dcde-173">CUD</span></span> | <span data-ttu-id="9dcde-174">Cursore giù</span><span class="sxs-lookup"><span data-stu-id="9dcde-174">Cursor Down</span></span> | <span data-ttu-id="9dcde-175">Cursore giù di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="9dcde-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="9dcde-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="9dcde-177">CUF</span><span class="sxs-lookup"><span data-stu-id="9dcde-177">CUF</span></span> | <span data-ttu-id="9dcde-178">Cursore avanti</span><span class="sxs-lookup"><span data-stu-id="9dcde-178">Cursor Forward</span></span> | <span data-ttu-id="9dcde-179">Cursore avanti (verso destra) di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="9dcde-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="9dcde-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="9dcde-181">CUB</span><span class="sxs-lookup"><span data-stu-id="9dcde-181">CUB</span></span> | <span data-ttu-id="9dcde-182">Cursore indietro</span><span class="sxs-lookup"><span data-stu-id="9dcde-182">Cursor Backward</span></span> | <span data-ttu-id="9dcde-183">Cursore indietro (verso sinistra) di &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="9dcde-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="9dcde-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="9dcde-185">CNL</span><span class="sxs-lookup"><span data-stu-id="9dcde-185">CNL</span></span> | <span data-ttu-id="9dcde-186">Cursore riga successiva</span><span class="sxs-lookup"><span data-stu-id="9dcde-186">Cursor Next Line</span></span> | <span data-ttu-id="9dcde-187">Cursore giù di &lt;n&gt; righe dalla posizione corrente</span><span class="sxs-lookup"><span data-stu-id="9dcde-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="9dcde-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="9dcde-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="9dcde-189">CPL</span><span class="sxs-lookup"><span data-stu-id="9dcde-189">CPL</span></span> | <span data-ttu-id="9dcde-190">Cursore riga precedente</span><span class="sxs-lookup"><span data-stu-id="9dcde-190">Cursor Previous Line</span></span> | <span data-ttu-id="9dcde-191">Cursore su &lt;n&gt; righe dalla posizione corrente</span><span class="sxs-lookup"><span data-stu-id="9dcde-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="9dcde-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="9dcde-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="9dcde-193">CHA</span><span class="sxs-lookup"><span data-stu-id="9dcde-193">CHA</span></span> | <span data-ttu-id="9dcde-194">Cursore assoluto orizzontale</span><span class="sxs-lookup"><span data-stu-id="9dcde-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="9dcde-195">Il cursore si sposta orizzontalmente alla posizione &lt;n&gt; nella riga corrente</span><span class="sxs-lookup"><span data-stu-id="9dcde-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="9dcde-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="9dcde-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="9dcde-197">VPA</span><span class="sxs-lookup"><span data-stu-id="9dcde-197">VPA</span></span> | <span data-ttu-id="9dcde-198">Assoluto posizione riga verticale</span><span class="sxs-lookup"><span data-stu-id="9dcde-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="9dcde-199">Il cursore si sposta verticalmente alla posizione &lt;n&gt; nella colonna corrente</span><span class="sxs-lookup"><span data-stu-id="9dcde-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="9dcde-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="9dcde-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="9dcde-201">CUP</span><span class="sxs-lookup"><span data-stu-id="9dcde-201">CUP</span></span> | <span data-ttu-id="9dcde-202">Posizione cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-202">Cursor Position</span></span> | <span data-ttu-id="9dcde-203">\*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="9dcde-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="9dcde-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="9dcde-205">HVP</span><span class="sxs-lookup"><span data-stu-id="9dcde-205">HVP</span></span> | <span data-ttu-id="9dcde-206">Posizione verticale orizzontale</span><span class="sxs-lookup"><span data-stu-id="9dcde-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="9dcde-207">\*Il cursore si sposta alla coordinata &lt;x&gt;; &lt;y&gt; all'interno del riquadro di visualizzazione, dove &lt;x&gt; è la colonna della riga &lt;y&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="9dcde-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="9dcde-208">ESC \[ s</span></span> | <span data-ttu-id="9dcde-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="9dcde-209">ANSISYSSC</span></span> | <span data-ttu-id="9dcde-210">Salvataggio cursore - Emulazione Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="9dcde-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="9dcde-211">\*\*Senza parametri, esegue un'operazione di salvataggio del cursore come DECSC</span><span class="sxs-lookup"><span data-stu-id="9dcde-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="9dcde-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="9dcde-212">ESC \[ u</span></span> | <span data-ttu-id="9dcde-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="9dcde-213">ANSISYSSC</span></span> | <span data-ttu-id="9dcde-214">Ripristino cursore - Emulazione Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="9dcde-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="9dcde-215">\*\*Senza parametri, esegue un'operazione di ripristino del cursore come DECRC</span><span class="sxs-lookup"><span data-stu-id="9dcde-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="9dcde-216">\*I parametri &lt;x&gt; e &lt;y&gt; hanno le stesse limitazioni del valore &lt;n&gt; sopraindicato.</span><span class="sxs-lookup"><span data-stu-id="9dcde-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="9dcde-217">Se &lt;x&gt; e &lt;y&gt; vengono omessi, verranno impostati su 1;1.</span><span class="sxs-lookup"><span data-stu-id="9dcde-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="9dcde-218">\*\*La documentazione cronologica relativa ad ANSI.sys è disponibile nel sito Web all'indirizzo <https://msdn.microsoft.com/library/cc722862.aspx> e viene implementata per praticità e/o compatibilità.</span><span class="sxs-lookup"><span data-stu-id="9dcde-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="9dcde-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilità del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="9dcde-220">I comandi seguenti controllano la visibilità del cursore e del relativo stato intermittente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="9dcde-221">Le sequenze DECTCEM sono generalmente equivalenti alla chiamata dell'API della console [**SetConsoleCursorInfo**](setconsolecursorinfo.md) per attivare o disattivare la visibilità del cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="9dcde-222">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-222">Sequence</span></span> | <span data-ttu-id="9dcde-223">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-223">Code</span></span> | <span data-ttu-id="9dcde-224">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-224">Description</span></span> | <span data-ttu-id="9dcde-225">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="9dcde-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-226">ESC \[ ?</span></span> <span data-ttu-id="9dcde-227">12 h</span><span class="sxs-lookup"><span data-stu-id="9dcde-227">12 h</span></span> | <span data-ttu-id="9dcde-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="9dcde-228">ATT160</span></span> | <span data-ttu-id="9dcde-229">Abilitazione cursore di testo intermittente</span><span class="sxs-lookup"><span data-stu-id="9dcde-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="9dcde-230">Avvia lo stato intermittente del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="9dcde-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-231">ESC \[ ?</span></span> <span data-ttu-id="9dcde-232">12 l</span><span class="sxs-lookup"><span data-stu-id="9dcde-232">12 l</span></span> | <span data-ttu-id="9dcde-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="9dcde-233">ATT160</span></span> | <span data-ttu-id="9dcde-234">Disabilitazione cursore di testo intermittente</span><span class="sxs-lookup"><span data-stu-id="9dcde-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="9dcde-235">Interrompe lo stato intermittente del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="9dcde-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-236">ESC \[ ?</span></span> <span data-ttu-id="9dcde-237">25 h</span><span class="sxs-lookup"><span data-stu-id="9dcde-237">25 h</span></span> | <span data-ttu-id="9dcde-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="9dcde-238">DECTCEM</span></span> | <span data-ttu-id="9dcde-239">Abilitazione cursore di testo in modalità Mostra</span><span class="sxs-lookup"><span data-stu-id="9dcde-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="9dcde-240">Mostra il cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-240">Show the cursor</span></span> |
| <span data-ttu-id="9dcde-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-241">ESC \[ ?</span></span> <span data-ttu-id="9dcde-242">25 l</span><span class="sxs-lookup"><span data-stu-id="9dcde-242">25 l</span></span> | <span data-ttu-id="9dcde-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="9dcde-243">DECTCEM</span></span> | <span data-ttu-id="9dcde-244">Abilitazione cursore di testo in modalità Nascondi</span><span class="sxs-lookup"><span data-stu-id="9dcde-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="9dcde-245">Nasconde il cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="9dcde-246">Le sequenze di abilitazione terminano con un carattere H minuscolo (`h`), mentre le sequenze di disabilitazione terminano con un carattere L minuscolo (`l`).</span><span class="sxs-lookup"><span data-stu-id="9dcde-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="9dcde-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posizionamento del riquadro di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="9dcde-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="9dcde-248">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata dell'API della console [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per spostare il contenuto del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="9dcde-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="9dcde-249">**Attenzione** I nomi dei comandi sono fuorvianti.</span><span class="sxs-lookup"><span data-stu-id="9dcde-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="9dcde-250">Il termine "scorrere" si riferisce alla direzione di spostamento del testo durante l'operazione, non alla modalità di spostamento del riquadro di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="9dcde-251">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-251">Sequence</span></span> | <span data-ttu-id="9dcde-252">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-252">Code</span></span> | <span data-ttu-id="9dcde-253">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-253">Description</span></span> | <span data-ttu-id="9dcde-254">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="9dcde-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="9dcde-256">Unità di streaming (SU)</span><span class="sxs-lookup"><span data-stu-id="9dcde-256">SU</span></span> | <span data-ttu-id="9dcde-257">Scorrimento verso l'alto</span><span class="sxs-lookup"><span data-stu-id="9dcde-257">Scroll Up</span></span> | <span data-ttu-id="9dcde-258">Scorrimento del testo verso l'alto di &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="9dcde-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="9dcde-259">Operazione nota anche come "panoramica in basso", dove le nuove righe vengono compilate a partire dalla parte inferiore dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="9dcde-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="9dcde-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="9dcde-261">DS</span><span class="sxs-lookup"><span data-stu-id="9dcde-261">SD</span></span> | <span data-ttu-id="9dcde-262">Scorrimento verso il basso</span><span class="sxs-lookup"><span data-stu-id="9dcde-262">Scroll Down</span></span> | <span data-ttu-id="9dcde-263">Scorrimento verso il basso di &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="9dcde-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="9dcde-264">Operazione nota anche come "panoramica in alto", dove le nuove righe vengono compilate a partire dalla parte superiore dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="9dcde-265">Il testo viene spostato a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="9dcde-266">Se il cursore si trova nella riga centrale del riquadro di visualizzazione, lo scorrimento verso l'alto determinerà lo spostamento della metà inferiore del riquadro e l'inserimento di righe vuote in fondo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="9dcde-267">Lo scorrimento verso il basso determinerà lo spostamento della metà superiore delle righe del riquadro di visualizzazione e l'inserimento di nuove righe in cima.</span><span class="sxs-lookup"><span data-stu-id="9dcde-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="9dcde-268">È inoltre importante notare che lo scorrimento verso l'alto e lo scorrimento verso il basso dipendono anche dai margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="9dcde-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="9dcde-269">Lo scorrimento verso l'alto e lo scorrimento verso il basso non influiranno sulle righe esterne ai margini di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="9dcde-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="9dcde-270">Il valore predefinito per &lt;n&gt; è 1 che facoltativamente può essere omesso.</span><span class="sxs-lookup"><span data-stu-id="9dcde-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="9dcde-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modifica del testo</span><span class="sxs-lookup"><span data-stu-id="9dcde-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="9dcde-272">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) e [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) per modificare il contenuto del buffer di testo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="9dcde-273">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-273">Sequence</span></span> | <span data-ttu-id="9dcde-274">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-274">Code</span></span> | <span data-ttu-id="9dcde-275">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-275">Description</span></span> | <span data-ttu-id="9dcde-276">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="9dcde-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="9dcde-278">ICH</span><span class="sxs-lookup"><span data-stu-id="9dcde-278">ICH</span></span> | <span data-ttu-id="9dcde-279">Inserimento carattere</span><span class="sxs-lookup"><span data-stu-id="9dcde-279">Insert Character</span></span> | <span data-ttu-id="9dcde-280">Inserisce &lt;n&gt; spazi nella posizione corrente del cursore, spostando tutto il testo esistente verso destra.</span><span class="sxs-lookup"><span data-stu-id="9dcde-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="9dcde-281">All'uscita dallo schermo, il testo a destra viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="9dcde-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="9dcde-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="9dcde-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="9dcde-283">DCH</span><span class="sxs-lookup"><span data-stu-id="9dcde-283">DCH</span></span> | <span data-ttu-id="9dcde-284">Eliminazione carattere</span><span class="sxs-lookup"><span data-stu-id="9dcde-284">Delete Character</span></span> | <span data-ttu-id="9dcde-285">Elimina &lt;n&gt; caratteri nella posizione corrente del cursore, scalando gli spazi dal bordo destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="9dcde-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="9dcde-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="9dcde-287">ECH</span><span class="sxs-lookup"><span data-stu-id="9dcde-287">ECH</span></span> | <span data-ttu-id="9dcde-288">Cancellazione carattere</span><span class="sxs-lookup"><span data-stu-id="9dcde-288">Erase Character</span></span> | <span data-ttu-id="9dcde-289">Cancella &lt;n&gt; caratteri dalla posizione corrente del cursore sovrascrivendoli con uno spazio.</span><span class="sxs-lookup"><span data-stu-id="9dcde-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="9dcde-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="9dcde-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="9dcde-291">IL</span><span class="sxs-lookup"><span data-stu-id="9dcde-291">IL</span></span> | <span data-ttu-id="9dcde-292">Inserisci riga</span><span class="sxs-lookup"><span data-stu-id="9dcde-292">Insert Line</span></span> | <span data-ttu-id="9dcde-293">Inserisce &lt;n&gt; righe nel buffer in corrispondenza della posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="9dcde-294">La riga in cui si trova il cursore e le righe sottostanti verranno spostate verso il basso.</span><span class="sxs-lookup"><span data-stu-id="9dcde-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="9dcde-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="9dcde-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="9dcde-296">DL</span><span class="sxs-lookup"><span data-stu-id="9dcde-296">DL</span></span> | <span data-ttu-id="9dcde-297">Elimina riga</span><span class="sxs-lookup"><span data-stu-id="9dcde-297">Delete Line</span></span> | <span data-ttu-id="9dcde-298">Elimina &lt;n&gt; righe dal buffer, a partire dalla riga in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="9dcde-299">Per IL e DL sono interessate solo le righe incluse nei margini di scorrimento (vedere Margini di scorrimento).</span><span class="sxs-lookup"><span data-stu-id="9dcde-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="9dcde-300">Se non è impostato alcun margine, i bordi predefiniti corrispondono al riquadro di visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="9dcde-301">Se le righe vengono spostate sotto i margini, vengono rimosse.</span><span class="sxs-lookup"><span data-stu-id="9dcde-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="9dcde-302">Quando le righe vengono eliminate, vengono inserite righe vuote in fondo ai margini. Le linee esterne al riquadro di visualizzazione non sono mai interessate.</span><span class="sxs-lookup"><span data-stu-id="9dcde-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="9dcde-303">Per ognuna delle sequenze, il valore predefinito di &lt;n&gt;, se omesso, è 0.</span><span class="sxs-lookup"><span data-stu-id="9dcde-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="9dcde-304">Per i comandi seguenti il parametro &lt;n&gt; ha 3 valori validi:</span><span class="sxs-lookup"><span data-stu-id="9dcde-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="9dcde-305">0 cancella il contenuto dalla posizione corrente del cursore (inclusa) alla fine della riga o del display</span><span class="sxs-lookup"><span data-stu-id="9dcde-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="9dcde-306">1 cancella il contenuto dall'inizio della riga o del display fino alla posizione corrente del cursore inclusa</span><span class="sxs-lookup"><span data-stu-id="9dcde-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="9dcde-307">2 cancella il contenuto di tutta la riga o di tutto il display</span><span class="sxs-lookup"><span data-stu-id="9dcde-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="9dcde-308">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-308">Sequence</span></span> | <span data-ttu-id="9dcde-309">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-309">Code</span></span> | <span data-ttu-id="9dcde-310">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-310">Description</span></span> | <span data-ttu-id="9dcde-311">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="9dcde-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="9dcde-313">ED</span><span class="sxs-lookup"><span data-stu-id="9dcde-313">ED</span></span> | <span data-ttu-id="9dcde-314">Cancellazione nel display</span><span class="sxs-lookup"><span data-stu-id="9dcde-314">Erase in Display</span></span> | <span data-ttu-id="9dcde-315">Sostituisce tutto il testo presente nel riquadro di visualizzazione o nello schermo, specificato da &lt;n&gt; con spazi</span><span class="sxs-lookup"><span data-stu-id="9dcde-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="9dcde-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="9dcde-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="9dcde-317">EL</span><span class="sxs-lookup"><span data-stu-id="9dcde-317">EL</span></span> | <span data-ttu-id="9dcde-318">Cancellazione nella riga</span><span class="sxs-lookup"><span data-stu-id="9dcde-318">Erase in Line</span></span> | <span data-ttu-id="9dcde-319">Sostituisce tutto il testo presente nella riga con il cursore specificato da &lt;n&gt; con spazi</span><span class="sxs-lookup"><span data-stu-id="9dcde-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="9dcde-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formattazione del testo</span><span class="sxs-lookup"><span data-stu-id="9dcde-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="9dcde-321">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console [**SetConsoleTextAttribute**](setconsoletextattribute.md) per regolare la formattazione di tutte le operazioni di scrittura future nel buffer di testo di output della console.</span><span class="sxs-lookup"><span data-stu-id="9dcde-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="9dcde-322">Questo comando è speciale in quanto la posizione &lt;n&gt; indicata di seguito può accettare da 0 a 16 parametri separati da punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="9dcde-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="9dcde-323">Se non è specificato alcun parametro, si considera come se fosse specificato un singolo parametro 0.</span><span class="sxs-lookup"><span data-stu-id="9dcde-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="9dcde-324">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-324">Sequence</span></span> | <span data-ttu-id="9dcde-325">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-325">Code</span></span> | <span data-ttu-id="9dcde-326">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-326">Description</span></span> | <span data-ttu-id="9dcde-327">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="9dcde-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="9dcde-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="9dcde-329">SGR</span><span class="sxs-lookup"><span data-stu-id="9dcde-329">SGR</span></span> | <span data-ttu-id="9dcde-330">Impostazione rendering grafica</span><span class="sxs-lookup"><span data-stu-id="9dcde-330">Set Graphics Rendition</span></span> | <span data-ttu-id="9dcde-331">Imposta il formato dello schermo e del testo come specificato da &lt;n&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="9dcde-332">La seguente tabella di valori può essere usata in &lt;n&gt; per rappresentare modalità di formattazione diverse.</span><span class="sxs-lookup"><span data-stu-id="9dcde-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="9dcde-333">Le modalità di formattazione vengono applicate da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="9dcde-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="9dcde-334">Se si applicano opzioni di formattazione concorrenti, l'opzione più a destra avrà la precedenza.</span><span class="sxs-lookup"><span data-stu-id="9dcde-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="9dcde-335">Per le opzioni che specificano i colori, i colori verranno usati come definito nella tabella dei colori della console, che può essere modificata usando l'API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md).</span><span class="sxs-lookup"><span data-stu-id="9dcde-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="9dcde-336">Se la tabella viene modificata in modo che la posizione "blu" visualizzi una sfumatura di rosso RGB, tutte le chiamate a **Blu primo piano** visualizzeranno il colore rosso fino a quando questa opzione non viene modificata.</span><span class="sxs-lookup"><span data-stu-id="9dcde-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="9dcde-337">Valore</span><span class="sxs-lookup"><span data-stu-id="9dcde-337">Value</span></span> | <span data-ttu-id="9dcde-338">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-338">Description</span></span> | <span data-ttu-id="9dcde-339">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="9dcde-340">0</span><span class="sxs-lookup"><span data-stu-id="9dcde-340">0</span></span> | <span data-ttu-id="9dcde-341">Predefinito</span><span class="sxs-lookup"><span data-stu-id="9dcde-341">Default</span></span> | <span data-ttu-id="9dcde-342">Ripristina lo stato predefinito di tutti gli attributi precedente alla modifica</span><span class="sxs-lookup"><span data-stu-id="9dcde-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="9dcde-343">1</span><span class="sxs-lookup"><span data-stu-id="9dcde-343">1</span></span> | <span data-ttu-id="9dcde-344">Grassetto/Brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-344">Bold/Bright</span></span> | <span data-ttu-id="9dcde-345">Applica il flag di luminosità/intensità al colore di primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="9dcde-346">4</span><span class="sxs-lookup"><span data-stu-id="9dcde-346">4</span></span> | <span data-ttu-id="9dcde-347">Sottolineato</span><span class="sxs-lookup"><span data-stu-id="9dcde-347">Underline</span></span> | <span data-ttu-id="9dcde-348">Aggiunge la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="9dcde-348">Adds underline</span></span> |
| <span data-ttu-id="9dcde-349">24</span><span class="sxs-lookup"><span data-stu-id="9dcde-349">24</span></span> | <span data-ttu-id="9dcde-350">Nessuna sottolineatura</span><span class="sxs-lookup"><span data-stu-id="9dcde-350">No underline</span></span> | <span data-ttu-id="9dcde-351">Rimuove la sottolineatura</span><span class="sxs-lookup"><span data-stu-id="9dcde-351">Removes underline</span></span> |
| <span data-ttu-id="9dcde-352">7</span><span class="sxs-lookup"><span data-stu-id="9dcde-352">7</span></span> | <span data-ttu-id="9dcde-353">Negativo</span><span class="sxs-lookup"><span data-stu-id="9dcde-353">Negative</span></span> | <span data-ttu-id="9dcde-354">Scambia i colori di primo piano e di sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="9dcde-355">27</span><span class="sxs-lookup"><span data-stu-id="9dcde-355">27</span></span> | <span data-ttu-id="9dcde-356">Positivo (non negativo)</span><span class="sxs-lookup"><span data-stu-id="9dcde-356">Positive (No negative)</span></span> | <span data-ttu-id="9dcde-357">Ripristina il valore normale di primo piano/sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="9dcde-358">30</span><span class="sxs-lookup"><span data-stu-id="9dcde-358">30</span></span> | <span data-ttu-id="9dcde-359">Nero primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-359">Foreground Black</span></span> | <span data-ttu-id="9dcde-360">Applica il colore nero non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="9dcde-361">31</span><span class="sxs-lookup"><span data-stu-id="9dcde-361">31</span></span> | <span data-ttu-id="9dcde-362">Rosso primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-362">Foreground Red</span></span> | <span data-ttu-id="9dcde-363">Applica il colore rosso non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="9dcde-364">32</span><span class="sxs-lookup"><span data-stu-id="9dcde-364">32</span></span> | <span data-ttu-id="9dcde-365">Verde primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-365">Foreground Green</span></span> | <span data-ttu-id="9dcde-366">Applica il colore verde non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="9dcde-367">33</span><span class="sxs-lookup"><span data-stu-id="9dcde-367">33</span></span> | <span data-ttu-id="9dcde-368">Giallo primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-368">Foreground Yellow</span></span> | <span data-ttu-id="9dcde-369">Applica il colore giallo non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="9dcde-370">34</span><span class="sxs-lookup"><span data-stu-id="9dcde-370">34</span></span> | <span data-ttu-id="9dcde-371">Blu primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-371">Foreground Blue</span></span> | <span data-ttu-id="9dcde-372">Applica il colore blu non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="9dcde-373">35</span><span class="sxs-lookup"><span data-stu-id="9dcde-373">35</span></span> | <span data-ttu-id="9dcde-374">Magenta primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-374">Foreground Magenta</span></span> | <span data-ttu-id="9dcde-375">Applica il color magenta non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="9dcde-376">36</span><span class="sxs-lookup"><span data-stu-id="9dcde-376">36</span></span> | <span data-ttu-id="9dcde-377">Ciano primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-377">Foreground Cyan</span></span> | <span data-ttu-id="9dcde-378">Applica il color ciano non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="9dcde-379">37</span><span class="sxs-lookup"><span data-stu-id="9dcde-379">37</span></span> | <span data-ttu-id="9dcde-380">Bianco primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-380">Foreground White</span></span> | <span data-ttu-id="9dcde-381">Applica il colore bianco non grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="9dcde-382">38</span><span class="sxs-lookup"><span data-stu-id="9dcde-382">38</span></span> | <span data-ttu-id="9dcde-383">Valore esteso primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-383">Foreground Extended</span></span> | <span data-ttu-id="9dcde-384">Applica il valore di colore esteso al primo piano (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="9dcde-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="9dcde-385">39</span><span class="sxs-lookup"><span data-stu-id="9dcde-385">39</span></span> | <span data-ttu-id="9dcde-386">Valore predefinito primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-386">Foreground Default</span></span> | <span data-ttu-id="9dcde-387">Applica solo la parte in primo piano delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="9dcde-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="9dcde-388">40</span><span class="sxs-lookup"><span data-stu-id="9dcde-388">40</span></span> | <span data-ttu-id="9dcde-389">Nero sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-389">Background Black</span></span> | <span data-ttu-id="9dcde-390">Applica il colore nero non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="9dcde-391">41</span><span class="sxs-lookup"><span data-stu-id="9dcde-391">41</span></span> | <span data-ttu-id="9dcde-392">Rosso sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-392">Background Red</span></span> | <span data-ttu-id="9dcde-393">Applica il colore rosso non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="9dcde-394">42</span><span class="sxs-lookup"><span data-stu-id="9dcde-394">42</span></span> | <span data-ttu-id="9dcde-395">Verde sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-395">Background Green</span></span> | <span data-ttu-id="9dcde-396">Applica il colore verde non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="9dcde-397">43</span><span class="sxs-lookup"><span data-stu-id="9dcde-397">43</span></span> | <span data-ttu-id="9dcde-398">Giallo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-398">Background Yellow</span></span> | <span data-ttu-id="9dcde-399">Applica il colore giallo non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="9dcde-400">44</span><span class="sxs-lookup"><span data-stu-id="9dcde-400">44</span></span> | <span data-ttu-id="9dcde-401">Blu sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-401">Background Blue</span></span> | <span data-ttu-id="9dcde-402">Applica il colore blu non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="9dcde-403">45</span><span class="sxs-lookup"><span data-stu-id="9dcde-403">45</span></span> | <span data-ttu-id="9dcde-404">Magenta sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-404">Background Magenta</span></span> | <span data-ttu-id="9dcde-405">Applica il color magenta non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="9dcde-406">46</span><span class="sxs-lookup"><span data-stu-id="9dcde-406">46</span></span> | <span data-ttu-id="9dcde-407">Ciano sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-407">Background Cyan</span></span> | <span data-ttu-id="9dcde-408">Applica il color ciano non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="9dcde-409">47</span><span class="sxs-lookup"><span data-stu-id="9dcde-409">47</span></span> | <span data-ttu-id="9dcde-410">Bianco sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-410">Background White</span></span> | <span data-ttu-id="9dcde-411">Applica il colore bianco non grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="9dcde-412">48</span><span class="sxs-lookup"><span data-stu-id="9dcde-412">48</span></span> | <span data-ttu-id="9dcde-413">Valore esteso sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-413">Background Extended</span></span> | <span data-ttu-id="9dcde-414">Applica il valore di colore esteso allo sfondo (vedere i dettagli di seguito)</span><span class="sxs-lookup"><span data-stu-id="9dcde-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="9dcde-415">49</span><span class="sxs-lookup"><span data-stu-id="9dcde-415">49</span></span> | <span data-ttu-id="9dcde-416">Valore predefinito sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-416">Background Default</span></span> | <span data-ttu-id="9dcde-417">Applica solo la parte dello sfondo delle impostazioni predefinite (vedere 0)</span><span class="sxs-lookup"><span data-stu-id="9dcde-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="9dcde-418">90</span><span class="sxs-lookup"><span data-stu-id="9dcde-418">90</span></span> | <span data-ttu-id="9dcde-419">Nero primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-419">Bright Foreground Black</span></span> | <span data-ttu-id="9dcde-420">Applica il colore nero grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="9dcde-421">91</span><span class="sxs-lookup"><span data-stu-id="9dcde-421">91</span></span> | <span data-ttu-id="9dcde-422">Rosso primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-422">Bright Foreground Red</span></span> | <span data-ttu-id="9dcde-423">Applica il colore rosso grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="9dcde-424">92</span><span class="sxs-lookup"><span data-stu-id="9dcde-424">92</span></span> | <span data-ttu-id="9dcde-425">Verde primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-425">Bright Foreground Green</span></span> | <span data-ttu-id="9dcde-426">Applica il colore verde grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="9dcde-427">93</span><span class="sxs-lookup"><span data-stu-id="9dcde-427">93</span></span> | <span data-ttu-id="9dcde-428">Giallo primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="9dcde-429">Applica il colore giallo grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="9dcde-430">94</span><span class="sxs-lookup"><span data-stu-id="9dcde-430">94</span></span> | <span data-ttu-id="9dcde-431">Blu primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-431">Bright Foreground Blue</span></span> | <span data-ttu-id="9dcde-432">Applica il colore blu grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="9dcde-433">95</span><span class="sxs-lookup"><span data-stu-id="9dcde-433">95</span></span> | <span data-ttu-id="9dcde-434">Magenta primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="9dcde-435">Applica il color magenta grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="9dcde-436">96</span><span class="sxs-lookup"><span data-stu-id="9dcde-436">96</span></span> | <span data-ttu-id="9dcde-437">Ciano primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="9dcde-438">Applica il color ciano grassetto/brillante in primo piano</span><span class="sxs-lookup"><span data-stu-id="9dcde-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="9dcde-439">97</span><span class="sxs-lookup"><span data-stu-id="9dcde-439">97</span></span> | <span data-ttu-id="9dcde-440">Bianco primo piano brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-440">Bright Foreground White</span></span> | <span data-ttu-id="9dcde-441">Applica il colore bianco grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="9dcde-442">100</span><span class="sxs-lookup"><span data-stu-id="9dcde-442">100</span></span> | <span data-ttu-id="9dcde-443">Nero sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-443">Bright Background Black</span></span> | <span data-ttu-id="9dcde-444">Applica il colore nero grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="9dcde-445">101</span><span class="sxs-lookup"><span data-stu-id="9dcde-445">101</span></span> | <span data-ttu-id="9dcde-446">Rosso sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-446">Bright Background Red</span></span> | <span data-ttu-id="9dcde-447">Applica il colore rosso grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="9dcde-448">102</span><span class="sxs-lookup"><span data-stu-id="9dcde-448">102</span></span> | <span data-ttu-id="9dcde-449">Verde sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-449">Bright Background Green</span></span> | <span data-ttu-id="9dcde-450">Applica il colore verde grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="9dcde-451">103</span><span class="sxs-lookup"><span data-stu-id="9dcde-451">103</span></span> | <span data-ttu-id="9dcde-452">Giallo sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-452">Bright Background Yellow</span></span> | <span data-ttu-id="9dcde-453">Applica il colore giallo grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="9dcde-454">104</span><span class="sxs-lookup"><span data-stu-id="9dcde-454">104</span></span> | <span data-ttu-id="9dcde-455">Blu sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-455">Bright Background Blue</span></span> | <span data-ttu-id="9dcde-456">Applica il colore blu grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="9dcde-457">105</span><span class="sxs-lookup"><span data-stu-id="9dcde-457">105</span></span> | <span data-ttu-id="9dcde-458">Magenta sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-458">Bright Background Magenta</span></span> | <span data-ttu-id="9dcde-459">Applica il color magenta grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="9dcde-460">106</span><span class="sxs-lookup"><span data-stu-id="9dcde-460">106</span></span> | <span data-ttu-id="9dcde-461">Ciano sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-461">Bright Background Cyan</span></span> | <span data-ttu-id="9dcde-462">Applica il color ciano grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="9dcde-463">107</span><span class="sxs-lookup"><span data-stu-id="9dcde-463">107</span></span> | <span data-ttu-id="9dcde-464">Bianco sfondo brillante</span><span class="sxs-lookup"><span data-stu-id="9dcde-464">Bright Background White</span></span> | <span data-ttu-id="9dcde-465">Applica il colore bianco grassetto/brillante allo sfondo</span><span class="sxs-lookup"><span data-stu-id="9dcde-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="9dcde-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colori estesi</span><span class="sxs-lookup"><span data-stu-id="9dcde-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="9dcde-467">Alcuni emulatori di terminale virtuale supportano una tavolozza di colori più estesa dei 16 colori forniti dalla console di Windows.</span><span class="sxs-lookup"><span data-stu-id="9dcde-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="9dcde-468">Per questi colori estesi, la console di Windows sceglierà il colore appropriato più vicino dalla tavola dei 16 colori esistente per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="9dcde-469">Diversamente dai valori SGR tipici sopraindicati, i valori estesi utilizzano parametri aggiuntivi dopo l'indicatore iniziale, in base alle informazioni riportate nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="9dcde-470">Sottosequenza SGR</span><span class="sxs-lookup"><span data-stu-id="9dcde-470">SGR Subsequence</span></span> | <span data-ttu-id="9dcde-471">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="9dcde-473">Imposta il colore di primo piano sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="9dcde-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="9dcde-475">Imposta il colore di sfondo sul valore RGB specificato nei parametri &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="9dcde-476">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="9dcde-477">Imposta il colore di primo piano sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="9dcde-478">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="9dcde-479">Imposta il colore di sfondo sull'indice &lt;s&gt; nella tabella da 88 o 256 colori\*</span><span class="sxs-lookup"><span data-stu-id="9dcde-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="9dcde-480">\*Le tavolozze da 88 e 256 colori gestite internamente per il confronto sono basate sull'emulatore di terminale xterm.</span><span class="sxs-lookup"><span data-stu-id="9dcde-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="9dcde-481">Non è possibile modificare le tabelle di confronto o di arrotondamento in questa fase.</span><span class="sxs-lookup"><span data-stu-id="9dcde-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="9dcde-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colori dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="9dcde-483">Il comando seguente consente all'applicazione di impostare i valori della tavolozza dei colori dello schermo su qualsiasi valore RGB.</span><span class="sxs-lookup"><span data-stu-id="9dcde-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="9dcde-484">I valori RGB devono essere valori esadecimali compresi tra `0` e `ff` e separati dal carattere barra (ad esempio, `rgb:1/24/86`).</span><span class="sxs-lookup"><span data-stu-id="9dcde-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="9dcde-485">Si noti che questa sequenza è di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza inizia con "\\x1b\]", non con "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="9dcde-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="9dcde-486">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-486">Sequence</span></span> | <span data-ttu-id="9dcde-487">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-487">Description</span></span> | <span data-ttu-id="9dcde-488">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="9dcde-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="9dcde-490">Modifica colori schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-490">Modify Screen Colors</span></span> | <span data-ttu-id="9dcde-491">Imposta l'indice &lt;i&gt; della tavolozza dei colori dello schermo sui valori RGB specificati in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="9dcde-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Modifiche della modalità</span><span class="sxs-lookup"><span data-stu-id="9dcde-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="9dcde-493">Si tratta di sequenze che controllano le modalità di input.</span><span class="sxs-lookup"><span data-stu-id="9dcde-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="9dcde-494">Esistono due diversi set di modalità di input, ovvero la modalità tasti cursore e la modalità tasti del tastierino.</span><span class="sxs-lookup"><span data-stu-id="9dcde-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="9dcde-495">La modalità tasti cursore controlla le sequenze generate dai tasti di direzione, nonché da Home e Fine, mentre la modalità tasti del tastierino controlla le sequenze generate principalmente dai tasti sul tastierino numerico, nonché dai tasti funzione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="9dcde-496">Ognuna di queste modalità è una semplice impostazione booleana. La modalità tasti cursore è impostata su normale (impostazione predefinita) o applicazione e la modalità tasti del tastierino è impostata su numerica (impostazione predefinita) o applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="9dcde-497">Per le sequenze generate in queste modalità, vedere le sezioni Tasti cursore e Tastierino numerico.</span><span class="sxs-lookup"><span data-stu-id="9dcde-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="9dcde-498">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-498">Sequence</span></span> | <span data-ttu-id="9dcde-499">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-499">Code</span></span> | <span data-ttu-id="9dcde-500">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-500">Description</span></span> | <span data-ttu-id="9dcde-501">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="9dcde-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="9dcde-502">ESC =</span></span> | <span data-ttu-id="9dcde-503">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="9dcde-503">DECKPAM</span></span> | <span data-ttu-id="9dcde-504">Abilitazione modalità applicazione tastierino</span><span class="sxs-lookup"><span data-stu-id="9dcde-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="9dcde-505">I tasti del tastierino generano le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="9dcde-506">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="9dcde-506">ESC &gt;</span></span> | <span data-ttu-id="9dcde-507">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="9dcde-507">DECKPNM</span></span> | <span data-ttu-id="9dcde-508">Abilitazione modalità numerica tastierino</span><span class="sxs-lookup"><span data-stu-id="9dcde-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="9dcde-509">I tasti del tastierino genereranno le relative sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="9dcde-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="9dcde-510">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-510">ESC \[ ?</span></span> <span data-ttu-id="9dcde-511">1 ora</span><span class="sxs-lookup"><span data-stu-id="9dcde-511">1 h</span></span> | <span data-ttu-id="9dcde-512">DECCKM</span><span class="sxs-lookup"><span data-stu-id="9dcde-512">DECCKM</span></span> | <span data-ttu-id="9dcde-513">Abilitazione modalità applicazione tasti cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="9dcde-514">I tasti del tastierino generano le relative sequenze in modalità applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="9dcde-515">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-515">ESC \[ ?</span></span> <span data-ttu-id="9dcde-516">1 l</span><span class="sxs-lookup"><span data-stu-id="9dcde-516">1 l</span></span> | <span data-ttu-id="9dcde-517">DECCKM</span><span class="sxs-lookup"><span data-stu-id="9dcde-517">DECCKM</span></span> | <span data-ttu-id="9dcde-518">Disabilitazione modalità applicazione tasti cursore (usare la modalità normale)</span><span class="sxs-lookup"><span data-stu-id="9dcde-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="9dcde-519">I tasti del tastierino genereranno le relative sequenze in modalità numerica.</span><span class="sxs-lookup"><span data-stu-id="9dcde-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="9dcde-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Stato delle query</span><span class="sxs-lookup"><span data-stu-id="9dcde-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="9dcde-521">Tutti i comandi inclusi in questa sezione sono generalmente equivalenti alla chiamata delle API della console Get\* per recuperare informazioni sullo stato corrente del buffer della console.</span><span class="sxs-lookup"><span data-stu-id="9dcde-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="9dcde-522">Queste query generano le risposte nel flusso di input della console subito dopo essere state riconosciute nel flusso di output durante l'impostazione di ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING.</span><span class="sxs-lookup"><span data-stu-id="9dcde-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="9dcde-523">Il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT non si applica ai comandi di query perché si presuppone che un'applicazione che esegue la query voglia sempre ricevere la risposta.</span><span class="sxs-lookup"><span data-stu-id="9dcde-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="9dcde-524">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-524">Sequence</span></span> | <span data-ttu-id="9dcde-525">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-525">Code</span></span> | <span data-ttu-id="9dcde-526">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-526">Description</span></span> | <span data-ttu-id="9dcde-527">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="9dcde-528">ESC \[ 6 n</span></span> | <span data-ttu-id="9dcde-529">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="9dcde-529">DECXCPR</span></span> | <span data-ttu-id="9dcde-530">Segnalazione posizione cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-530">Report Cursor Position</span></span> | <span data-ttu-id="9dcde-531">Genera la posizione del cursore come: ESC \[ &lt;r&gt; ; &lt;c&gt; R dove &lt;r&gt; = riga del cursore e &lt;c&gt; = colonna del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="9dcde-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="9dcde-532">ESC \[ 0 c</span></span> | <span data-ttu-id="9dcde-533">DA</span><span class="sxs-lookup"><span data-stu-id="9dcde-533">DA</span></span> | <span data-ttu-id="9dcde-534">Attributi dispositivo</span><span class="sxs-lookup"><span data-stu-id="9dcde-534">Device Attributes</span></span> | <span data-ttu-id="9dcde-535">Segnala l'identità del terminale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-535">Report the terminal identity.</span></span> <span data-ttu-id="9dcde-536">Genera "\\x1b\[?1;0c", per indicare "VT101 senza opzioni".</span><span class="sxs-lookup"><span data-stu-id="9dcde-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="9dcde-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabulazioni</span><span class="sxs-lookup"><span data-stu-id="9dcde-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="9dcde-538">Benché la console di Windows preveda tradizionalmente che la larghezza delle tabulazioni sia di otto caratteri, le applicazioni \*nix che utilizzano determinate sequenze possono modificare il punto in cui si trovano le tabulazioni nelle finestre della console per ottimizzare lo spostamento del cursore in base all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="9dcde-539">Le sequenze seguenti consentono a un'applicazione di impostare le posizioni delle tabulazioni nella finestra della console, rimuoverle e spostarsi da una posizione all'altra.</span><span class="sxs-lookup"><span data-stu-id="9dcde-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="9dcde-540">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-540">Sequence</span></span> | <span data-ttu-id="9dcde-541">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-541">Code</span></span> | <span data-ttu-id="9dcde-542">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-542">Description</span></span> | <span data-ttu-id="9dcde-543">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9dcde-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="9dcde-544">ESC H</span></span> | <span data-ttu-id="9dcde-545">HTS</span><span class="sxs-lookup"><span data-stu-id="9dcde-545">HTS</span></span> | <span data-ttu-id="9dcde-546">Tabulazione orizzontale impostata</span><span class="sxs-lookup"><span data-stu-id="9dcde-546">Horizontal Tab Set</span></span> | <span data-ttu-id="9dcde-547">Imposta una tabulazione nella colonna corrente in cui si trova il cursore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="9dcde-548">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="9dcde-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="9dcde-549">CHT</span><span class="sxs-lookup"><span data-stu-id="9dcde-549">CHT</span></span> | <span data-ttu-id="9dcde-550">Tabulazione orizzontale (in avanti) del cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="9dcde-551">Sposta il cursore nella colonna successiva (stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="9dcde-552">Se non sono presenti altre tabulazioni, il cursore si sposta nell'ultima colonna della riga.</span><span class="sxs-lookup"><span data-stu-id="9dcde-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="9dcde-553">Se il cursore si trova nell'ultima colonna, passa alla prima colonna della riga successiva.</span><span class="sxs-lookup"><span data-stu-id="9dcde-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="9dcde-554">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="9dcde-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="9dcde-555">CBT</span><span class="sxs-lookup"><span data-stu-id="9dcde-555">CBT</span></span> | <span data-ttu-id="9dcde-556">Tabulazione cursore indietro</span><span class="sxs-lookup"><span data-stu-id="9dcde-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="9dcde-557">Sposta il cursore nella colonna precedente (stessa riga) con una tabulazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="9dcde-558">Se non sono presenti altre tabulazioni, sposta il cursore nella prima colonna.</span><span class="sxs-lookup"><span data-stu-id="9dcde-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="9dcde-559">Se il cursore si trova nella prima colonna, non viene spostato.</span><span class="sxs-lookup"><span data-stu-id="9dcde-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="9dcde-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="9dcde-560">ESC \[ 0 g</span></span> | <span data-ttu-id="9dcde-561">TBC</span><span class="sxs-lookup"><span data-stu-id="9dcde-561">TBC</span></span> | <span data-ttu-id="9dcde-562">Cancellazione tabulazione (colonna corrente)</span><span class="sxs-lookup"><span data-stu-id="9dcde-562">Tab Clear (current column)</span></span> | <span data-ttu-id="9dcde-563">Cancella la tabulazione, se presente, nella colonna corrente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="9dcde-564">In caso contrario, non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="9dcde-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="9dcde-565">ESC \[ 3 g</span></span> | <span data-ttu-id="9dcde-566">TBC</span><span class="sxs-lookup"><span data-stu-id="9dcde-566">TBC</span></span> | <span data-ttu-id="9dcde-567">Cancellazione tabulazione (tutte le colonne)</span><span class="sxs-lookup"><span data-stu-id="9dcde-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="9dcde-568">Cancella tutte le tabulazioni attualmente impostate.</span><span class="sxs-lookup"><span data-stu-id="9dcde-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="9dcde-569">Per CHT e CBT, &lt;n&gt; è un parametro facoltativo (valore predefinito = 1) che indica il numero di volte in cui spostare il cursore nella direzione specificata.</span><span class="sxs-lookup"><span data-stu-id="9dcde-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="9dcde-570">Se non sono presenti tabulazioni impostate tramite HTS, CHT e CBT, la prima e l'ultima colonna della finestra verranno considerate come le uniche due tabulazioni.</span><span class="sxs-lookup"><span data-stu-id="9dcde-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="9dcde-571">Se si usa HTS per impostare una tabulazione, la console passerà alla successiva tabulazione nell'output di un carattere di tabulazione (0x09,'\\t'), come avviene quando si usa CHT.</span><span class="sxs-lookup"><span data-stu-id="9dcde-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="9dcde-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designare il set di caratteri</span><span class="sxs-lookup"><span data-stu-id="9dcde-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="9dcde-573">Le sequenze seguenti consentono a un programma di modificare il mapping del set di caratteri attivo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="9dcde-574">In questo modo un programma può generare caratteri ASCII a 7 bit, ma visualizzarli come altri glifi nello schermo del terminale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="9dcde-575">Attualmente gli unici due set di caratteri supportati sono ASCII (impostazione predefinita) e il set di caratteri grafici speciali DEC.</span><span class="sxs-lookup"><span data-stu-id="9dcde-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="9dcde-576">Per un elenco di tutti i caratteri rappresentati dal set di caratteri grafici speciali DEC, visitare il sito Web all'indirizzo <http://vt100.net/docs/vt220-rm/table2-4.html>.</span><span class="sxs-lookup"><span data-stu-id="9dcde-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="9dcde-577">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-577">Sequence</span></span> | <span data-ttu-id="9dcde-578">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-578">Description</span></span> | <span data-ttu-id="9dcde-579">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="9dcde-580">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="9dcde-580">ESC ( 0</span></span> | <span data-ttu-id="9dcde-581">Designazione set di caratteri DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="9dcde-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="9dcde-582">Abilita la modalità DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="9dcde-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="9dcde-583">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="9dcde-583">ESC ( B</span></span> | <span data-ttu-id="9dcde-584">Designazione set di caratteri ASCII Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="9dcde-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="9dcde-585">Abilita la modalità ASCII (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="9dcde-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="9dcde-586">In particolare, la modalità DEC Line Drawing viene usata per disegnare i bordi nelle applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="9dcde-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="9dcde-587">La tabella seguente illustra il mapping tra caratteri ASCII e caratteri DEC Line Drawing.</span><span class="sxs-lookup"><span data-stu-id="9dcde-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="9dcde-588">Hex</span><span class="sxs-lookup"><span data-stu-id="9dcde-588">Hex</span></span> | <span data-ttu-id="9dcde-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="9dcde-589">ASCII</span></span> | <span data-ttu-id="9dcde-590">DEC Line Drawing</span><span class="sxs-lookup"><span data-stu-id="9dcde-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="9dcde-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="9dcde-591">0x6a</span></span> | <span data-ttu-id="9dcde-592">j</span><span class="sxs-lookup"><span data-stu-id="9dcde-592">j</span></span> | <span data-ttu-id="9dcde-593">┘</span><span class="sxs-lookup"><span data-stu-id="9dcde-593">┘</span></span> |
| <span data-ttu-id="9dcde-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="9dcde-594">0x6b</span></span> | <span data-ttu-id="9dcde-595">k</span><span class="sxs-lookup"><span data-stu-id="9dcde-595">k</span></span> | <span data-ttu-id="9dcde-596">┐</span><span class="sxs-lookup"><span data-stu-id="9dcde-596">┐</span></span> |
| <span data-ttu-id="9dcde-597">0x6c</span><span class="sxs-lookup"><span data-stu-id="9dcde-597">0x6c</span></span> | <span data-ttu-id="9dcde-598">l</span><span class="sxs-lookup"><span data-stu-id="9dcde-598">l</span></span> | <span data-ttu-id="9dcde-599">┌</span><span class="sxs-lookup"><span data-stu-id="9dcde-599">┌</span></span> |
| <span data-ttu-id="9dcde-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="9dcde-600">0x6d</span></span> | <span data-ttu-id="9dcde-601">m</span><span class="sxs-lookup"><span data-stu-id="9dcde-601">m</span></span> | <span data-ttu-id="9dcde-602">└</span><span class="sxs-lookup"><span data-stu-id="9dcde-602">└</span></span> |
| <span data-ttu-id="9dcde-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="9dcde-603">0x6e</span></span> | <span data-ttu-id="9dcde-604">n</span><span class="sxs-lookup"><span data-stu-id="9dcde-604">n</span></span> | <span data-ttu-id="9dcde-605">┼</span><span class="sxs-lookup"><span data-stu-id="9dcde-605">┼</span></span> |
| <span data-ttu-id="9dcde-606">0x71</span><span class="sxs-lookup"><span data-stu-id="9dcde-606">0x71</span></span> | <span data-ttu-id="9dcde-607">q</span><span class="sxs-lookup"><span data-stu-id="9dcde-607">q</span></span> | <span data-ttu-id="9dcde-608">─</span><span class="sxs-lookup"><span data-stu-id="9dcde-608">─</span></span> |
| <span data-ttu-id="9dcde-609">0x74</span><span class="sxs-lookup"><span data-stu-id="9dcde-609">0x74</span></span> | <span data-ttu-id="9dcde-610">u</span><span class="sxs-lookup"><span data-stu-id="9dcde-610">t</span></span> | <span data-ttu-id="9dcde-611">├</span><span class="sxs-lookup"><span data-stu-id="9dcde-611">├</span></span> |
| <span data-ttu-id="9dcde-612">0x75</span><span class="sxs-lookup"><span data-stu-id="9dcde-612">0x75</span></span> | <span data-ttu-id="9dcde-613">u</span><span class="sxs-lookup"><span data-stu-id="9dcde-613">u</span></span> | <span data-ttu-id="9dcde-614">┤</span><span class="sxs-lookup"><span data-stu-id="9dcde-614">┤</span></span> |
| <span data-ttu-id="9dcde-615">0x76</span><span class="sxs-lookup"><span data-stu-id="9dcde-615">0x76</span></span> | <span data-ttu-id="9dcde-616">v</span><span class="sxs-lookup"><span data-stu-id="9dcde-616">v</span></span> | <span data-ttu-id="9dcde-617">┴</span><span class="sxs-lookup"><span data-stu-id="9dcde-617">┴</span></span> |
| <span data-ttu-id="9dcde-618">0x77</span><span class="sxs-lookup"><span data-stu-id="9dcde-618">0x77</span></span> | <span data-ttu-id="9dcde-619">w</span><span class="sxs-lookup"><span data-stu-id="9dcde-619">w</span></span> | <span data-ttu-id="9dcde-620">┬</span><span class="sxs-lookup"><span data-stu-id="9dcde-620">┬</span></span> |
| <span data-ttu-id="9dcde-621">0x78</span><span class="sxs-lookup"><span data-stu-id="9dcde-621">0x78</span></span> | <span data-ttu-id="9dcde-622">x</span><span class="sxs-lookup"><span data-stu-id="9dcde-622">x</span></span> | <span data-ttu-id="9dcde-623">│</span><span class="sxs-lookup"><span data-stu-id="9dcde-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="9dcde-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Margini di scorrimento</span><span class="sxs-lookup"><span data-stu-id="9dcde-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="9dcde-625">Le sequenze seguenti consentono a un programma di configurare l'"area di scorrimento" dello schermo interessata dalle operazioni di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="9dcde-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="9dcde-626">Si tratta di un subset di righe che vengono regolate quando altrimenti lo schermo scorrerebbe, ad esempio per una sequenza '\\n' o RI.</span><span class="sxs-lookup"><span data-stu-id="9dcde-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="9dcde-627">Questi margini influiscono anche sulle righe modificate da Inserimento riga (IL) ed Eliminazione riga (DL), Scorrimento verso l'alto (SU) e Scorrimento verso il basso (SD).</span><span class="sxs-lookup"><span data-stu-id="9dcde-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="9dcde-628">I margini di scorrimento possono essere utili soprattutto per fare in modo che una parte dello schermo non scorra quando il resto dello schermo viene riempito, ad esempio con una barra del titolo nella parte superiore o una barra di stato nella parte inferiore dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="9dcde-629">Per DECSTBM sono disponibili due parametri facoltativi, &lt;t&gt; e &lt;b&gt;, usati per specificare le righe che rappresentano la riga superiore e quella inferiore dell'area di scorrimento incluse.</span><span class="sxs-lookup"><span data-stu-id="9dcde-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="9dcde-630">Se i parametri vengono omessi, &lt;t&gt; viene impostato automaticamente su 1 e &lt;b&gt; sull'altezza del riquadro di visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="9dcde-631">I margini di scorrimento vanno considerati per buffer. È quindi importante che il buffer alternativo e il buffer principale mantengano impostazioni separate dei margini di scorrimento (di conseguenza, un'applicazione a schermo intero nel buffer alternativo non comprometterà i margini del buffer principale).</span><span class="sxs-lookup"><span data-stu-id="9dcde-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="9dcde-632">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-632">Sequence</span></span> | <span data-ttu-id="9dcde-633">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-633">Code</span></span> | <span data-ttu-id="9dcde-634">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-634">Description</span></span> | <span data-ttu-id="9dcde-635">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="9dcde-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="9dcde-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="9dcde-637">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="9dcde-637">DECSTBM</span></span> | <span data-ttu-id="9dcde-638">Impostazione area di scorrimento</span><span class="sxs-lookup"><span data-stu-id="9dcde-638">Set Scrolling Region</span></span> | <span data-ttu-id="9dcde-639">Imposta i margini di scorrimento VT del riquadro di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="9dcde-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Titolo della finestra</span><span class="sxs-lookup"><span data-stu-id="9dcde-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="9dcde-641">I comandi seguenti consentono all'applicazione di impostare il titolo della finestra della console sul parametro &lt;stringa&gt; specificato.</span><span class="sxs-lookup"><span data-stu-id="9dcde-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="9dcde-642">Per essere accettata, la stringa deve contenere meno di 255 caratteri.</span><span class="sxs-lookup"><span data-stu-id="9dcde-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="9dcde-643">L'operazione è equivalente alla chiamata di SetConsoleTitle con la stringa specificata.</span><span class="sxs-lookup"><span data-stu-id="9dcde-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="9dcde-644">Si noti che queste sequenze sono di tipo OSC ("comando sistema operativo"), non CSI come molte delle altre sequenze elencate, e di conseguenza iniziano con "\\x1b\]", non con "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="9dcde-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="9dcde-645">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-645">Sequence</span></span> | <span data-ttu-id="9dcde-646">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-646">Description</span></span> | <span data-ttu-id="9dcde-647">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="9dcde-648">ESC \] 0 ; &lt;stringa&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="9dcde-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="9dcde-649">Impostazione icona e titolo finestra</span><span class="sxs-lookup"><span data-stu-id="9dcde-649">Set Icon and Window Title</span></span> | <span data-ttu-id="9dcde-650">Imposta il titolo della finestra della console su &lt;stringa&gt;.</span><span class="sxs-lookup"><span data-stu-id="9dcde-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="9dcde-651">ESC \] 2 ; &lt;stringa&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="9dcde-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="9dcde-652">Impostazione titolo finestra</span><span class="sxs-lookup"><span data-stu-id="9dcde-652">Set Window Title</span></span> | <span data-ttu-id="9dcde-653">Imposta il titolo della finestra della console su &lt;stringa&gt;.</span><span class="sxs-lookup"><span data-stu-id="9dcde-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="9dcde-654">Il carattere finale in queste sequenze è il carattere "Bell", '\\x07'</span><span class="sxs-lookup"><span data-stu-id="9dcde-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="9dcde-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Buffer alternativo dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="9dcde-656">Le applicazioni di tipo \*nix utilizzano spesso un buffer alternativo dello schermo, in modo da poter modificare l'intero contenuto del buffer senza influire sull'applicazione che le ha avviate.</span><span class="sxs-lookup"><span data-stu-id="9dcde-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="9dcde-657">Il buffer alternativo è esattamente delle dimensioni della finestra, senza area di scrollback.</span><span class="sxs-lookup"><span data-stu-id="9dcde-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="9dcde-658">Per un esempio di questo comportamento, si prenda in considerazione quando vim viene avviato da bash.</span><span class="sxs-lookup"><span data-stu-id="9dcde-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="9dcde-659">Vim usa l'intero schermo per modificare il file e quindi, tornando a bash, lascia invariato il buffer originale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="9dcde-660">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-660">Sequence</span></span> | <span data-ttu-id="9dcde-661">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-661">Description</span></span> | <span data-ttu-id="9dcde-662">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="9dcde-663">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-663">ESC \[ ?</span></span> <span data-ttu-id="9dcde-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="9dcde-664">1 0 4 9 h</span></span> | <span data-ttu-id="9dcde-665">Uso buffer alternativo dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="9dcde-666">Passa a un nuovo buffer alternativo dello schermo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="9dcde-667">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-667">ESC \[ ?</span></span> <span data-ttu-id="9dcde-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="9dcde-668">1 0 4 9 l</span></span> | <span data-ttu-id="9dcde-669">Uso buffer principale dello schermo</span><span class="sxs-lookup"><span data-stu-id="9dcde-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="9dcde-670">Passa al buffer principale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="9dcde-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Larghezza della finestra</span><span class="sxs-lookup"><span data-stu-id="9dcde-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="9dcde-672">Le sequenze seguenti possono essere usate per controllare la larghezza della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="9dcde-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="9dcde-673">Sono approssimativamente equivalenti alla chiamata dell'API della console SetConsoleScreenBufferInfoEx per impostare la larghezza della finestra.</span><span class="sxs-lookup"><span data-stu-id="9dcde-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="9dcde-674">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-674">Sequence</span></span> | <span data-ttu-id="9dcde-675">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-675">Code</span></span> | <span data-ttu-id="9dcde-676">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-676">Description</span></span> | <span data-ttu-id="9dcde-677">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="9dcde-678">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-678">ESC \[ ?</span></span> <span data-ttu-id="9dcde-679">3 h</span><span class="sxs-lookup"><span data-stu-id="9dcde-679">3 h</span></span> | <span data-ttu-id="9dcde-680">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="9dcde-680">DECCOLM</span></span> | <span data-ttu-id="9dcde-681">Impostazione numero di colonne su 132</span><span class="sxs-lookup"><span data-stu-id="9dcde-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="9dcde-682">Imposta la larghezza della console su una larghezza pari a 132 colonne.</span><span class="sxs-lookup"><span data-stu-id="9dcde-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="9dcde-683">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="9dcde-683">ESC \[ ?</span></span> <span data-ttu-id="9dcde-684">3 l</span><span class="sxs-lookup"><span data-stu-id="9dcde-684">3 l</span></span> | <span data-ttu-id="9dcde-685">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="9dcde-685">DECCOLM</span></span> | <span data-ttu-id="9dcde-686">Impostazione numero di colonne su 80</span><span class="sxs-lookup"><span data-stu-id="9dcde-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="9dcde-687">Imposta la larghezza della console su una larghezza pari a 80 colonne.</span><span class="sxs-lookup"><span data-stu-id="9dcde-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="9dcde-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft reset</span><span class="sxs-lookup"><span data-stu-id="9dcde-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="9dcde-689">La sequenza seguente può essere usata per reimpostare i valori predefiniti di determinate proprietà. Le proprietà seguenti vengono reimpostate sui valori predefiniti indicati di seguito (sono elencate anche le sequenze che controllano tali proprietà):</span><span class="sxs-lookup"><span data-stu-id="9dcde-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="9dcde-690">Visibilità cursore: visibile (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="9dcde-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="9dcde-691">Tastierino numerico: modalità numerica (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="9dcde-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="9dcde-692">Modalità tasti cursore: modalità normale (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="9dcde-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="9dcde-693">Margini superiore e inferiore: superiore = 1, inferiore = altezza console (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="9dcde-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="9dcde-694">Set di caratteri: ASCII Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="9dcde-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="9dcde-695">Rendering grafica: predefinito/off (SGR)</span><span class="sxs-lookup"><span data-stu-id="9dcde-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="9dcde-696">Salvataggio stato cursore: posizione Home (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="9dcde-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="9dcde-697">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-697">Sequence</span></span> | <span data-ttu-id="9dcde-698">Codice</span><span class="sxs-lookup"><span data-stu-id="9dcde-698">Code</span></span> | <span data-ttu-id="9dcde-699">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9dcde-699">Description</span></span> | <span data-ttu-id="9dcde-700">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9dcde-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="9dcde-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="9dcde-701">ESC \[ !</span></span> <span data-ttu-id="9dcde-702">p</span><span class="sxs-lookup"><span data-stu-id="9dcde-702">p</span></span> | <span data-ttu-id="9dcde-703">DECSTR</span><span class="sxs-lookup"><span data-stu-id="9dcde-703">DECSTR</span></span> | <span data-ttu-id="9dcde-704">Soft reset</span><span class="sxs-lookup"><span data-stu-id="9dcde-704">Soft Reset</span></span> | <span data-ttu-id="9dcde-705">Ripristina i valori predefiniti di determinate impostazioni del terminale.</span><span class="sxs-lookup"><span data-stu-id="9dcde-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="9dcde-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Sequenze di input</span><span class="sxs-lookup"><span data-stu-id="9dcde-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="9dcde-707">Le sequenze di terminale seguenti vengono generate dall'host della console nel flusso di input se il flag ENABLE\_VIRTUAL\_TERMINAL\_INPUT viene impostato sull'handle del buffer di input usando il flag SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="9dcde-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="9dcde-708">Sono disponibili due modalità interne che controllano le sequenze generate per i tasti di input specificati: la modalità tasti cursore e la modalità tasti del tastierino.</span><span class="sxs-lookup"><span data-stu-id="9dcde-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="9dcde-709">Queste modalità sono descritte nella sezione Modifiche della modalità.</span><span class="sxs-lookup"><span data-stu-id="9dcde-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="9dcde-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Tasti cursore</span><span class="sxs-lookup"><span data-stu-id="9dcde-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="9dcde-711">Chiave</span><span class="sxs-lookup"><span data-stu-id="9dcde-711">Key</span></span> | <span data-ttu-id="9dcde-712">Modalità normale</span><span class="sxs-lookup"><span data-stu-id="9dcde-712">Normal Mode</span></span> | <span data-ttu-id="9dcde-713">Modalità applicazione</span><span class="sxs-lookup"><span data-stu-id="9dcde-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="9dcde-714">Freccia SU</span><span class="sxs-lookup"><span data-stu-id="9dcde-714">Up Arrow</span></span> | <span data-ttu-id="9dcde-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="9dcde-715">ESC \[ A</span></span> | <span data-ttu-id="9dcde-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="9dcde-716">ESC O A</span></span> |
| <span data-ttu-id="9dcde-717">Freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="9dcde-717">Down Arrow</span></span> | <span data-ttu-id="9dcde-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="9dcde-718">ESC \[ B</span></span> | <span data-ttu-id="9dcde-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="9dcde-719">ESC O B</span></span> |
| <span data-ttu-id="9dcde-720">Freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-720">Right Arrow</span></span> | <span data-ttu-id="9dcde-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="9dcde-721">ESC \[ C</span></span> | <span data-ttu-id="9dcde-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="9dcde-722">ESC O C</span></span> |
| <span data-ttu-id="9dcde-723">Freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-723">Left Arrow</span></span> | <span data-ttu-id="9dcde-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="9dcde-724">ESC \[ D</span></span> | <span data-ttu-id="9dcde-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="9dcde-725">ESC O D</span></span> |
| <span data-ttu-id="9dcde-726">Home</span><span class="sxs-lookup"><span data-stu-id="9dcde-726">Home</span></span> | <span data-ttu-id="9dcde-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="9dcde-727">ESC \[ H</span></span> | <span data-ttu-id="9dcde-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="9dcde-728">ESC O H</span></span> |
| <span data-ttu-id="9dcde-729">Fine</span><span class="sxs-lookup"><span data-stu-id="9dcde-729">End</span></span> | <span data-ttu-id="9dcde-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="9dcde-730">ESC \[ F</span></span> | <span data-ttu-id="9dcde-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="9dcde-731">ESC O F</span></span> |



<span data-ttu-id="9dcde-732">Inoltre, se si preme CTRL con uno qualsiasi di questi tasti, vengono generate le sequenze seguenti, indipendentemente dalla modalità tasti cursore:</span><span class="sxs-lookup"><span data-stu-id="9dcde-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="9dcde-733">Chiave</span><span class="sxs-lookup"><span data-stu-id="9dcde-733">Key</span></span> | <span data-ttu-id="9dcde-734">Qualsiasi modalità</span><span class="sxs-lookup"><span data-stu-id="9dcde-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="9dcde-735">CTRL + freccia SU</span><span class="sxs-lookup"><span data-stu-id="9dcde-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="9dcde-736">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="9dcde-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="9dcde-737">CTRL + freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="9dcde-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="9dcde-738">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="9dcde-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="9dcde-739">CTRL + freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="9dcde-740">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="9dcde-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="9dcde-741">CTRL + freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="9dcde-742">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="9dcde-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="9dcde-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Tastierino numerico e tasti funzione</span><span class="sxs-lookup"><span data-stu-id="9dcde-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="9dcde-744">Chiave</span><span class="sxs-lookup"><span data-stu-id="9dcde-744">Key</span></span> | <span data-ttu-id="9dcde-745">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="9dcde-746">Backspace</span><span class="sxs-lookup"><span data-stu-id="9dcde-746">Backspace</span></span> | <span data-ttu-id="9dcde-747">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="9dcde-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="9dcde-748">Sospendi</span><span class="sxs-lookup"><span data-stu-id="9dcde-748">Pause</span></span> | <span data-ttu-id="9dcde-749">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="9dcde-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="9dcde-750">Carattere speciale di escape</span><span class="sxs-lookup"><span data-stu-id="9dcde-750">Escape</span></span> | <span data-ttu-id="9dcde-751">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="9dcde-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="9dcde-752">Insert</span><span class="sxs-lookup"><span data-stu-id="9dcde-752">Insert</span></span> | <span data-ttu-id="9dcde-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="9dcde-754">Elimina</span><span class="sxs-lookup"><span data-stu-id="9dcde-754">Delete</span></span> | <span data-ttu-id="9dcde-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="9dcde-756">PGSU</span><span class="sxs-lookup"><span data-stu-id="9dcde-756">Page Up</span></span> | <span data-ttu-id="9dcde-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="9dcde-758">PGGIÙ</span><span class="sxs-lookup"><span data-stu-id="9dcde-758">Page Down</span></span> | <span data-ttu-id="9dcde-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="9dcde-760">F1</span><span class="sxs-lookup"><span data-stu-id="9dcde-760">F1</span></span> | <span data-ttu-id="9dcde-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="9dcde-761">ESC O P</span></span> |
| <span data-ttu-id="9dcde-762">F2</span><span class="sxs-lookup"><span data-stu-id="9dcde-762">F2</span></span> | <span data-ttu-id="9dcde-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="9dcde-763">ESC O Q</span></span> |
| <span data-ttu-id="9dcde-764">F3</span><span class="sxs-lookup"><span data-stu-id="9dcde-764">F3</span></span> | <span data-ttu-id="9dcde-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="9dcde-765">ESC O R</span></span> |
| <span data-ttu-id="9dcde-766">F4</span><span class="sxs-lookup"><span data-stu-id="9dcde-766">F4</span></span> | <span data-ttu-id="9dcde-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="9dcde-767">ESC O S</span></span> |
| <span data-ttu-id="9dcde-768">F5</span><span class="sxs-lookup"><span data-stu-id="9dcde-768">F5</span></span> | <span data-ttu-id="9dcde-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="9dcde-770">F6</span><span class="sxs-lookup"><span data-stu-id="9dcde-770">F6</span></span> | <span data-ttu-id="9dcde-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="9dcde-772">F7</span><span class="sxs-lookup"><span data-stu-id="9dcde-772">F7</span></span> | <span data-ttu-id="9dcde-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="9dcde-774">F8</span><span class="sxs-lookup"><span data-stu-id="9dcde-774">F8</span></span> | <span data-ttu-id="9dcde-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="9dcde-776">F9</span><span class="sxs-lookup"><span data-stu-id="9dcde-776">F9</span></span> | <span data-ttu-id="9dcde-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="9dcde-778">F10</span><span class="sxs-lookup"><span data-stu-id="9dcde-778">F10</span></span> | <span data-ttu-id="9dcde-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="9dcde-780">F11</span><span class="sxs-lookup"><span data-stu-id="9dcde-780">F11</span></span> | <span data-ttu-id="9dcde-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="9dcde-782">F12</span><span class="sxs-lookup"><span data-stu-id="9dcde-782">F12</span></span> | <span data-ttu-id="9dcde-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="9dcde-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="9dcde-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificatori</span><span class="sxs-lookup"><span data-stu-id="9dcde-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="9dcde-785">Il tasto ALT viene trattato anteponendo alla sequenza un carattere di escape: ESC &lt;c&gt; dove &lt;c&gt; è il carattere passato dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="9dcde-786">La combinazione di tasti ALT + CTRL viene gestita allo stesso modo, tranne per il fatto che il sistema operativo avrà preliminarmente spostato il tasto &lt;c&gt; sul carattere di controllo appropriato che verrà inoltrato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="9dcde-787">Il tasto CTRL viene in genere passato esattamente come viene ricevuto dal sistema.</span><span class="sxs-lookup"><span data-stu-id="9dcde-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="9dcde-788">Si tratta in genere di un singolo carattere spostato nello spazio riservato al carattere di controllo (0x0-0x1f).</span><span class="sxs-lookup"><span data-stu-id="9dcde-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="9dcde-789">Ad esempio, CTRL + @ (0x40) diventa NUL (0x00), CTRL + \[ (0x5b) diventa ESC (0x1b) e così via. Alcune combinazioni con il tasto CTRL vengono trattate in modo speciale in base alla tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="9dcde-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="9dcde-790">Chiave</span><span class="sxs-lookup"><span data-stu-id="9dcde-790">Key</span></span> | <span data-ttu-id="9dcde-791">Sequenza</span><span class="sxs-lookup"><span data-stu-id="9dcde-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="9dcde-792">CTRL+BARRA SPAZIATRICE</span><span class="sxs-lookup"><span data-stu-id="9dcde-792">Ctrl + Space</span></span> | <span data-ttu-id="9dcde-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="9dcde-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="9dcde-794">CTRL + freccia SU</span><span class="sxs-lookup"><span data-stu-id="9dcde-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="9dcde-795">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="9dcde-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="9dcde-796">CTRL + freccia GIÙ</span><span class="sxs-lookup"><span data-stu-id="9dcde-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="9dcde-797">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="9dcde-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="9dcde-798">CTRL + freccia DESTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="9dcde-799">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="9dcde-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="9dcde-800">CTRL + freccia SINISTRA</span><span class="sxs-lookup"><span data-stu-id="9dcde-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="9dcde-801">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="9dcde-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="9dcde-802">La combinazione <kbd>CTRL</kbd> sinistra + <kbd>ALT</kbd> destra viene trattata come ALT GR.</span><span class="sxs-lookup"><span data-stu-id="9dcde-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="9dcde-803">Quando entrambi gli elementi vengono visualizzati insieme, vengono rimossi e il valore Unicode del carattere presentato dal sistema viene passato nella destinazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="9dcde-804">Il sistema eseguirà la conversione preliminare dei valori di ALT GR in base alle impostazioni di input di sistema correnti.</span><span class="sxs-lookup"><span data-stu-id="9dcde-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="9dcde-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Esempi</span><span class="sxs-lookup"><span data-stu-id="9dcde-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="9dcde-806"><span id="example"></span><span id="EXAMPLE"></span>Esempio di sequenze di terminale SGR</span><span class="sxs-lookup"><span data-stu-id="9dcde-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="9dcde-807">Il codice seguente fornisce alcuni esempi di formattazione del testo.</span><span class="sxs-lookup"><span data-stu-id="9dcde-807">The following code provides several examples of text formatting.</span></span>

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
><span data-ttu-id="9dcde-808">Nell'esempio precedente la stringa '`\x1b[31m`' è l'implementazione di **ESC \[ &lt;n&gt; m** dove &lt;n&gt; è uguale a 31.</span><span class="sxs-lookup"><span data-stu-id="9dcde-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="9dcde-809">La figura seguente mostra l'output dell'esempio di codice precedente.</span><span class="sxs-lookup"><span data-stu-id="9dcde-809">The following graphic shows the output of the previous code example.</span></span>

![output della console con il comando sgr](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="9dcde-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Esempio di abilitazione dell'elaborazione del terminale virtuale</span><span class="sxs-lookup"><span data-stu-id="9dcde-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="9dcde-812">Il codice seguente fornisce un esempio della modalità consigliata per abilitare l'elaborazione del terminale virtuale per un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9dcde-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="9dcde-813">Lo scopo dell'esempio è dimostrare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="9dcde-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="9dcde-814">La modalità esistente deve sempre essere recuperata tramite GetConsoleMode e analizzata prima di essere impostata con SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="9dcde-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="9dcde-815">Verificare se SetConsoleMode restituisce `0` e GetLastError restituisce STATUS\_INVALID\_PARAMETER è il meccanismo corrente per determinare l'esecuzione in un sistema di livello inferiore.</span><span class="sxs-lookup"><span data-stu-id="9dcde-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="9dcde-816">Un'applicazione che riceve STATUS\_INVALID\_PARAMETER con uno dei flag di modalità della console più recenti nel campo bit dovrebbe scalare automaticamente il comportamento e riprovare.</span><span class="sxs-lookup"><span data-stu-id="9dcde-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="9dcde-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Esempio di alcune funzionalità dell'aggiornamento dell'anniversario</span><span class="sxs-lookup"><span data-stu-id="9dcde-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="9dcde-818">L'esempio seguente è destinato a essere un esempio di codice più affidabile che usa una serie di sequenze di escape per modificare il buffer, con particolare attenzione alle funzionalità aggiunte nell'aggiornamento dell'anniversario per Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9dcde-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="9dcde-819">Questo esempio usa il buffer alternativo dello schermo, la modifica delle tabulazioni, l'impostazione dei margini di scorrimento e la modifica del set di caratteri.</span><span class="sxs-lookup"><span data-stu-id="9dcde-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
// Copyright (C) Microsoft. All rights reserved.
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
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
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








