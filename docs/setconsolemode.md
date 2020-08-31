---
title: SetConsoleMode (funzione)
description: Imposta la modalità di input del buffer di input di una console o la modalità di output di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a524a9f730d53efd331a70693aadfeddeaad4cc0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060516"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="2d03a-104">SetConsoleMode (funzione)</span><span class="sxs-lookup"><span data-stu-id="2d03a-104">SetConsoleMode function</span></span>


<span data-ttu-id="2d03a-105">Imposta la modalità di input del buffer di input di una console o la modalità di output di un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2d03a-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="2d03a-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2d03a-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

<a name="parameters"></a><span data-ttu-id="2d03a-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="2d03a-107">Parameters</span></span>
----------

<span data-ttu-id="2d03a-108">*hConsoleHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2d03a-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="2d03a-109">Handle per il buffer di input della console o un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2d03a-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="2d03a-110">L'handle deve avere il diritto di accesso in \*\* \_ lettura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="2d03a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="2d03a-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="2d03a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2d03a-112">*dwMode* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2d03a-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="2d03a-113">Modalità di input o output da impostare.</span><span class="sxs-lookup"><span data-stu-id="2d03a-113">The input or output mode to be set.</span></span> <span data-ttu-id="2d03a-114">Se il parametro *hConsoleHandle* è un handle di input, la modalità può essere costituita da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="2d03a-114">If the *hConsoleHandle* parameter is an input handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="2d03a-115">Quando viene creata una console, tutte le modalità di input eccetto **Abilita \_ \_ input finestra** sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="2d03a-115">When a console is created, all input modes except **ENABLE\_WINDOW\_INPUT** are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="2d03a-116">valore</span><span class="sxs-lookup"><span data-stu-id="2d03a-116">Value</span></span></th>
<th><span data-ttu-id="2d03a-117">Significato</span><span class="sxs-lookup"><span data-stu-id="2d03a-117">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="2d03a-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="2d03a-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="2d03a-119">I caratteri letti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> vengono scritti nel buffer dello schermo attivo mentre vengono letti.</span><span class="sxs-lookup"><span data-stu-id="2d03a-119">Characters read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are written to the active screen buffer as they are read.</span></span> <span data-ttu-id="2d03a-120">Questa modalità può essere utilizzata solo se è abilitata anche la modalità <strong>ENABLE_LINE_INPUT</strong> .</span><span class="sxs-lookup"><span data-stu-id="2d03a-120">This mode can be used only if the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="2d03a-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="2d03a-122">Obbligatorio per abilitare o disabilitare i flag estesi.</span><span class="sxs-lookup"><span data-stu-id="2d03a-122">Required to enable or disable extended flags.</span></span> <span data-ttu-id="2d03a-123">Vedere <strong>ENABLE_INSERT_MODE</strong> e <strong>ENABLE_QUICK_EDIT_MODE</strong>.</span><span class="sxs-lookup"><span data-stu-id="2d03a-123">See <strong>ENABLE_INSERT_MODE</strong> and <strong>ENABLE_QUICK_EDIT_MODE</strong>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="2d03a-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="2d03a-125">Se abilitata, il testo immesso in una finestra della console verrà inserito nella posizione corrente del cursore e tutto il testo successivo a tale percorso non verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="2d03a-125">When enabled, text entered in a console window will be inserted at the current cursor location and all text following that location will not be overwritten.</span></span> <span data-ttu-id="2d03a-126">Se disabilitato, tutto il testo seguente verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="2d03a-126">When disabled, all following text will be overwritten.</span></span></p>
<p><span data-ttu-id="2d03a-127">Per abilitare questa modalità, utilizzare <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="2d03a-127">To enable this mode, use <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="2d03a-128">Per disabilitare questa modalità, utilizzare <strong>ENABLE_EXTENDED_FLAGS</strong> senza questo flag.</span><span class="sxs-lookup"><span data-stu-id="2d03a-128">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="2d03a-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="2d03a-130">La funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> restituisce solo quando viene letto un carattere di ritorno a capo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-130">The <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function returns only when a carriage return character is read.</span></span> <span data-ttu-id="2d03a-131">Se questa modalità è disabilitata, le funzioni restituiscono quando sono disponibili uno o più caratteri.</span><span class="sxs-lookup"><span data-stu-id="2d03a-131">If this mode is disabled, the functions return when one or more characters are available.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="2d03a-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="2d03a-133">Se il puntatore del mouse si trova all'interno dei bordi della finestra della console e la finestra ha lo stato attivo della tastiera, gli eventi del mouse generati dal movimento del mouse e dalle pressioni dei pulsanti vengono inseriti nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="2d03a-133">If the mouse pointer is within the borders of the console window and the window has the keyboard focus, mouse events generated by mouse movement and button presses are placed in the input buffer.</span></span> <span data-ttu-id="2d03a-134">Questi eventi vengono eliminati da <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, anche quando questa modalità è abilitata.</span><span class="sxs-lookup"><span data-stu-id="2d03a-134">These events are discarded by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, even when this mode is enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="2d03a-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="2d03a-136">CTRL + C viene elaborato dal sistema e non viene inserito nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="2d03a-136">CTRL+C is processed by the system and is not placed in the input buffer.</span></span> <span data-ttu-id="2d03a-137">Se il buffer di input viene letto da <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, altre chiavi di controllo vengono elaborate dal sistema e non vengono restituite nel buffer <strong>ReadFile</strong> o <strong>ReadConsole</strong> .</span><span class="sxs-lookup"><span data-stu-id="2d03a-137">If the input buffer is being read by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, other control keys are processed by the system and are not returned in the <strong>ReadFile</strong> or <strong>ReadConsole</strong> buffer.</span></span> <span data-ttu-id="2d03a-138">Se è abilitata anche la modalità <strong>ENABLE_LINE_INPUT</strong> , i caratteri backspace, ritorno a capo e avanzamento riga vengono gestiti dal sistema.</span><span class="sxs-lookup"><span data-stu-id="2d03a-138">If the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled, backspace, carriage return, and line feed characters are handled by the system.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="2d03a-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="2d03a-140">Questo flag consente all'utente di usare il mouse per selezionare e modificare il testo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-140">This flag enables the user to use the mouse to select and edit text.</span></span></p>
<p><span data-ttu-id="2d03a-141">Per abilitare questa modalità, utilizzare <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="2d03a-141">To enable this mode, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="2d03a-142">Per disabilitare questa modalità, utilizzare <strong>ENABLE_EXTENDED_FLAGS</strong> senza questo flag.</span><span class="sxs-lookup"><span data-stu-id="2d03a-142">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="2d03a-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="2d03a-144">Le interazioni utente che modificano le dimensioni del buffer dello schermo della console sono segnalate nel buffer di input della console&#39;s.</span><span class="sxs-lookup"><span data-stu-id="2d03a-144">User interactions that change the size of the console screen buffer are reported in the console&#39;s input buffer.</span></span> <span data-ttu-id="2d03a-145">Le informazioni su questi eventi possono essere lette dal buffer di input dalle applicazioni che usano la funzione <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , ma non da quelle che usano <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="2d03a-145">Information about these events can be read from the input buffer by applications using the <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> function, but not by those using <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="2d03a-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="2d03a-147">Impostando questo flag, il motore di elaborazione dei terminali virtuali viene indirizzato alla conversione dell'input utente ricevuto dalla finestra della console in sequenze di terminali virtuali della console che possono essere recuperate da un'applicazione di supporto tramite le funzioni ReadFile o ReadConsole.</span><span class="sxs-lookup"><span data-stu-id="2d03a-147">Setting this flag directs the Virtual Terminal processing engine to convert user input received by the console window into Console Virtual Terminal Sequences that can be retrieved by a supporting application through ReadFile or ReadConsole functions.</span></span></p>
<p><span data-ttu-id="2d03a-148">L'utilizzo tipico di questo flag è concepito insieme a ENABLE_VIRTUAL_TERMINAL_PROCESSING nell'handle di output per connettersi a un'applicazione che comunica esclusivamente tramite sequenze di terminali virtuali.</span><span class="sxs-lookup"><span data-stu-id="2d03a-148">The typical usage of this flag is intended in conjunction with ENABLE_VIRTUAL_TERMINAL_PROCESSING on the output handle to connect to an application that communicates exclusively via virtual terminal sequences.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="2d03a-149">Se il parametro *hConsoleHandle* è un handle del buffer dello schermo, la modalità può essere costituita da uno o più dei valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="2d03a-149">If the *hConsoleHandle* parameter is a screen buffer handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="2d03a-150">Quando viene creato un buffer dello schermo, entrambe le modalità di output sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="2d03a-150">When a screen buffer is created, both output modes are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="2d03a-151">valore</span><span class="sxs-lookup"><span data-stu-id="2d03a-151">Value</span></span></th>
<th><span data-ttu-id="2d03a-152">Significato</span><span class="sxs-lookup"><span data-stu-id="2d03a-152">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="2d03a-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="2d03a-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="2d03a-154">I caratteri scritti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o restituiti dalla funzione <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> vengono esaminati per le sequenze di controllo ASCII e viene eseguita l'azione corretta.</span><span class="sxs-lookup"><span data-stu-id="2d03a-154">Characters written by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> function or echoed by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are examined for ASCII control sequences and the correct action is performed.</span></span> <span data-ttu-id="2d03a-155">Vengono elaborati i caratteri di ritorno a capo, tabulazione, ritorno a capo e avanzamento riga.</span><span class="sxs-lookup"><span data-stu-id="2d03a-155">Backspace, tab, bell, carriage return, and line feed characters are processed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="2d03a-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="2d03a-157">Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o si esegue l'eco con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, il cursore si sposta all'inizio della riga successiva quando raggiunge la fine della riga corrente.</span><span class="sxs-lookup"><span data-stu-id="2d03a-157">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> or echoing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, the cursor moves to the beginning of the next row when it reaches the end of the current row.</span></span> <span data-ttu-id="2d03a-158">In questo modo, le righe visualizzate nella finestra della console scorrono automaticamente quando il cursore avanza oltre l'ultima riga nella finestra.</span><span class="sxs-lookup"><span data-stu-id="2d03a-158">This causes the rows displayed in the console window to scroll up automatically when the cursor advances beyond the last row in the window.</span></span> <span data-ttu-id="2d03a-159">Consente inoltre di scorrere verso l'alto il contenuto del buffer dello schermo della console (eliminando la prima riga del buffer dello schermo della console) quando il cursore avanza oltre l'ultima riga nel buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2d03a-159">It also causes the contents of the console screen buffer to scroll up (discarding the top row of the console screen buffer) when the cursor advances beyond the last row in the console screen buffer.</span></span> <span data-ttu-id="2d03a-160">Se questa modalità è disabilitata, l'ultimo carattere della riga viene sovrascritto con i caratteri successivi.</span><span class="sxs-lookup"><span data-stu-id="2d03a-160">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="2d03a-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="2d03a-162">Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, i caratteri vengono analizzati per VT100 e sequenze di caratteri di controllo simili che controllano lo spostamento del cursore, la modalità colore/carattere e altre operazioni che possono essere eseguite anche tramite le API della console esistenti.</span><span class="sxs-lookup"><span data-stu-id="2d03a-162">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, characters are parsed for VT100 and similar control character sequences that control cursor movement, color/font mode, and other operations that can also be performed via the existing Console APIs.</span></span> <span data-ttu-id="2d03a-163">Per altre informazioni, vedere <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">sequenze di terminali virtuali della console</a>.</span><span class="sxs-lookup"><span data-stu-id="2d03a-163">For more information, see <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2d03a-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="2d03a-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="2d03a-165">Quando si scrive con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, viene aggiunto uno stato aggiuntivo al wrapping di fine riga che può ritardare le operazioni di spostamento del cursore e scorrimento del buffer.</span><span class="sxs-lookup"><span data-stu-id="2d03a-165">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, this adds an additional state to end-of-line wrapping that can delay the cursor move and buffer scroll operations.</span></span></p>
<p><span data-ttu-id="2d03a-166">In genere, quando ENABLE_WRAP_AT_EOL_OUTPUT è impostato e il testo raggiunge la fine della riga, il cursore si sposta immediatamente alla riga successiva e il contenuto del buffer scorre verso l'alto di una riga.</span><span class="sxs-lookup"><span data-stu-id="2d03a-166">Normally when ENABLE_WRAP_AT_EOL_OUTPUT is set and text reaches the end of the line, the cursor will immediately move to the next line and the contents of the buffer will scroll up by one line.</span></span> <span data-ttu-id="2d03a-167">Diversamente da questo set di flag, l'operazione di scorrimento e lo spostamento del cursore vengono posticipati fino all'arrivo del carattere successivo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-167">In contrast with this flag set, the scroll operation and cursor move is delayed until the next character arrives.</span></span> <span data-ttu-id="2d03a-168">Il carattere scritto verrà stampato nella posizione finale sulla riga e il cursore rimarrà al di sopra di questo carattere come se ENABLE_WRAP_AT_EOL_OUTPUT fosse disattivato, ma il successivo carattere stampabile verrà stampato come se ENABLE_WRAP_AT_EOL_OUTPUT fosse attivo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-168">The written character will be printed in the final position on the line and the cursor will remain above this character as if ENABLE_WRAP_AT_EOL_OUTPUT was off, but the next printable character will be printed as if ENABLE_WRAP_AT_EOL_OUTPUT is on.</span></span> <span data-ttu-id="2d03a-169">Non si verificherà alcuna sovrascrittura.</span><span class="sxs-lookup"><span data-stu-id="2d03a-169">No overwrite will occur.</span></span> <span data-ttu-id="2d03a-170">In particolare, il cursore avanza rapidamente fino alla riga seguente, viene eseguito uno scorrimento, se necessario, il carattere viene stampato e il cursore avanza di una posizione.</span><span class="sxs-lookup"><span data-stu-id="2d03a-170">Specifically, the cursor quickly advances down to the following line, a scroll is performed if necessary, the character is printed, and the cursor advances one more position.</span></span></p>
<p><span data-ttu-id="2d03a-171">L'utilizzo tipico di questo flag è concepito insieme all'impostazione ENABLE_VIRTUAL_TERMINAL_PROCESSING per emulare meglio un emulatore di terminale in cui la scrittura del carattere finale sullo schermo (nell'angolo inferiore destro) senza attivare uno scorrimento immediato è il comportamento desiderato.</span><span class="sxs-lookup"><span data-stu-id="2d03a-171">The typical usage of this flag is intended in conjunction with setting ENABLE_VIRTUAL_TERMINAL_PROCESSING to better emulate a terminal emulator where writing the final character on the screen (in the bottom right corner) without triggering an immediate scroll is the desired behavior.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2d03a-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="2d03a-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="2d03a-173">Le API per la scrittura di attributi di caratteri, tra cui <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> e <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , consentono di utilizzare flag di <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">attributi di caratteri</a> per modificare il colore del primo piano e dello sfondo del testo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-173">The APIs for writing character attributes including <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> and <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> allow the usage of flags from <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">character attributes</a> to adjust the color of the foreground and background of text.</span></span> <span data-ttu-id="2d03a-174">È stato inoltre specificato un intervallo di flag DBCS con il prefisso COMMON_LVB.</span><span class="sxs-lookup"><span data-stu-id="2d03a-174">Additionally, a range of DBCS flags was specified with the COMMON_LVB prefix.</span></span> <span data-ttu-id="2d03a-175">In passato, questi flag funzionavano solo nelle tabelle codici DBCS per le lingue cinese, giapponese e coreano.</span><span class="sxs-lookup"><span data-stu-id="2d03a-175">Historically, these flags only functioned in DBCS code pages for Chinese, Japanese, and Korean languages.</span></span></p>
<p><span data-ttu-id="2d03a-176">Con l'eccezione dei flag di byte iniziali e finali, i flag rimanenti che descrivono il disegno a linee e i video inversi (scambio di primo piano e colori di sfondo) possono essere utili per altri linguaggi per enfatizzare porzioni di output.</span><span class="sxs-lookup"><span data-stu-id="2d03a-176">With exception of the leading byte and trailing byte flags, the remaining flags describing line drawing and reverse video (swap foreground and background colors) can be useful for other languages to emphasize portions of output.</span></span></p>
<p><span data-ttu-id="2d03a-177">L'impostazione di questo flag della modalità console consentirà l'utilizzo di questi attributi in ogni tabella codici in ogni lingua.</span><span class="sxs-lookup"><span data-stu-id="2d03a-177">Setting this console mode flag will allow these attributes to be used in every code page on every language.</span></span></p>
<p><span data-ttu-id="2d03a-178">È disattivata per impostazione predefinita per garantire la compatibilità con le applicazioni note che hanno utilizzato in passato la console ignorando questi flag sui computer non CJK per archiviare i bit in questi campi per loro scopi o per errore.</span><span class="sxs-lookup"><span data-stu-id="2d03a-178">It is off by default to maintain compatibility with known applications that have historically taken advantage of the console ignoring these flags on non-CJK machines to store bits in these fields for their own purposes or by accident.</span></span></p>
<p><span data-ttu-id="2d03a-179">Si noti che l'uso della modalità di ENABLE_VIRTUAL_TERMINAL_PROCESSING può comportare l'impostazione di LVB Grid e dei flag video inversi mentre questo flag è disattivato se l'applicazione collegata richiede la sottolineatura o il video inverso tramite le <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">sequenze di terminali virtuali della console</a>.</span><span class="sxs-lookup"><span data-stu-id="2d03a-179">Note that using the ENABLE_VIRTUAL_TERMINAL_PROCESSING mode can result in LVB grid and reverse video flags being set while this flag is still off if the attached application requests underlining or inverse video via <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="2d03a-180">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2d03a-180">Return value</span></span>
------------

<span data-ttu-id="2d03a-181">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="2d03a-181">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2d03a-182">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="2d03a-182">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2d03a-183">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2d03a-183">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2d03a-184">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2d03a-184">Remarks</span></span>
-------

<span data-ttu-id="2d03a-185">Una console di è costituita da un buffer di input e uno o più buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-185">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="2d03a-186">La modalità di un buffer della console determina il comportamento della console durante le operazioni di input e output (I/O).</span><span class="sxs-lookup"><span data-stu-id="2d03a-186">The mode of a console buffer determines how the console behaves during input and output (I/O) operations.</span></span> <span data-ttu-id="2d03a-187">Un set di costanti flag viene usato con gli handle di input e un altro set viene usato con gli handle del buffer dello schermo (output).</span><span class="sxs-lookup"><span data-stu-id="2d03a-187">One set of flag constants is used with input handles, and another set is used with screen buffer (output) handles.</span></span> <span data-ttu-id="2d03a-188">L'impostazione delle modalità di output di un buffer dello schermo non influisce sulle modalità di output di altri buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="2d03a-188">Setting the output modes of one screen buffer does not affect the output modes of other screen buffers.</span></span>

<span data-ttu-id="2d03a-189">Le **modalità \_ Abilita \_ input riga** e **Abilita \_ \_ input echo** influiscono solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) per la lettura dal buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="2d03a-189">The **ENABLE\_LINE\_INPUT** and **ENABLE\_ECHO\_INPUT** modes only affect processes that use [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) to read from the console's input buffer.</span></span> <span data-ttu-id="2d03a-190">Analogamente, l'abilitazione della modalità di \*\* \_ \_ input elaborati\*\* interessa principalmente gli utenti **ReadFile** e **ReadConsole** , con la differenza che determina anche se l'input di CTRL + C viene segnalato nel buffer di input (per la lettura da parte della funzione [**ReadConsoleInput**](readconsoleinput.md) ) o viene passato a una funzione [**HandlerRoutine**](handlerroutine.md) definita dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2d03a-190">Similarly, the **ENABLE\_PROCESSED\_INPUT** mode primarily affects **ReadFile** and **ReadConsole** users, except that it also determines whether Ctrl+C input is reported in the input buffer (to be read by the [**ReadConsoleInput**](readconsoleinput.md) function) or is passed to a [**HandlerRoutine**](handlerroutine.md) function defined by the application.</span></span>

<span data-ttu-id="2d03a-191">Le **modalità \_ Abilita \_ input finestra** e **Abilita \_ \_ input mouse** determinano se le interazioni utente che coinvolgono il ridimensionamento delle finestre e le azioni del mouse vengono segnalate nel buffer di input o eliminate.</span><span class="sxs-lookup"><span data-stu-id="2d03a-191">The **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** modes determine whether user interactions involving window resizing and mouse actions are reported in the input buffer or discarded.</span></span> <span data-ttu-id="2d03a-192">Questi eventi possono essere letti da [**ReadConsoleInput**](readconsoleinput.md), ma vengono sempre filtrati in base a [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**ReadConsole**](readconsole.md).</span><span class="sxs-lookup"><span data-stu-id="2d03a-192">These events can be read by [**ReadConsoleInput**](readconsoleinput.md), but they are always filtered by [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md).</span></span>

<span data-ttu-id="2d03a-193">L' **Abilitazione dell' \_ \_ output elaborato** e l' **Abilitazione del \_ wrapping \_ in modalità di \_ \_ output EOL** hanno effetto solo sui processi che usano [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md).</span><span class="sxs-lookup"><span data-stu-id="2d03a-193">The **ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** modes only affect processes using [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md).</span></span>

<span data-ttu-id="2d03a-194">Per determinare la modalità corrente di un buffer di input della console o di un buffer dello schermo, usare la funzione [**GetConsoleMode**](getconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="2d03a-194">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="2d03a-195">Esempi</span><span class="sxs-lookup"><span data-stu-id="2d03a-195">Examples</span></span>
--------

<span data-ttu-id="2d03a-196">Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="2d03a-196">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="2d03a-197">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2d03a-197">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2d03a-198">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2d03a-198">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2d03a-199">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2d03a-199">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d03a-200">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="2d03a-200">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2d03a-201">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="2d03a-201">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d03a-202">Intestazione</span><span class="sxs-lookup"><span data-stu-id="2d03a-202">Header</span></span></p></td>
<td><span data-ttu-id="2d03a-203">ConsoleApi. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2d03a-203">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d03a-204">Libreria</span><span class="sxs-lookup"><span data-stu-id="2d03a-204">Library</span></span></p></td>
<td><span data-ttu-id="2d03a-205">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2d03a-205">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d03a-206">DLL</span><span class="sxs-lookup"><span data-stu-id="2d03a-206">DLL</span></span></p></td>
<td><span data-ttu-id="2d03a-207">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2d03a-207">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2d03a-208"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2d03a-208"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2d03a-209">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="2d03a-209">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2d03a-210">Modalità console</span><span class="sxs-lookup"><span data-stu-id="2d03a-210">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="2d03a-211">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="2d03a-211">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="2d03a-212">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="2d03a-212">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="2d03a-213">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="2d03a-213">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="2d03a-214">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2d03a-214">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="2d03a-215">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="2d03a-215">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="2d03a-216">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="2d03a-216">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="2d03a-217">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="2d03a-217">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




