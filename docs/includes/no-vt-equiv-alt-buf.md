---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039135"
---
> [!TIP]
> <span data-ttu-id="7d062-101">Questa API non è consigliata, ma ha un **[terminale virtuale](../console-virtual-terminal-sequences.md)** approssimato equivalente nella sequenza di **[buffer dello schermo alternativa](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** .</span><span class="sxs-lookup"><span data-stu-id="7d062-101">This API is not recommended but it does have an approximate **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent in the **[alternate screen buffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** sequence.</span></span> <span data-ttu-id="7d062-102">L'impostazione del _buffer dello schermo alternativo_ può fornire un'applicazione con uno spazio separato e isolato per il disegno nel corso del runtime di sessione, mantenendo al tempo stesso il contenuto visualizzato dall'invoker dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7d062-102">Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker.</span></span> <span data-ttu-id="7d062-103">Questo mantiene le informazioni di disegno per il ripristino semplice all'uscita del processo.</span><span class="sxs-lookup"><span data-stu-id="7d062-103">This maintains that drawing information for simple restoration on process exit.</span></span>
