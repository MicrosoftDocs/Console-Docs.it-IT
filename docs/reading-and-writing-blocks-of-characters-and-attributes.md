---
title: Lettura e scrittura di blocchi di caratteri e attributi
description: La funzione ReadConsoleOutput copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer dello schermo della console in un buffer di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_reading\_and\_writing\_blocks\_of\_characters\_and\_attributes'
- base.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
- consoles.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: eaa57723-f003-4e90-8156-be8c3b42b912
ms.openlocfilehash: 17c50e3cc0d519e087cdb8bb40e04db43cfea36f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039469"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a>Lettura e scrittura di blocchi di caratteri e attributi

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

La funzione [**ReadConsoleOutput**](readconsoleoutput.md) copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer dello schermo della console in un buffer di destinazione. La funzione considera il buffer di destinazione come una matrice bidimensionale di strutture di [**\_ informazioni char**](char-info-str.md) . Analogamente, la funzione [**WriteConsoleOutput**](writeconsoleoutput.md) copia un blocco rettangolare di dati di attributi di caratteri e colori da un buffer di origine a un buffer dello schermo della console. Per ulteriori informazioni sulla lettura o la scrittura in blocchi rettangolari di celle del buffer dello schermo, vedere [metodi di input e output](input-and-output-methods.md).

Nell'esempio seguente viene usata la funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) per creare un nuovo buffer dello schermo. Dopo che la funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) rende il buffer dello schermo attivo, viene copiato un blocco di caratteri e attributi di colore dalle prime due righe del buffer dello schermo stdout in un buffer temporaneo. I dati vengono quindi copiati dal buffer temporaneo nel nuovo buffer dello schermo attivo. Al termine dell'applicazione con il nuovo buffer dello schermo, viene chiamato **SetConsoleActiveScreenBuffer** per ripristinare il buffer dello schermo stdout originale.

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
