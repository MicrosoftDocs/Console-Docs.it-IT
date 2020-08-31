---
title: Lettura e scrittura di blocchi di caratteri e attributi
description: La funzione ReadConsoleOutput copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer dello schermo della console in un buffer di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_reading\_and\_writing\_blocks\_of\_characters\_and\_attributes'
- base.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
- consoles.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: eaa57723-f003-4e90-8156-be8c3b42b912
ms.openlocfilehash: f7993979d358c46a6fb6f8411c52e8df50a1eed5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060361"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a><span data-ttu-id="02efc-104">Lettura e scrittura di blocchi di caratteri e attributi</span><span class="sxs-lookup"><span data-stu-id="02efc-104">Reading and Writing Blocks of Characters and Attributes</span></span>


<span data-ttu-id="02efc-105">La funzione [**ReadConsoleOutput**](readconsoleoutput.md) copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer dello schermo della console in un buffer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="02efc-105">The [**ReadConsoleOutput**](readconsoleoutput.md) function copies a rectangular block of character and color attribute data from a console screen buffer into a destination buffer.</span></span> <span data-ttu-id="02efc-106">La funzione considera il buffer di destinazione come una matrice bidimensionale di strutture di [\*\* \_ informazioni char\*\*](char-info-str.md) .</span><span class="sxs-lookup"><span data-stu-id="02efc-106">The function treats the destination buffer as a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures.</span></span> <span data-ttu-id="02efc-107">Analogamente, la funzione [**WriteConsoleOutput**](writeconsoleoutput.md) copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer di origine a un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="02efc-107">Similarly, the [**WriteConsoleOutput**](writeconsoleoutput.md) function copies a rectangular block of character and color attribute data from a source buffer to a console screen buffer.</span></span> <span data-ttu-id="02efc-108">Per ulteriori informazioni sulla lettura o la scrittura in blocchi rettangolari di celle del buffer dello schermo, vedere [metodi di input e output](input-and-output-methods.md).</span><span class="sxs-lookup"><span data-stu-id="02efc-108">For more information about reading from or writing to rectangular blocks of screen buffer cells, see [Input and Output Methods](input-and-output-methods.md).</span></span>

<span data-ttu-id="02efc-109">Nell'esempio seguente viene usata la funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) per creare un nuovo buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="02efc-109">The following example uses the [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function to create a new screen buffer.</span></span> <span data-ttu-id="02efc-110">Dopo che la funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) rende il buffer dello schermo attivo, viene copiato un blocco di caratteri e attributi di colore dalle prime due righe del buffer dello schermo stdout in un buffer temporaneo.</span><span class="sxs-lookup"><span data-stu-id="02efc-110">After the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function makes this the active screen buffer, a block of characters and color attributes is copied from the top two rows of the STDOUT screen buffer into a temporary buffer.</span></span> <span data-ttu-id="02efc-111">I dati vengono quindi copiati dal buffer temporaneo nel nuovo buffer dello schermo attivo.</span><span class="sxs-lookup"><span data-stu-id="02efc-111">The data is then copied from the temporary buffer into the new active screen buffer.</span></span> <span data-ttu-id="02efc-112">Al termine dell'applicazione con il nuovo buffer dello schermo, viene chiamato **SetConsoleActiveScreenBuffer** per ripristinare il buffer dello schermo stdout originale.</span><span class="sxs-lookup"><span data-stu-id="02efc-112">When the application is finished using the new screen buffer, it calls **SetConsoleActiveScreenBuffer** to restore the original STDOUT screen buffer.</span></span>

```C
#include <windows.h> 
#include <stdio.h>
 
int main(void) 
{ 
    HANDLE hStdout, hNewScreenBuffer; 
    SMALL_RECT srctReadRect; 
    SMALL_RECT srctWriteRect; 
    CHAR_INFO chiBuffer[160]; // [2][80]; 
    COORD coordBufSize; 
    COORD coordBufCoord; 
    BOOL fSuccess; 
 
    // Get a handle to the STDOUT screen buffer to copy from and 
    // create a new screen buffer to copy to. 
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 
    hNewScreenBuffer = CreateConsoleScreenBuffer( 
       GENERIC_READ |           // read/write access 
       GENERIC_WRITE, 
       FILE_SHARE_READ | 
       FILE_SHARE_WRITE,        // shared 
       NULL,                    // default security attributes 
       CONSOLE_TEXTMODE_BUFFER, // must be TEXTMODE 
       NULL);                   // reserved; must be NULL 
    if (hStdout == INVALID_HANDLE_VALUE || 
            hNewScreenBuffer == INVALID_HANDLE_VALUE) 
    {
        printf("CreateConsoleScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Make the new screen buffer the active screen buffer. 
 
    if (! SetConsoleActiveScreenBuffer(hNewScreenBuffer) ) 
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Set the source rectangle. 
 
    srctReadRect.Top = 0;    // top left: row 0, col 0 
    srctReadRect.Left = 0; 
    srctReadRect.Bottom = 1; // bot. right: row 1, col 79 
    srctReadRect.Right = 79; 
 
    // The temporary buffer size is 2 rows x 80 columns. 
 
    coordBufSize.Y = 2; 
    coordBufSize.X = 80; 
 
    // The top left destination cell of the temporary buffer is 
    // row 0, col 0. 
 
    coordBufCoord.X = 0; 
    coordBufCoord.Y = 0; 
 
    // Copy the block from the screen buffer to the temp. buffer. 
 
    fSuccess = ReadConsoleOutput( 
       hStdout,        // screen buffer to read from 
       chiBuffer,      // buffer to copy into 
       coordBufSize,   // col-row size of chiBuffer 
       coordBufCoord,  // top left dest. cell in chiBuffer 
       &srctReadRect); // screen buffer source rectangle 
    if (! fSuccess) 
    {
        printf("ReadConsoleOutput failed - (%d)\n", GetLastError()); 
        return 1;
    }
 
    // Set the destination rectangle. 
 
    srctWriteRect.Top = 10;    // top lt: row 10, col 0 
    srctWriteRect.Left = 0; 
    srctWriteRect.Bottom = 11; // bot. rt: row 11, col 79 
    srctWriteRect.Right = 79; 
 
    // Copy from the temporary buffer to the new screen buffer. 
 
    fSuccess = WriteConsoleOutput( 
        hNewScreenBuffer, // screen buffer to write to 
        chiBuffer,        // buffer to copy from 
        coordBufSize,     // col-row size of chiBuffer 
        coordBufCoord,    // top left src cell in chiBuffer 
        &srctWriteRect);  // dest. screen buffer rectangle 
    if (! fSuccess) 
    {
        printf("WriteConsoleOutput failed - (%d)\n", GetLastError()); 
        return 1;
    }
    Sleep(5000); 
 
    // Restore the original active screen buffer. 
 
    if (! SetConsoleActiveScreenBuffer(hStdout)) 
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError()); 
        return 1;
    }

    return 0;
}
```

 

 




