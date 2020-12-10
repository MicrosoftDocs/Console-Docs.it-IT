---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037034"
---
Questa funzione usa i caratteri Unicode o i caratteri a 8 bit dalla tabella codici corrente della console. Inizialmente il valore predefinito della tabella codici della console è la tabella codici OEM del sistema. Per modificare la tabella codici della console usare le funzioni [**SetConsoleCP**](../setconsolecp.md) o [**SetConsoleOutputCP**](../setconsoleoutputcp.md). I consumer legacy possono anche usare i comandi **chcp** o **mode con cp select=** ma non è consigliabile per il nuovo sviluppo.