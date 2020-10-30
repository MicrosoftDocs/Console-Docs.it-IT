---
title: GetConsoleWindow (funzione)
description: Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038809"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="5ac9c-104">GetConsoleWindow (funzione)</span><span class="sxs-lookup"><span data-stu-id="5ac9c-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5ac9c-105">Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ac9c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5ac9c-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="5ac9c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5ac9c-107">Parameters</span></span>

<span data-ttu-id="5ac9c-108">Questa funzione non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ac9c-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5ac9c-109">Return value</span></span>

<span data-ttu-id="5ac9c-110">Il valore restituito è un handle per la finestra utilizzata dalla console associata al processo chiamante oppure **null** se tale console associata non è presente.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ac9c-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="5ac9c-111">Remarks</span></span>

<span data-ttu-id="5ac9c-112">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="5ac9c-113">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="5ac9c-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="5ac9c-114">Per un'applicazione ospitata all'interno di una sessione [**pseudoconsole**](pseudoconsoles.md) , questa funzione restituisce un handle di finestra solo per la coda dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="5ac9c-115">La finestra associata non viene visualizzata localmente perché _pseudoconsole_ esegue la serializzazione di tutte le azioni in un flusso per la presentazione in un'altra finestra del terminale altrove.</span><span class="sxs-lookup"><span data-stu-id="5ac9c-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ac9c-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5ac9c-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5ac9c-117">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5ac9c-117">Minimum supported client</span></span> | <span data-ttu-id="5ac9c-118">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="5ac9c-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5ac9c-119">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="5ac9c-119">Minimum supported server</span></span> | <span data-ttu-id="5ac9c-120">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="5ac9c-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5ac9c-121">Intestazione</span><span class="sxs-lookup"><span data-stu-id="5ac9c-121">Header</span></span> | <span data-ttu-id="5ac9c-122">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5ac9c-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5ac9c-123">Libreria</span><span class="sxs-lookup"><span data-stu-id="5ac9c-123">Library</span></span> | <span data-ttu-id="5ac9c-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5ac9c-124">Kernel32.lib</span></span> |
| <span data-ttu-id="5ac9c-125">DLL</span><span class="sxs-lookup"><span data-stu-id="5ac9c-125">DLL</span></span> | <span data-ttu-id="5ac9c-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5ac9c-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="5ac9c-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5ac9c-127">See also</span></span>

[<span data-ttu-id="5ac9c-128">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="5ac9c-128">Console Functions</span></span>](console-functions.md)
