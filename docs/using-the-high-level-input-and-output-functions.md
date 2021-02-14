---
title: Uso delle funzioni di input e output di High-Level
description: Nell'esempio seguente vengono utilizzate le funzioni di I/O della console di alto livello per l'I/o della console. Per ulteriori informazioni sulle funzioni di I/O della console di alto livello, vedere High-Level I/O della console.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_using\_the\_high\_level\_input\_and\_output\_functions'
- base.using\_the\_high\_level\_input\_and\_output\_functions
- consoles.using\_the\_high\_level\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0226cd94-86d0-452b-80e6-e0fed8af0a62
ms.openlocfilehash: a520c1688bf9e682e5c6696738f5b81d30679d7b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358481"
---
# <a name="using-the-high-level-input-and-output-functions"></a>Uso delle funzioni di input e output di High-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Nell'esempio seguente vengono utilizzate le funzioni di I/O della console di alto livello per l'I/o della console. Per ulteriori informazioni sulle funzioni di I/O della console di alto livello, vedere [i/o](high-level-console-i-o.md)della console di alto livello.

Nell'esempio si presuppone che le modalità di I/O predefinite siano attive inizialmente per le prime chiamate alle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) . La modalità di input viene quindi modificata per attivare la modalità di input offline e la modalità di input echo per la seconda chiamata a **ReadFile** e **WriteFile**. La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) viene utilizzata per impostare i colori in cui verrà visualizzato il testo scritto successivamente. Prima di uscire, il programma ripristina gli attributi di colore e la modalità di input della console originale.

La funzione dell'esempio `NewLine` viene utilizzata quando la modalità di input della riga è disabilitata. Gestisce i ritorni a capo spostando la posizione del cursore sulla prima cella della riga successiva. Se il cursore si trova già nell'ultima riga del buffer dello schermo della console, il contenuto del buffer dello schermo della console viene spostato verso l'alto di una riga.

```C
#include <windows.h>

void NewLine(void);
void ScrollScreenBuffer(HANDLE, INT);

HANDLE hStdout, hStdin;
CONSOLE_SCREEN_BUFFER_INFO csbiInfo;

int main(void)
{
    LPSTR lpszPrompt1 = "Type a line and press Enter, or q to quit: ";
    LPSTR lpszPrompt2 = "Type any key, or q to quit: ";
    CHAR chBuffer[256];
    DWORD cRead, cWritten, fdwMode, fdwOldMode;
    WORD wOldColorAttrs;

    // Get handles to STDIN and STDOUT.

    hStdin = GetStdHandle(STD_INPUT_HANDLE);
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hStdin == INVALID_HANDLE_VALUE ||
        hStdout == INVALID_HANDLE_VALUE)
    {
        MessageBox(NULL, TEXT("GetStdHandle"), TEXT("Console Error"),
            MB_OK);
        return 1;
    }

    // Save the current text colors.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        MessageBox(NULL, TEXT("GetConsoleScreenBufferInfo"),
            TEXT("Console Error"), MB_OK);
        return 1;
    }

    wOldColorAttrs = csbiInfo.wAttributes;

    // Set the text attributes to draw red text on black background.

    if (! SetConsoleTextAttribute(hStdout, FOREGROUND_RED |
            FOREGROUND_INTENSITY))
    {
        MessageBox(NULL, TEXT("SetConsoleTextAttribute"),
            TEXT("Console Error"), MB_OK);
        return 1;
    }

    // Write to STDOUT and read from STDIN by using the default
    // modes. Input is echoed automatically, and ReadFile
    // does not return until a carriage return is typed.
    //
    // The default input modes are line, processed, and echo.
    // The default output modes are processed and wrap at EOL.

    while (1)
    {
        if (! WriteFile(
            hStdout,               // output handle
            lpszPrompt1,           // prompt string
            lstrlenA(lpszPrompt1), // string length
            &cWritten,             // bytes written
            NULL) )                // not overlapped
        {
            MessageBox(NULL, TEXT("WriteFile"), TEXT("Console Error"),
                MB_OK);
            return 1;
        }

        if (! ReadFile(
            hStdin,    // input handle
            chBuffer,  // buffer to read into
            255,       // size of buffer
            &cRead,    // actual bytes read
            NULL) )    // not overlapped
        break;
        if (chBuffer[0] == 'q') break;
    }

    // Turn off the line input and echo input modes

    if (! GetConsoleMode(hStdin, &fdwOldMode))
    {
       MessageBox(NULL, TEXT("GetConsoleMode"), TEXT("Console Error"),
           MB_OK);
       return 1;
    }

    fdwMode = fdwOldMode &
        ~(ENABLE_LINE_INPUT | ENABLE_ECHO_INPUT);
    if (! SetConsoleMode(hStdin, fdwMode))
    {
       MessageBox(NULL, TEXT("SetConsoleMode"), TEXT("Console Error"),
           MB_OK);
       return 1;
    }

    // ReadFile returns when any input is available.  
    // WriteFile is used to echo input.

    NewLine();

    while (1)
    {
        if (! WriteFile(
            hStdout,               // output handle
            lpszPrompt2,           // prompt string
            lstrlenA(lpszPrompt2), // string length
            &cWritten,             // bytes written
            NULL) )                // not overlapped
        {
            MessageBox(NULL, TEXT("WriteFile"), TEXT("Console Error"),
                MB_OK);
            return 1;
        }

        if (! ReadFile(hStdin, chBuffer, 1, &cRead, NULL))
            break;
        if (chBuffer[0] == '\r')
            NewLine();
        else if (! WriteFile(hStdout, chBuffer, cRead,
            &cWritten, NULL)) break;
        else
            NewLine();
        if (chBuffer[0] == 'q') break;
    }

    // Restore the original console mode.

    SetConsoleMode(hStdin, fdwOldMode);

    // Restore the original text colors.

    SetConsoleTextAttribute(hStdout, wOldColorAttrs);

    return 0;
}

// The NewLine function handles carriage returns when the processed
// input mode is disabled. It gets the current cursor position
// and resets it to the first cell of the next row.

void NewLine(void)
{
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        MessageBox(NULL, TEXT("GetConsoleScreenBufferInfo"),
            TEXT("Console Error"), MB_OK);
        return;
    }

    csbiInfo.dwCursorPosition.X = 0;

    // If it is the last line in the screen buffer, scroll
    // the buffer up.

    if ((csbiInfo.dwSize.Y-1) == csbiInfo.dwCursorPosition.Y)
    {
        ScrollScreenBuffer(hStdout, 1);
    }

    // Otherwise, advance the cursor to the next line.

    else csbiInfo.dwCursorPosition.Y += 1;

    if (! SetConsoleCursorPosition(hStdout,
        csbiInfo.dwCursorPosition))
    {
        MessageBox(NULL, TEXT("SetConsoleCursorPosition"),
            TEXT("Console Error"), MB_OK);
        return;
    }
}

void ScrollScreenBuffer(HANDLE h, INT x)
{
    SMALL_RECT srctScrollRect, srctClipRect;
    CHAR_INFO chiFill;
    COORD coordDest;

    srctScrollRect.Left = 0;
    srctScrollRect.Top = 1;
    srctScrollRect.Right = csbiInfo.dwSize.X - (SHORT)x;
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - (SHORT)x;

    // The destination for the scroll rectangle is one row up.

    coordDest.X = 0;
    coordDest.Y = 0;

    // The clipping rectangle is the same as the scrolling rectangle.
    // The destination row is left unchanged.

    srctClipRect = srctScrollRect;

    // Set the fill character and attributes.

    chiFill.Attributes = FOREGROUND_RED|FOREGROUND_INTENSITY;
    chiFill.Char.AsciiChar = (char)' ';

    // Scroll up one line.

    ScrollConsoleScreenBuffer(
        h,               // screen buffer handle
        &srctScrollRect, // scrolling rectangle
        &srctClipRect,   // clipping rectangle
        coordDest,       // top left destination cell
        &chiFill);       // fill character and color
}
```