---
title: Struttura CONSOLE_HISTORY_INFO
description: Vedere le informazioni di riferimento sulla struttura CONSOLE_HISTORY_INFO, che contiene informazioni sulla cronologia della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060460"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="4758e-104">Struttura delle informazioni della \_ cronologia della console \_</span><span class="sxs-lookup"><span data-stu-id="4758e-104">CONSOLE\_HISTORY\_INFO structure</span></span>


<span data-ttu-id="4758e-105">Contiene informazioni sulla cronologia della console.</span><span class="sxs-lookup"><span data-stu-id="4758e-105">Contains information about the console history.</span></span>

<a name="syntax"></a><span data-ttu-id="4758e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4758e-106">Syntax</span></span>
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a><span data-ttu-id="4758e-107">Membri</span><span class="sxs-lookup"><span data-stu-id="4758e-107">Members</span></span>
-------

<span data-ttu-id="4758e-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="4758e-108">**cbSize**</span></span>  
<span data-ttu-id="4758e-109">Dimensioni, in byte, della struttura.</span><span class="sxs-lookup"><span data-stu-id="4758e-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="4758e-110">Impostare questo membro su `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="4758e-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="4758e-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="4758e-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="4758e-112">Il numero di comandi conservati in ogni buffer della cronologia.</span><span class="sxs-lookup"><span data-stu-id="4758e-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="4758e-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="4758e-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="4758e-114">Numero di buffer di cronologia conservati per questo processo della console.</span><span class="sxs-lookup"><span data-stu-id="4758e-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="4758e-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="4758e-115">**dwFlags**</span></span>  
<span data-ttu-id="4758e-116">Questo parametro può essere zero o il valore seguente.</span><span class="sxs-lookup"><span data-stu-id="4758e-116">This parameter can be zero or the following value.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="4758e-117">valore</span><span class="sxs-lookup"><span data-stu-id="4758e-117">Value</span></span></th>
<th><span data-ttu-id="4758e-118">Significato</span><span class="sxs-lookup"><span data-stu-id="4758e-118">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="4758e-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span><span class="sxs-lookup"><span data-stu-id="4758e-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span></span></td>
<td><p><span data-ttu-id="4758e-120">Le voci duplicate non verranno archiviate nel buffer della cronologia.</span><span class="sxs-lookup"><span data-stu-id="4758e-120">Duplicate entries will not be stored in the history buffer.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="4758e-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4758e-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4758e-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4758e-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4758e-123">Windows Vista [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="4758e-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4758e-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4758e-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4758e-125">Windows Server 2008 [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="4758e-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4758e-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4758e-126">Header</span></span></p></td>
<td><span data-ttu-id="4758e-127">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4758e-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4758e-128"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4758e-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4758e-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="4758e-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="4758e-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="4758e-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




