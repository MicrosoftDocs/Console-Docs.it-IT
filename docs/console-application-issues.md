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
ms.openlocfilehash: e81a2b8f6e3b7ba17a7fd704aac868425c86d52c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358271"
---
# <a name="console-application-issues"></a><span data-ttu-id="8a760-104">Problemi relativi alle applicazioni console</span><span class="sxs-lookup"><span data-stu-id="8a760-104">Console Application Issues</span></span>

<span data-ttu-id="8a760-105">Le funzioni console a 8 bit utilizzano la tabella codici OEM.</span><span class="sxs-lookup"><span data-stu-id="8a760-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="8a760-106">Per impostazione predefinita, tutte le altre funzioni usano la tabella codici ANSI.</span><span class="sxs-lookup"><span data-stu-id="8a760-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="8a760-107">Ciò significa che le stringhe restituite dalle funzioni console potrebbero non essere elaborate correttamente dalle altre funzioni e viceversa.</span><span class="sxs-lookup"><span data-stu-id="8a760-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="8a760-108">Se, ad esempio, **FindFirstFileA** restituisce una stringa che contiene alcuni caratteri ANSI estesi, **WriteConsoleA** non visualizzerà correttamente la stringa.</span><span class="sxs-lookup"><span data-stu-id="8a760-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="8a760-109">La soluzione migliore a lungo termine per un'applicazione console consiste nell'usare **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="8a760-109">The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="8a760-110">La console accetta la codifica UTF-16 sulla variante W delle API o la codifica UTF-8 in una variante delle API dopo l'uso di **[SetConsoleCP](setconsolecp.md)** e **[SetConsoleOutputCP](setconsoleoutputcp.md)** in `65001` ( `CP_UTF8` Constant) per la tabella codici UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8a760-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="8a760-111">Escludendo tale soluzione, un'applicazione console deve usare la funzione [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) .</span><span class="sxs-lookup"><span data-stu-id="8a760-111">Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function.</span></span> <span data-ttu-id="8a760-112">Questa funzione modifica le funzioni dei file rilevanti in modo che producano stringhe di set di caratteri OEM anziché stringhe di set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="8a760-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="8a760-113">Di seguito sono riportate le funzioni di file:</span><span class="sxs-lookup"><span data-stu-id="8a760-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="8a760-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="8a760-114">CopyFile</span></span>](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [<span data-ttu-id="8a760-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-115">CreateDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [<span data-ttu-id="8a760-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="8a760-116">CreateFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [<span data-ttu-id="8a760-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="8a760-117">CreateProcess</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [<span data-ttu-id="8a760-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="8a760-118">DeleteFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [<span data-ttu-id="8a760-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="8a760-119">FindFirstFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [<span data-ttu-id="8a760-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="8a760-120">FindNextFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [<span data-ttu-id="8a760-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-121">GetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [<span data-ttu-id="8a760-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="8a760-122">GetDiskFreeSpace</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [<span data-ttu-id="8a760-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="8a760-123">GetDriveType</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="8a760-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="8a760-124">GetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [<span data-ttu-id="8a760-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="8a760-125">GetFullPathName</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [<span data-ttu-id="8a760-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="8a760-126">GetModuleFileName</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [<span data-ttu-id="8a760-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="8a760-127">GetModuleHandle</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [<span data-ttu-id="8a760-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-128">GetSystemDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [<span data-ttu-id="8a760-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="8a760-129">GetTempFileName</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [<span data-ttu-id="8a760-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="8a760-130">GetTempPath</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [<span data-ttu-id="8a760-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="8a760-131">GetVolumeInformation</span></span>](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [<span data-ttu-id="8a760-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-132">GetWindowsDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [<span data-ttu-id="8a760-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="8a760-133">LoadLibrary</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="8a760-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="8a760-134">LoadLibraryEx</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [<span data-ttu-id="8a760-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="8a760-135">MoveFile</span></span>](/windows/win32/api/winbase/nf-winbase-movefile)  
        [<span data-ttu-id="8a760-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="8a760-136">MoveFileEx</span></span>](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [<span data-ttu-id="8a760-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="8a760-137">OpenFile</span></span>](/windows/win32/api/winbase/nf-winbase-openfile)  
        [<span data-ttu-id="8a760-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-138">RemoveDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [<span data-ttu-id="8a760-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="8a760-139">SearchPath</span></span>](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [<span data-ttu-id="8a760-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="8a760-140">SetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [<span data-ttu-id="8a760-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="8a760-141">SetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="8a760-142">Quando si gestiscono le righe di comando, un'applicazione console deve ottenere la riga di comando in formato Unicode e convertirla in un modulo OEM usando le funzioni da carattere a OEM pertinenti.</span><span class="sxs-lookup"><span data-stu-id="8a760-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="8a760-143">Si noti inoltre che *argv* utilizza il set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="8a760-143">Note, also, that *argv* uses the ANSI character set.</span></span>