---
title: Registrazione di una funzione del gestore di controllo
description: Questo è un esempio della funzione SetConsoleCtrlHandler usata per installare un gestore di controllo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: cda72574b13c8c8fa1644e78310c66598c7b9dcf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060345"
---
# <a name="registering-a-control-handler-function"></a><span data-ttu-id="3fb75-104">Registrazione di una funzione del gestore di controllo</span><span class="sxs-lookup"><span data-stu-id="3fb75-104">Registering a Control Handler Function</span></span>


<span data-ttu-id="3fb75-105">Questo è un esempio della funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) usata per installare un gestore di controllo.</span><span class="sxs-lookup"><span data-stu-id="3fb75-105">This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.</span></span>

<span data-ttu-id="3fb75-106">Quando viene ricevuto un segnale CTRL + C, il gestore di controllo restituisce **true**, a indicare che ha gestito il segnale.</span><span class="sxs-lookup"><span data-stu-id="3fb75-106">When a CTRL+C signal is received, the control handler returns **TRUE**, indicating that it has handled the signal.</span></span> <span data-ttu-id="3fb75-107">Questa operazione impedisce la chiamata di altri gestori del controllo.</span><span class="sxs-lookup"><span data-stu-id="3fb75-107">Doing this prevents other control handlers from being called.</span></span>

<span data-ttu-id="3fb75-108">Quando viene ricevuto un segnale di \*\* \_ \_ evento di chiusura CTRL\*\* , il gestore di controllo restituisce **true** e il processo viene terminato.</span><span class="sxs-lookup"><span data-stu-id="3fb75-108">When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.</span></span>

<span data-ttu-id="3fb75-109">Quando viene ricevuto un evento \*\*CTRL \_ break \_ \*\*, un evento di \*\* \_ disconnessione \_ \*\*CTRL o un segnale di **arresto dell' \_ \_ evento CTRL** , il gestore di controllo restituisce **false**.</span><span class="sxs-lookup"><span data-stu-id="3fb75-109">When a **CTRL\_BREAK\_EVENT**, **CTRL\_LOGOFF\_EVENT**, or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE**.</span></span> <span data-ttu-id="3fb75-110">Questa operazione fa sì che il segnale venga passato alla funzione del gestore di controllo successiva.</span><span class="sxs-lookup"><span data-stu-id="3fb75-110">Doing this causes the signal to be passed to the next control handler function.</span></span> <span data-ttu-id="3fb75-111">Se non sono stati registrati altri gestori di controllo o se nessuno dei gestori registrati restituisce **true**, verrà utilizzato il gestore predefinito, con conseguente terminazione del processo.</span><span class="sxs-lookup"><span data-stu-id="3fb75-111">If no other control handlers have been registered or none of the registered handlers returns **TRUE**, the default handler will be used, resulting in the process being terminated.</span></span>

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include "pch.h"

#include <windows.h> 
#include <stdio.h> 

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal. 
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit. 
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler. 
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```

 

 




