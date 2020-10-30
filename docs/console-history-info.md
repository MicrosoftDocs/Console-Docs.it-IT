---
title: Struttura CONSOLE_HISTORY_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_HISTORY_INFO, che contiene informazioni sulla cronologia della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039219"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="34996-104">Struttura delle informazioni della \_ cronologia della console \_</span><span class="sxs-lookup"><span data-stu-id="34996-104">CONSOLE\_HISTORY\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="34996-105">Contiene informazioni sulla cronologia della console.</span><span class="sxs-lookup"><span data-stu-id="34996-105">Contains information about the console history.</span></span>

## <a name="syntax"></a><span data-ttu-id="34996-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="34996-106">Syntax</span></span>

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a><span data-ttu-id="34996-107">Members</span><span class="sxs-lookup"><span data-stu-id="34996-107">Members</span></span>

<span data-ttu-id="34996-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="34996-108">**cbSize**</span></span>  
<span data-ttu-id="34996-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="34996-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="34996-110">Impostare questo membro su `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="34996-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="34996-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="34996-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="34996-112">Il numero di comandi conservati in ogni buffer della cronologia.</span><span class="sxs-lookup"><span data-stu-id="34996-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="34996-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="34996-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="34996-114">Numero di buffer di cronologia conservati per questo processo della console.</span><span class="sxs-lookup"><span data-stu-id="34996-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="34996-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="34996-115">**dwFlags**</span></span>  
<span data-ttu-id="34996-116">Questo parametro può essere zero o il valore seguente.</span><span class="sxs-lookup"><span data-stu-id="34996-116">This parameter can be zero or the following value.</span></span>

| <span data-ttu-id="34996-117">Valore</span><span class="sxs-lookup"><span data-stu-id="34996-117">Value</span></span> | <span data-ttu-id="34996-118">Significato</span><span class="sxs-lookup"><span data-stu-id="34996-118">Meaning</span></span> |
|-|-|
| <span data-ttu-id="34996-119">**HISTORY_NO_DUP_FLAG** 0x1</span><span class="sxs-lookup"><span data-stu-id="34996-119">**HISTORY_NO_DUP_FLAG** 0x1</span></span> | <span data-ttu-id="34996-120">Le voci duplicate non verranno archiviate nel buffer della cronologia.</span><span class="sxs-lookup"><span data-stu-id="34996-120">Duplicate entries will not be stored in the history buffer.</span></span>

## <a name="requirements"></a><span data-ttu-id="34996-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="34996-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="34996-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="34996-122">Minimum supported client</span></span> | <span data-ttu-id="34996-123">\[Solo app desktop di Windows Vista\]</span><span class="sxs-lookup"><span data-stu-id="34996-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="34996-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="34996-124">Minimum supported server</span></span> | <span data-ttu-id="34996-125">\[Solo app desktop Windows Server 2008\]</span><span class="sxs-lookup"><span data-stu-id="34996-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="34996-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="34996-126">Header</span></span> | <span data-ttu-id="34996-127">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="34996-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="34996-128">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="34996-128">See also</span></span>

[<span data-ttu-id="34996-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="34996-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="34996-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="34996-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
