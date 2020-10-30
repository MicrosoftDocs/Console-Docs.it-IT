---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039135"
---
> [!TIP]
> Questa API non è consigliata, ma ha un **[terminale virtuale](../console-virtual-terminal-sequences.md)** approssimato equivalente nella sequenza di **[buffer dello schermo alternativa](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** . L'impostazione del _buffer dello schermo alternativo_ può fornire un'applicazione con uno spazio separato e isolato per il disegno nel corso del runtime di sessione, mantenendo al tempo stesso il contenuto visualizzato dall'invoker dell'applicazione. Questo mantiene le informazioni di disegno per il ripristino semplice all'uscita del processo.
