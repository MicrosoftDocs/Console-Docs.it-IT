---
title: Problemi delle applicazioni console
description: Esaminare i problemi dell'applicazione console, ad esempio le funzioni che accettano o restituiscono stringhe dei set di caratteri OEM e funzioni che accettano o restituiscono stringhe di set di caratteri ANSI.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: 4bf0d6792a991d8ae141ec0b1b9c940311e00ab9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060169"
---
# <a name="console-application-issues"></a><span data-ttu-id="013da-104">Problemi delle applicazioni console</span><span class="sxs-lookup"><span data-stu-id="013da-104">Console Application Issues</span></span>

<span data-ttu-id="013da-105">Le funzioni console a 8 bit utilizzano la tabella codici OEM.</span><span class="sxs-lookup"><span data-stu-id="013da-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="013da-106">Per impostazione predefinita, tutte le altre funzioni usano la tabella codici ANSI.</span><span class="sxs-lookup"><span data-stu-id="013da-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="013da-107">Ciò significa che le stringhe restituite dalle funzioni console potrebbero non essere elaborate correttamente dalle altre funzioni e viceversa.</span><span class="sxs-lookup"><span data-stu-id="013da-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="013da-108">Se, ad esempio, **FindFirstFileA** restituisce una stringa che contiene alcuni caratteri ANSI estesi, **WriteConsoleA** non visualizzerà correttamente la stringa.</span><span class="sxs-lookup"><span data-stu-id="013da-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="013da-109">La soluzione migliore a lungo termine per un'applicazione console consiste nell'usare Unicode.</span><span class="sxs-lookup"><span data-stu-id="013da-109">The best long-term solution for a console application is to use Unicode.</span></span> <span data-ttu-id="013da-110">Escludendo tale soluzione, un'applicazione console deve usare la funzione [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="013da-110">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="013da-111">Questa funzione modifica le funzioni dei file rilevanti in modo che producano stringhe di set di caratteri OEM anziché stringhe di set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="013da-111">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="013da-112">Di seguito sono riportate le funzioni di file:</span><span class="sxs-lookup"><span data-stu-id="013da-112">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="013da-113">CopyFile</span><span class="sxs-lookup"><span data-stu-id="013da-113">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="013da-114">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-114">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="013da-115">CreateFile</span><span class="sxs-lookup"><span data-stu-id="013da-115">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="013da-116">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="013da-116">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="013da-117">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="013da-117">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="013da-118">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="013da-118">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="013da-119">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="013da-119">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="013da-120">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-120">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="013da-121">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="013da-121">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="013da-122">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="013da-122">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="013da-123">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="013da-123">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="013da-124">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="013da-124">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="013da-125">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="013da-125">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="013da-126">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="013da-126">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="013da-127">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-127">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="013da-128">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="013da-128">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="013da-129">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="013da-129">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="013da-130">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="013da-130">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="013da-131">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-131">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="013da-132">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="013da-132">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="013da-133">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="013da-133">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="013da-134">MoveFile</span><span class="sxs-lookup"><span data-stu-id="013da-134">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="013da-135">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="013da-135">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="013da-136">OpenFile</span><span class="sxs-lookup"><span data-stu-id="013da-136">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="013da-137">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-137">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="013da-138">SearchPath</span><span class="sxs-lookup"><span data-stu-id="013da-138">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="013da-139">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="013da-139">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="013da-140">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="013da-140">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="013da-141">Quando si gestiscono le righe di comando, un'applicazione console deve ottenere la riga di comando in formato Unicode e convertirla in un modulo OEM usando le funzioni da carattere a OEM pertinenti.</span><span class="sxs-lookup"><span data-stu-id="013da-141">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="013da-142">Si noti inoltre che *argv* utilizza il set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="013da-142">Note, also, that *argv* uses the ANSI character set.</span></span>
