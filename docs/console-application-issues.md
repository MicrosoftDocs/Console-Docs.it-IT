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
# <a name="console-application-issues"></a>Problemi relativi alle applicazioni console

Le funzioni console a 8 bit utilizzano la tabella codici OEM. Per impostazione predefinita, tutte le altre funzioni usano la tabella codici ANSI. Ciò significa che le stringhe restituite dalle funzioni console potrebbero non essere elaborate correttamente dalle altre funzioni e viceversa. Se, ad esempio, **FindFirstFileA** restituisce una stringa che contiene alcuni caratteri ANSI estesi, **WriteConsoleA** non visualizzerà correttamente la stringa.

La soluzione migliore a lungo termine per un'applicazione console consiste nell'usare **[Unicode](/windows/win32/intl/unicode)**. La console accetta la codifica UTF-16 sulla variante W delle API o la codifica UTF-8 in una variante delle API dopo l'uso di **[SetConsoleCP](setconsolecp.md)** e **[SetConsoleOutputCP](setconsoleoutputcp.md)** in `65001` ( `CP_UTF8` Constant) per la tabella codici UTF-8.

Escludendo tale soluzione, un'applicazione console deve usare la funzione [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Questa funzione modifica le funzioni dei file rilevanti in modo che producano stringhe di set di caratteri OEM anziché stringhe di set di caratteri ANSI.

Di seguito sono riportate le funzioni di file:

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        [MoveFileEx](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [SetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

Quando si gestiscono le righe di comando, un'applicazione console deve ottenere la riga di comando in formato Unicode e convertirla in un modulo OEM usando le funzioni da carattere a OEM pertinenti. Si noti inoltre che *argv* utilizza il set di caratteri ANSI.