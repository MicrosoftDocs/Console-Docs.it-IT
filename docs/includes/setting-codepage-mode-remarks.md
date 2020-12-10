---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037034"
---
<span data-ttu-id="c879b-101">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit dalla tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="c879b-101">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="c879b-102">Inizialmente il valore predefinito della tabella codici della console è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="c879b-102">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="c879b-103">Per modificare la tabella codici della console usare le funzioni [**SetConsoleCP**](../setconsolecp.md) o [**SetConsoleOutputCP**](../setconsoleoutputcp.md).</span><span class="sxs-lookup"><span data-stu-id="c879b-103">To change the console's code page, use the [**SetConsoleCP**](../setconsolecp.md) or [**SetConsoleOutputCP**](../setconsoleoutputcp.md) functions.</span></span> <span data-ttu-id="c879b-104">I consumer legacy possono anche usare i comandi **chcp** o **mode con cp select=** ma non è consigliabile per il nuovo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="c879b-104">Legacy consumers may also use the **chcp** or **mode con cp select=** commands, but it is not recommended for new development.</span></span>