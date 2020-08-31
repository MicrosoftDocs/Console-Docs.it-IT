---
title: Scorrimento del contenuto di un buffer dello schermo
description: La funzione ScrollConsoleScreenBuffer sposta un blocco di celle di tipo carattere da una parte di un buffer dello schermo a un'altra parte dello stesso buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- base.scrolling\_a\_screen\_buffer\_s\_contents
- consoles.scrolling\_a\_screen\_buffer\_s\_contents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
ms.openlocfilehash: a25e9ad7a27977e6dbfcf58de2cf7a250ffd6c4d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060353"
---
# <a name="scrolling-a-screen-buffers-contents"></a>Scorrimento del contenuto di un buffer dello schermo


La funzione [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) sposta un blocco di celle di tipo carattere da una parte di un buffer dello schermo a un'altra parte dello stesso buffer dello schermo. La funzione specifica le celle in alto a sinistra e in basso a destra del rettangolo di origine da spostare e le coordinate di destinazione della nuova posizione per la cella in alto a sinistra. I dati di tipo carattere e colore nelle celle di origine vengono spostati nella nuova posizione e le celle lasciate vuote dallo spostamento vengono compilate con il carattere e il colore specificati. Se viene specificato un rettangolo di ritaglio, le celle esterne a tale rettangolo rimangono invariate.

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) può essere usato per eliminare una riga specificando le coordinate della prima cella nella riga come coordinate di destinazione e specificando un rettangolo di scorrimento che include tutte le righe sotto la riga.

Nell'esempio seguente viene illustrato l'utilizzo di un rettangolo di ridimensionamento per scorrere solo le ultime 15 righe del buffer dello schermo della console. Le righe nel rettangolo specificato vengono spostate verso l'alto di una riga alla volta e la riga superiore del blocco viene eliminata. Il contenuto del buffer dello schermo della console all'esterno del rettangolo di ritaglio viene lasciato invariato.

```C
#include <windows.h>
#include <stdio.h>

int main( void )
{
    HANDLE hStdout; 
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctScrollRect, srctClipRect; 
    CHAR_INFO chiFill; 
    COORD coordDest; 
    int i;

    printf("\nPrinting 20 lines for reference. ");
    printf("Notice that line 6 is discarded during scrolling.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if (hStdout == INVALID_HANDLE_VALUE) 
    {
        printf("GetStdHandle failed with %d\n", GetLastError()); 
        return 1;
    }
 
    // Get the screen buffer size. 
 
    if (!GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo failed %d\n", GetLastError()); 
        return 1;
    }
 
    // The scrolling rectangle is the bottom 15 rows of the 
    // screen buffer. 
 
    srctScrollRect.Top = csbiInfo.dwSize.Y - 16; 
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - 1; 
    srctScrollRect.Left = 0; 
    srctScrollRect.Right = csbiInfo.dwSize.X - 1; 
 
    // The destination for the scroll rectangle is one row up. 
 
    coordDest.X = 0; 
    coordDest.Y = csbiInfo.dwSize.Y - 17; 
 
    // The clipping rectangle is the same as the scrolling rectangle. 
    // The destination row is left unchanged. 
 
    srctClipRect = srctScrollRect; 
 
    // Fill the bottom row with green blanks. 
 
    chiFill.Attributes = BACKGROUND_GREEN | FOREGROUND_RED; 
    chiFill.Char.AsciiChar = (char)' '; 
 
    // Scroll up one line. 
 
    if(!ScrollConsoleScreenBuffer(  
        hStdout,         // screen buffer handle 
        &srctScrollRect, // scrolling rectangle 
        &srctClipRect,   // clipping rectangle 
        coordDest,       // top left destination cell 
        &chiFill))       // fill character and color
    {
        printf("ScrollConsoleScreenBuffer failed %d\n", GetLastError()); 
        return 1;
    }
return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>Argomenti correlati


[Scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md)

[Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)

 

 




