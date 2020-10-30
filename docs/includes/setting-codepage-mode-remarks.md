---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037034"
---
Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console. Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema. Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](../setconsolecp.md) o [**SetConsoleOutputCP**](../setconsoleoutputcp.md) . I consumer legacy possono anche usare i comandi **chcp** o **mode con CP SELECT =** , ma non è consigliato per il nuovo sviluppo.