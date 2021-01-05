---
title: CreatePseudoConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione CreatePseudoConsole, che alloca un nuovo pseudoconsole per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b015f224684a53a8bb654f04b1797ac1af794fc3
ms.sourcegitcommit: f16996b9c7deead9bcfa44954be93a6ba087abcb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/16/2020
ms.locfileid: "97601478"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="b6a50-104">CreatePseudoConsole (funzione)</span><span class="sxs-lookup"><span data-stu-id="b6a50-104">CreatePseudoConsole function</span></span>

<span data-ttu-id="b6a50-105">Crea un nuovo oggetto pseudoconsole per il processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="b6a50-105">Creates a new pseudoconsole object for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6a50-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b6a50-106">Syntax</span></span>

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a><span data-ttu-id="b6a50-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="b6a50-107">Parameters</span></span>

<span data-ttu-id="b6a50-108">*dimensioni* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-108">*size* \[in\]</span></span>  
<span data-ttu-id="b6a50-109">Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati durante la creazione iniziale del pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b6a50-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="b6a50-110">Questa operazione può essere modificata in un secondo momento con [ResizePseudoConsole](resizepseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="b6a50-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="b6a50-111">*hInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="b6a50-112">Handle aperto per un flusso di dati che rappresenta l'input dell'utente per il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b6a50-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="b6a50-113">Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="b6a50-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="b6a50-114">*hOutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="b6a50-115">Handle aperto per un flusso di dati che rappresenta l'output dell'applicazione dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b6a50-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="b6a50-116">Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .</span><span class="sxs-lookup"><span data-stu-id="b6a50-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="b6a50-117">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="b6a50-118">I possibili valori sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="b6a50-118">The value can be one of the following:</span></span>

| <span data-ttu-id="b6a50-119">Valore</span><span class="sxs-lookup"><span data-stu-id="b6a50-119">Value</span></span> | <span data-ttu-id="b6a50-120">Significato</span><span class="sxs-lookup"><span data-stu-id="b6a50-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="b6a50-121">**0**</span><span class="sxs-lookup"><span data-stu-id="b6a50-121">**0**</span></span> | <span data-ttu-id="b6a50-122">Eseguire una creazione pseudoconsole standard.</span><span class="sxs-lookup"><span data-stu-id="b6a50-122">Perform a standard pseudoconsole creation.</span></span> |
| <span data-ttu-id="b6a50-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="b6a50-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1</span></span> | <span data-ttu-id="b6a50-124">La sessione pseudoconsole creata tenterà di ereditare la posizione del cursore della console padre.</span><span class="sxs-lookup"><span data-stu-id="b6a50-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span> |

<span data-ttu-id="b6a50-125">*phPC* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="b6a50-126">Puntatore a una posizione che riceverà un handle per il nuovo dispositivo pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b6a50-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6a50-127">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b6a50-127">Return value</span></span>

<span data-ttu-id="b6a50-128">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="b6a50-128">Type: **HRESULT**</span></span>

<span data-ttu-id="b6a50-129">Se questo metodo ha esito positivo, restituisce **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="b6a50-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="b6a50-130">In caso contrario, restituisce un codice di errore **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="b6a50-130">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6a50-131">Commenti</span><span class="sxs-lookup"><span data-stu-id="b6a50-131">Remarks</span></span>

<span data-ttu-id="b6a50-132">Questa funzione viene utilizzata principalmente dalle applicazioni che tentano di essere una finestra del terminale per un'applicazione con interfaccia utente della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="b6a50-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="b6a50-133">I chiamanti diventano responsabili della presentazione delle informazioni sul flusso di output e della raccolta dell'input utente e della relativa serializzazione nel flusso di input.</span><span class="sxs-lookup"><span data-stu-id="b6a50-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="b6a50-134">I flussi di input e di output codificati come UTF-8 contengono testo normale con sequenze di [terminali virtuali](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="b6a50-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span>

<span data-ttu-id="b6a50-135">Nel flusso di output, le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) possono essere decodificate dall'applicazione chiamante per il layout e presentano il testo normale in una finestra di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b6a50-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span>

<span data-ttu-id="b6a50-136">Nel flusso di input, il testo normale rappresenta i tasti di scelta rapida standard di un utente.</span><span class="sxs-lookup"><span data-stu-id="b6a50-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="b6a50-137">Le operazioni più complesse sono rappresentate da chiavi di controllo codificate e da movimenti del mouse come [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) incorporate in questo flusso.</span><span class="sxs-lookup"><span data-stu-id="b6a50-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="b6a50-138">L'handle creato da questa funzione deve essere chiuso con [ClosePseudoConsole](closepseudoconsole.md) al termine delle operazioni.</span><span class="sxs-lookup"><span data-stu-id="b6a50-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="b6a50-139">Se `PSEUDOCONSOLE_INHERIT_CURSOR` si utilizza, l'applicazione chiamante deve essere preparata a rispondere alla richiesta per lo stato del cursore in modo asincrono in un thread in background tramite l'inoltro o l'interpretazione della richiesta di informazioni di cursore che verranno ricevute `hOutput` e in risposta `hInput` .</span><span class="sxs-lookup"><span data-stu-id="b6a50-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="b6a50-140">In caso contrario, può causare il blocco dell'applicazione chiamante durante l'esecuzione di un'altra richiesta del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b6a50-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

## <a name="examples"></a><span data-ttu-id="b6a50-141">Esempi</span><span class="sxs-lookup"><span data-stu-id="b6a50-141">Examples</span></span>

<span data-ttu-id="b6a50-142">Per una procedura dettagliata sull'uso di questa funzione per stabilire una sessione pseudoconsole, vedere [creazione di una sessione pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="b6a50-142">For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b6a50-143">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b6a50-143">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b6a50-144">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b6a50-144">Minimum supported client</span></span> | <span data-ttu-id="b6a50-145">Aggiornamento di Windows 10 ottobre 2018 (versione 1809) \[ solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-145">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="b6a50-146">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="b6a50-146">Minimum supported server</span></span> | <span data-ttu-id="b6a50-147">\[Solo app desktop Windows Server 2019\]</span><span class="sxs-lookup"><span data-stu-id="b6a50-147">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="b6a50-148">Intestazione</span><span class="sxs-lookup"><span data-stu-id="b6a50-148">Header</span></span> | <span data-ttu-id="b6a50-149">ConsoleApi.h (tramite WinCon.h, con Windows.h)</span><span class="sxs-lookup"><span data-stu-id="b6a50-149">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b6a50-150">Libreria</span><span class="sxs-lookup"><span data-stu-id="b6a50-150">Library</span></span> | <span data-ttu-id="b6a50-151">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b6a50-151">Kernel32.lib</span></span> |
| <span data-ttu-id="b6a50-152">DLL</span><span class="sxs-lookup"><span data-stu-id="b6a50-152">DLL</span></span> | <span data-ttu-id="b6a50-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b6a50-153">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b6a50-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b6a50-154">See also</span></span>

[<span data-ttu-id="b6a50-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="b6a50-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="b6a50-156">Creazione di una sessione di pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b6a50-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="b6a50-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="b6a50-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="b6a50-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="b6a50-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
