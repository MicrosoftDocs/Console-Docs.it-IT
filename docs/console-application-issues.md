---
title: Problemi relativi alle applicazioni console
description: Esaminare i problemi dell'applicazione console, ad esempio le funzioni che accettano o restituiscono stringhe dei set di caratteri OEM e funzioni che accettano o restituiscono stringhe di set di caratteri ANSI.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: a1e49e605d1379984ebff7d1737db5ef96c4ff0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038459"
---
# <a name="console-application-issues"></a><span data-ttu-id="d845f-104">Problemi relativi alle applicazioni console</span><span class="sxs-lookup"><span data-stu-id="d845f-104">Console Application Issues</span></span>

<span data-ttu-id="d845f-105">Le funzioni console a 8 bit utilizzano la tabella codici OEM.</span><span class="sxs-lookup"><span data-stu-id="d845f-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="d845f-106">Per impostazione predefinita, tutte le altre funzioni usano la tabella codici ANSI.</span><span class="sxs-lookup"><span data-stu-id="d845f-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="d845f-107">Ciò significa che le stringhe restituite dalle funzioni console potrebbero non essere elaborate correttamente dalle altre funzioni e viceversa.</span><span class="sxs-lookup"><span data-stu-id="d845f-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="d845f-108">Se, ad esempio, **FindFirstFileA** restituisce una stringa che contiene alcuni caratteri ANSI estesi, **WriteConsoleA** non visualizzerà correttamente la stringa.</span><span class="sxs-lookup"><span data-stu-id="d845f-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="d845f-109">La soluzione migliore a lungo termine per un'applicazione console consiste nell'usare **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span><span class="sxs-lookup"><span data-stu-id="d845f-109">The best long-term solution for a console application is to use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="d845f-110">La console accetta la codifica UTF-16 sulla variante W delle API o la codifica UTF-8 in una variante delle API dopo l'uso di **[SetConsoleCP](setconsolecp.md)** e **[SetConsoleOutputCP](setconsoleoutputcp.md)** in `65001` ( `CP_UTF8` Constant) per la tabella codici UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d845f-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="d845f-111">Escludendo tale soluzione, un'applicazione console deve usare la funzione [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="d845f-111">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="d845f-112">Questa funzione modifica le funzioni dei file rilevanti in modo che producano stringhe di set di caratteri OEM anziché stringhe di set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="d845f-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="d845f-113">Di seguito sono riportate le funzioni di file:</span><span class="sxs-lookup"><span data-stu-id="d845f-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="d845f-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="d845f-114">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="d845f-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-115">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="d845f-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="d845f-116">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="d845f-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="d845f-117">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="d845f-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="d845f-118">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="d845f-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="d845f-119">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="d845f-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="d845f-120">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="d845f-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-121">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="d845f-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="d845f-122">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="d845f-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="d845f-123">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="d845f-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="d845f-124">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="d845f-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="d845f-125">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="d845f-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="d845f-126">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="d845f-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="d845f-127">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="d845f-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-128">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="d845f-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="d845f-129">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="d845f-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="d845f-130">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="d845f-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="d845f-131">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="d845f-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-132">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="d845f-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="d845f-133">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="d845f-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="d845f-134">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="d845f-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="d845f-135">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="d845f-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="d845f-136">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="d845f-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="d845f-137">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="d845f-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-138">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="d845f-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="d845f-139">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="d845f-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="d845f-140">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="d845f-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="d845f-141">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="d845f-142">Quando si gestiscono le righe di comando, un'applicazione console deve ottenere la riga di comando in formato Unicode e convertirla in un modulo OEM usando le funzioni da carattere a OEM pertinenti.</span><span class="sxs-lookup"><span data-stu-id="d845f-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="d845f-143">Si noti inoltre che *argv* utilizza il set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="d845f-143">Note, also, that *argv* uses the ANSI character set.</span></span>
