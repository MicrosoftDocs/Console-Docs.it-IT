---
title: Diritti di accesso e sicurezza del buffer della console
description: Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console. Per altre informazioni sulla sicurezza, vedere modello di controllo di accesso.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060161"
---
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="2a8fa-105">Diritti di accesso e sicurezza del buffer della console</span><span class="sxs-lookup"><span data-stu-id="2a8fa-105">Console Buffer Security and Access Rights</span></span>


<span data-ttu-id="2a8fa-106">Il modello di sicurezza di Windows consente di controllare l'accesso ai buffer di input della console e ai buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="2a8fa-107">Per altre informazioni sulla sicurezza, vedere [modello di controllo di accesso](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span><span class="sxs-lookup"><span data-stu-id="2a8fa-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

<span data-ttu-id="2a8fa-108">È possibile specificare un [descrittore di sicurezza](https://msdn.microsoft.com/library/windows/desktop/aa379563) per i buffer di input della console e dello schermo della console quando si chiama la funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="2a8fa-108">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="2a8fa-109">Se si specifica **null**, l'oggetto ottiene un descrittore di sicurezza predefinito.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-109">If you specify **NULL**, the object gets a default security descriptor.</span></span> <span data-ttu-id="2a8fa-110">Gli ACL nel descrittore di sicurezza predefinito per un buffer della console provengono dal token primario o di rappresentazione del creatore.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-110">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="2a8fa-111">Gli handle restituiti da [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)e [**GetStdHandle**](getstdhandle.md) dispongono dei diritti di accesso di \*\* \_ lettura\*\* e \*\* \_ scrittura\*\* generici.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-111">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="2a8fa-112">I diritti di accesso validi includono i [diritti di accesso](https://msdn.microsoft.com/library/windows/desktop/aa446632)generico di \*\* \_ lettura\*\* e \*\* \_ scrittura\*\* generica.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-112">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>


| <span data-ttu-id="2a8fa-113">valore</span><span class="sxs-lookup"><span data-stu-id="2a8fa-113">Value</span></span>                            | <span data-ttu-id="2a8fa-114">Significato</span><span class="sxs-lookup"><span data-stu-id="2a8fa-114">Meaning</span></span>                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2a8fa-115">**Generic \_ LETTURA** (0x80000000L)</span><span class="sxs-lookup"><span data-stu-id="2a8fa-115">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="2a8fa-116">Richiede l'accesso in lettura al buffer dello schermo della console, consentendo al processo di leggere i dati dal buffer.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-116">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="2a8fa-117">**Generic \_ SCRITTURA** (0x40000000L)</span><span class="sxs-lookup"><span data-stu-id="2a8fa-117">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="2a8fa-118">Richiede l'accesso in scrittura al buffer dello schermo della console, consentendo al processo di scrivere i dati nel buffer.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-118">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |










