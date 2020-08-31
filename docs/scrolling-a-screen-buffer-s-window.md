---
title: Scorrimento della finestra di un buffer dello schermo
description: La funzione SetConsoleWindowInfo può essere usata per scorrere il contenuto di un buffer dello schermo nella finestra della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- base.scrolling\_a\_screen\_buffer\_s\_window
- consoles.scrolling\_a\_screen\_buffer\_s\_window
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
ms.openlocfilehash: 02d39574e38c277bc7637816cd8e3866278a87e6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060380"
---
# <a name="scrolling-a-screen-buffers-window"></a><span data-ttu-id="53ea2-104">Scorrimento della finestra di un buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="53ea2-104">Scrolling a Screen Buffer's Window</span></span>


<span data-ttu-id="53ea2-105">La funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) può essere usata per scorrere il contenuto di un buffer dello schermo nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="53ea2-105">The [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function can be used to scroll the contents of a screen buffer in the console window.</span></span> <span data-ttu-id="53ea2-106">Questa funzione può anche modificare le dimensioni della finestra.</span><span class="sxs-lookup"><span data-stu-id="53ea2-106">This function can also change the window size.</span></span> <span data-ttu-id="53ea2-107">La funzione può specificare i nuovi angoli superiore sinistro e inferiore destro della finestra del buffer dello schermo della console come coordinate assolute del buffer dello schermo o specificare le modifiche dalle coordinate della finestra corrente.</span><span class="sxs-lookup"><span data-stu-id="53ea2-107">The function can either specify the new upper left and lower right corners of the console screen buffer's window as absolute screen buffer coordinates or specify the changes from the current window coordinates.</span></span> <span data-ttu-id="53ea2-108">La funzione ha esito negativo se le coordinate della finestra specificate si trovano all'esterno dei limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="53ea2-108">The function fails if the specified window coordinates are outside the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="53ea2-109">Nell'esempio seguente viene scorre la visualizzazione del buffer dello schermo della console modificando le coordinate della finestra restituite dalla funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="53ea2-109">The following example scrolls the view of the console screen buffer up by modifying the window coordinates returned by the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="53ea2-110">La `ScrollByAbsoluteCoord` funzione illustra come specificare coordinate assolute, mentre la `ScrollByRelativeCoord` funzione dimostra come specificare coordinate relative.</span><span class="sxs-lookup"><span data-stu-id="53ea2-110">The `ScrollByAbsoluteCoord` function demonstrates how to specify absolute coordinates, while the `ScrollByRelativeCoord` function demonstrates how to specify relative coordinates.</span></span>

```C
#include <windows.h>
#include <stdio.h>
#include <conio.h>

HANDLE hStdout; 

int ScrollByAbsoluteCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 
 
    // Get the current screen buffer size and window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Set srctWindow to the current window size and location. 
 
    srctWindow = csbiInfo.srWindow; 
 
    // Check whether the window is too close to the screen buffer top
 
    if ( srctWindow.Top >= iRows ) 
    { 
        srctWindow.Top -= (SHORT)iRows;     // move top up
        srctWindow.Bottom -= (SHORT)iRows;  // move bottom up

        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   TRUE,             // absolute coordinates 
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int ScrollByRelativeCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 

    // Get the current screen buffer window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Check whether the window is too close to the screen buffer top
 
    if (csbiInfo.srWindow.Top >= iRows) 
    { 
        srctWindow.Top =- (SHORT)iRows;     // move top up
        srctWindow.Bottom =- (SHORT)iRows;  // move bottom up 
        srctWindow.Left = 0;         // no change 
        srctWindow.Right = 0;        // no change 
 
        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   FALSE,            // relative coordinates
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int main( void )
{
    int i;

    printf("\nPrinting twenty lines, then scrolling up five lines.\n");
    printf("Press any key to scroll up ten lines; ");
    printf("then press another key to stop the demo.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if(ScrollByAbsoluteCoord(5))
        _getch();
    else return 0;

    if(ScrollByRelativeCoord(10))
        _getch();
    else return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span data-ttu-id="53ea2-111"><span id="related_topics"></span>Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="53ea2-111"><span id="related_topics"></span>Related topics</span></span>


[<span data-ttu-id="53ea2-112">Scorrimento del contenuto di un buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="53ea2-112">Scrolling a Screen Buffer's Contents</span></span>](scrolling-a-screen-buffer-s-contents.md)

[<span data-ttu-id="53ea2-113">Scorrimento del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="53ea2-113">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

 

 




