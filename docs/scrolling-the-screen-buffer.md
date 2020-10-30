---
title: Scorrimento del buffer dello schermo
description: Viene descritto come la finestra della console Visualizza una parte del buffer dello schermo attivo.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 1582b6232461469e10048ed8711c766a6821264f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037599"
---
# <a name="scrolling-the-screen-buffer"></a>Scorrimento del buffer dello schermo

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

La finestra della console Visualizza una parte del buffer dello schermo attivo. Ogni buffer della schermata mantiene il proprio rettangolo della finestra corrente che specifica le coordinate delle celle di caratteri in alto a sinistra e in basso a destra da visualizzare nella finestra della console. Per determinare il rettangolo della finestra corrente di un buffer dello schermo, usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Quando viene creato un buffer dello schermo, l'angolo superiore sinistro della finestra si trova nell'angolo superiore sinistro del buffer dello schermo della console in (0,0).

Il rettangolo della finestra può essere modificato in modo da visualizzare diverse parti del buffer dello schermo della console. Il rettangolo della finestra di un buffer dello schermo può variare nelle situazioni seguenti:

- Quando [**SetConsoleWindowInfo**](setconsolewindowinfo.md) viene chiamato per specificare un nuovo rettangolo della finestra, scorre la visualizzazione del buffer dello schermo della console modificando la posizione del rettangolo della finestra senza modificare le dimensioni della finestra. Per esempi di scorrimento del contenuto della finestra, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).

  ![Panoramica della finestra buffer dello schermo intorno a un buffer di grandi dimensioni](images/cscon-01.png)

- Quando si usa la funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) per scrivere in un buffer dello schermo con wrapping alla modalità di output End-of-line (EOL) abilitata, il rettangolo della finestra viene spostato automaticamente, quindi il cursore viene sempre visualizzato.
- Quando la funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) specifica una nuova posizione del cursore all'esterno dei limiti del rettangolo della finestra corrente, il rettangolo della finestra viene spostato automaticamente per visualizzare il cursore.
- Quando l'utente modifica la dimensione della finestra della console o usa le barre di scorrimento della finestra, il rettangolo della finestra del buffer dello schermo attivo può cambiare. Questa modifica non viene segnalata come un evento di ridimensionamento della finestra nel buffer di input.

In ognuna di queste situazioni, il rettangolo della finestra si sposta per visualizzare una parte diversa del buffer dello schermo della console, ma il contenuto del buffer dello schermo della console rimane nella stessa posizione. Le situazioni seguenti possono causare lo spostamento del contenuto del buffer dello schermo della console:

- Quando viene chiamata la funzione [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) , viene copiato un blocco rettangolare da una parte di un buffer dello schermo a un altro.
- Quando si usa [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) per scrivere in un buffer dello schermo con wrapping in modalità di output EOL abilitata, il contenuto del buffer dello schermo della console scorre automaticamente quando viene rilevata la fine del buffer dello schermo della console. Questo scorrimento elimina la riga superiore del buffer dello schermo della console.

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) specifica il rettangolo del buffer dello schermo della console spostato e le nuove coordinate in alto a sinistra in cui viene copiato il rettangolo. Questa funzione può scorrere una parte o l'intero contenuto del buffer dello schermo della console.

Nella figura viene mostrata un'operazione [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) che consente di scorrere l'intero contenuto del buffer dello schermo della console per più righe. Il contenuto delle prime righe viene eliminato e le righe in basso vengono riempite con il carattere e il colore specificati.

![finestra buffer dello scorrimento della finestra del contenuto fuori dalla parte superiore per eliminare](images/cscon-02.png)

Gli effetti di [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) possono essere limitati specificando un rettangolo di ritaglio facoltativo, in modo che il contenuto del buffer dello schermo della console all'esterno del rettangolo di ritaglio sia invariato. L'effetto del ritaglio consiste nel creare una finestra secondaria (rettangolo di ritaglio) il cui contenuto viene spostato senza influire sul resto del buffer dello schermo della console. Per un esempio che usa **ScrollConsoleScreenBuffer** , vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).
