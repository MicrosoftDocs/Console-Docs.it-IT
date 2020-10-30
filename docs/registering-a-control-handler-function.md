---
title: Registrazione di una funzione gestore di controllo
description: Questo è un esempio della funzione SetConsoleCtrlHandler usata per installare un gestore di controllo.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: 4142f4f0871bd11a56085324195702ab47301227
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039449"
---
# <a name="registering-a-control-handler-function"></a>Registrazione di una funzione gestore di controllo

Questo è un esempio della funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) usata per installare un gestore di controllo.

Quando viene ricevuto un segnale CTRL + C, il gestore di controllo restituisce **true** , a indicare che ha gestito il segnale. Questa operazione impedisce la chiamata di altri gestori del controllo.

Quando viene ricevuto un segnale di **\_ \_ evento di chiusura CTRL** , il gestore di controllo restituisce **true** e il processo viene terminato.

Quando viene ricevuto un evento **CTRL \_ break \_** , un evento di **\_ disconnessione \_** CTRL o un segnale di **arresto dell' \_ \_ evento CTRL** , il gestore di controllo restituisce **false** . Questa operazione fa sì che il segnale venga passato alla funzione del gestore di controllo successiva. Se non sono stati registrati altri gestori di controllo o se nessuno dei gestori registrati restituisce **true** , verrà utilizzato il gestore predefinito, con conseguente terminazione del processo.

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
