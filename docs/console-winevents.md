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
# <a name="console-winevents"></a><span data-ttu-id="7efb4-105">WinEvents console</span><span class="sxs-lookup"><span data-stu-id="7efb4-105">Console WinEvents</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7efb4-106">WinEvents fanno parte del Framework legacy di **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** .</span><span class="sxs-lookup"><span data-stu-id="7efb4-106">WinEvents are part of the legacy **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** framework.</span></span> <span data-ttu-id="7efb4-107">Lo sviluppo con questi eventi è fortemente sconsigliato rispetto al Framework di **[automazione interfaccia utente Microsoft](/windows/win32/winauto/entry-uiauto-win32)** , che fornisce una suite di interfacce più solida e completa per le applicazioni di accessibilità e automazione per interagire con la console.</span><span class="sxs-lookup"><span data-stu-id="7efb4-107">Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console.</span></span> 

> [!WARNING]
> <span data-ttu-id="7efb4-108">La registrazione per questi eventi è un'attività globale che avrà un notevole effetto sulle prestazioni di tutte le applicazioni da riga di comando in esecuzione su un sistema nello stesso momento, inclusi i servizi e le utilità in background.</span><span class="sxs-lookup"><span data-stu-id="7efb4-108">Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities.</span></span> <span data-ttu-id="7efb4-109">Il Framework di **automazione interfaccia utente Microsoft** è specifico della sessione della console ed è in questo limite.</span><span class="sxs-lookup"><span data-stu-id="7efb4-109">The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.</span></span>

<span data-ttu-id="7efb4-110">Le costanti di evento seguenti vengono usate nel parametro *Event* della funzione di callback [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) .</span><span class="sxs-lookup"><span data-stu-id="7efb4-110">The following event constants are used in the *event* parameter of the [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) callback function.</span></span> <span data-ttu-id="7efb4-111">Per ulteriori informazioni, vedere [winEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="7efb4-111">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

| <span data-ttu-id="7efb4-112">Costante/valore</span><span class="sxs-lookup"><span data-stu-id="7efb4-112">Constant/value</span></span> | <span data-ttu-id="7efb4-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7efb4-113">Description</span></span> |
|-|-|
| <span data-ttu-id="7efb4-114">**EVENT_CONSOLE_CARET** 0x4001</span><span class="sxs-lookup"><span data-stu-id="7efb4-114">**EVENT_CONSOLE_CARET** 0x4001</span></span> | <span data-ttu-id="7efb4-115">Il punto di inserimento della console è stato spostato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-115">The console caret has moved.</span></span> <span data-ttu-id="7efb4-116">Il parametro *idObject* è uno o più dei valori seguenti: **CONSOLE_CARET_SELECTION** o **CONSOLE_CARET_VISIBLE**.</span><span class="sxs-lookup"><span data-stu-id="7efb4-116">The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE**.</span></span> <span data-ttu-id="7efb4-117">Il parametro *idChild* è una struttura **[Coord](coord-str.md)** che specifica la posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="7efb4-117">The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position.</span></span> |
| <span data-ttu-id="7efb4-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span><span class="sxs-lookup"><span data-stu-id="7efb4-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span></span> | <span data-ttu-id="7efb4-119">Un processo console è stato terminato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-119">A console process has exited.</span></span> <span data-ttu-id="7efb4-120">Il parametro *idObject* contiene l'identificatore di processo del processo terminato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-120">The *idObject* parameter contains the process identifier of the terminated process.</span></span> |
| <span data-ttu-id="7efb4-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span><span class="sxs-lookup"><span data-stu-id="7efb4-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span></span> | <span data-ttu-id="7efb4-122">Il layout della console è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-122">The console layout has changed.</span></span> |
| <span data-ttu-id="7efb4-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span><span class="sxs-lookup"><span data-stu-id="7efb4-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span></span> | <span data-ttu-id="7efb4-124">È stato avviato un nuovo processo console.</span><span class="sxs-lookup"><span data-stu-id="7efb4-124">A new console process has started.</span></span> <span data-ttu-id="7efb4-125">Il parametro *idObject* contiene l'identificatore di processo del processo appena creato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-125">The *idObject* parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="7efb4-126">Se l'applicazione è un'applicazione a 16 bit, il parametro *idChild* è **CONSOLE_APPLICATION_16BIT** e *idObject* è l'identificatore del processo della sessione NTVDM associata alla console.</span><span class="sxs-lookup"><span data-stu-id="7efb4-126">If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console.</span></span> |
|<span data-ttu-id="7efb4-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span><span class="sxs-lookup"><span data-stu-id="7efb4-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span></span> | <span data-ttu-id="7efb4-128">Più di un carattere è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-128">More than one character has changed.</span></span> <span data-ttu-id="7efb4-129">Il parametro  *idObject* è una struttura **[Coord](coord-str.md)** che specifica l'inizio dell'area modificata.</span><span class="sxs-lookup"><span data-stu-id="7efb4-129">The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region.</span></span> <span data-ttu-id="7efb4-130">Il parametro *idChild* è una struttura **Coord** che specifica la fine dell'area modificata.</span><span class="sxs-lookup"><span data-stu-id="7efb4-130">The *idChild* parameter is a **COORD** structure that specifies the end of the changed region.</span></span> |
|<span data-ttu-id="7efb4-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span><span class="sxs-lookup"><span data-stu-id="7efb4-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span></span> | <span data-ttu-id="7efb4-132">Lo scorrimento della console è stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="7efb4-132">The console has scrolled.</span></span> <span data-ttu-id="7efb4-133">Il parametro *idObject* è la distanza orizzontale con cui è stato eseguito lo scorrimento della console.</span><span class="sxs-lookup"><span data-stu-id="7efb4-133">The *idObject* parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="7efb4-134">Il parametro *idChild* è la distanza verticale con cui è stato eseguito lo scorrimento della console.</span><span class="sxs-lookup"><span data-stu-id="7efb4-134">The *idChild* parameter is the vertical distance the console has scrolled.</span></span> |
|<span data-ttu-id="7efb4-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span><span class="sxs-lookup"><span data-stu-id="7efb4-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span></span> | <span data-ttu-id="7efb4-136">Un singolo carattere è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-136">A single character has changed.</span></span> <span data-ttu-id="7efb4-137">Il parametro *idObject* è una struttura **[Coord](coord-str.md)** che specifica il carattere che è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="7efb4-137">The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed.</span></span> <span data-ttu-id="7efb4-138">Il parametro *idChild* specifica il carattere nella parola bassa e gli **[attributi carattere](console-screen-buffers.md#character-attributes)** nella parola alta.</span><span class="sxs-lookup"><span data-stu-id="7efb4-138">The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7efb4-139">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7efb4-139">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7efb4-140">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7efb4-140">Minimum supported client</span></span> | <span data-ttu-id="7efb4-141">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="7efb4-141">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7efb4-142">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="7efb4-142">Minimum supported server</span></span> | <span data-ttu-id="7efb4-143">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="7efb4-143">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7efb4-144">Intestazione</span><span class="sxs-lookup"><span data-stu-id="7efb4-144">Header</span></span> | <span data-ttu-id="7efb4-145">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="7efb4-145">Winuser.h</span></span> |