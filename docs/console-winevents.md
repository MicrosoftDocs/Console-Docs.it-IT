---
title: WinEvents console
description: Le costanti di evento seguenti vengono usate nel parametro event della funzione di callback WinEventProc. Per ulteriori informazioni, vedere WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2cd48537ef79f09024a55b32a98e2aa85fe76f62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358051"
---
# <a name="console-winevents"></a>WinEvents console

> [!IMPORTANT]
> WinEvents fanno parte del Framework legacy di **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** . Lo sviluppo con questi eventi è fortemente sconsigliato rispetto al Framework di **[automazione interfaccia utente Microsoft](/windows/win32/winauto/entry-uiauto-win32)** , che fornisce una suite di interfacce più solida e completa per le applicazioni di accessibilità e automazione per interagire con la console. 

> [!WARNING]
> La registrazione per questi eventi è un'attività globale che avrà un notevole effetto sulle prestazioni di tutte le applicazioni da riga di comando in esecuzione su un sistema nello stesso momento, inclusi i servizi e le utilità in background. Il Framework di **automazione interfaccia utente Microsoft** è specifico della sessione della console ed è in questo limite.

Le costanti di evento seguenti vengono usate nel parametro *Event* della funzione di callback [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) . Per ulteriori informazioni, vedere [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

| Costante/valore | Descrizione |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | Il punto di inserimento della console è stato spostato. Il parametro *idObject* è uno o più dei valori seguenti: **CONSOLE_CARET_SELECTION** o **CONSOLE_CARET_VISIBLE**. Il parametro *idChild* è una struttura **[Coord](coord-str.md)** che specifica la posizione corrente del cursore. |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | Un processo console è stato terminato. Il parametro *idObject* contiene l'identificatore di processo del processo terminato. |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | Il layout della console è stato modificato. |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | È stato avviato un nuovo processo console. Il parametro *idObject* contiene l'identificatore di processo del processo appena creato. Se l'applicazione è un'applicazione a 16 bit, il parametro *idChild* è **CONSOLE_APPLICATION_16BIT** e *idObject* è l'identificatore del processo della sessione NTVDM associata alla console. |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | Più di un carattere è stato modificato. Il parametro  *idObject* è una struttura **[Coord](coord-str.md)** che specifica l'inizio dell'area modificata. Il parametro *idChild* è una struttura **Coord** che specifica la fine dell'area modificata. |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | Lo scorrimento della console è stato eseguito. Il parametro *idObject* è la distanza orizzontale con cui è stato eseguito lo scorrimento della console. Il parametro *idChild* è la distanza verticale con cui è stato eseguito lo scorrimento della console. |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | Un singolo carattere è stato modificato. Il parametro *idObject* è una struttura **[Coord](coord-str.md)** che specifica il carattere che è stato modificato. Il parametro *idChild* specifica il carattere nella parola bassa e gli **[attributi carattere](console-screen-buffers.md#character-attributes)** nella parola alta. |

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | Winuser. h |