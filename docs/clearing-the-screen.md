---
title: Cancellazione dello schermo
description: Come cancellare lo schermo della console di Windows usando la funzione di sistema o a livello di codice tramite le funzioni API pubbliche.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- base.clearing\_the\_screen
- consoles.clearing\_the\_screen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
ms.openlocfilehash: fd2a407e56d6b0fe00db59c5f783cb13546119f6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060201"
---
# <a name="clearing-the-screen"></a><span data-ttu-id="f77b7-104">Cancellazione dello schermo</span><span class="sxs-lookup"><span data-stu-id="f77b7-104">Clearing the Screen</span></span>


<span data-ttu-id="f77b7-105">Esistono due modi per cancellare la schermata in un'applicazione console.</span><span class="sxs-lookup"><span data-stu-id="f77b7-105">There are two ways to clear the screen in a console application.</span></span>

## <a name="span-idexample_1spanspan-idexample_1spanspan-idexample_1spanexample-1"></a><span data-ttu-id="f77b7-106"><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Esempio 1</span><span class="sxs-lookup"><span data-stu-id="f77b7-106"><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Example 1</span></span>


<span data-ttu-id="f77b7-107">Il primo metodo consiste nell'usare la funzione di **sistema** del runtime del linguaggio C.</span><span class="sxs-lookup"><span data-stu-id="f77b7-107">The first method is to use the C run-time **system** function.</span></span> <span data-ttu-id="f77b7-108">La funzione di **sistema** richiama il comando **CLS** fornito dall'interprete dei comandi per cancellare lo schermo.</span><span class="sxs-lookup"><span data-stu-id="f77b7-108">The **system** function invokes the **cls** command provided by the command interpreter to clear the screen.</span></span>

```C
#include <stdlib.h>

int main( void )
{
    system("cls");
    return 0;
}
```

## <a name="span-idexample_2spanspan-idexample_2spanspan-idexample_2spanexample-2"></a><span data-ttu-id="f77b7-109"><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Esempio 2</span><span class="sxs-lookup"><span data-stu-id="f77b7-109"><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Example 2</span></span>


<span data-ttu-id="f77b7-110">Il secondo metodo consiste nel scrivere una funzione per cancellare a livello di codice lo schermo usando le funzioni [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) e [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="f77b7-110">The second method is to write a function to programmatically clear the screen using the [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) and [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) functions.</span></span> <span data-ttu-id="f77b7-111">Nell'esempio di codice riportato di seguito viene illustrata questa tecnica.</span><span class="sxs-lookup"><span data-stu-id="f77b7-111">The following sample code demonstrates this technique.</span></span>

```C
#include <windows.h>

void cls( HANDLE hConsole )
{
   COORD coordScreen = { 0, 0 };    // home for the cursor 
   DWORD cCharsWritten;
   CONSOLE_SCREEN_BUFFER_INFO csbi; 
   DWORD dwConSize;

// Get the number of character cells in the current buffer. 

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

   // Fill the entire screen with blanks.

   if( !FillConsoleOutputCharacter( hConsole,        // Handle to console screen buffer 
                                    (TCHAR) ' ',     // Character to write to the buffer
                                    dwConSize,       // Number of cells to write 
                                    coordScreen,     // Coordinates of first cell 
                                    &cCharsWritten ))// Receive number of characters written
   {
      return;
   }

   // Get the current text attribute.

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   // Set the buffer's attributes accordingly.

   if( !FillConsoleOutputAttribute( hConsole,         // Handle to console screen buffer 
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute 
                                    coordScreen,      // Coordinates of first cell 
                                    &cCharsWritten )) // Receive number of characters written
   {
      return;
   }

   // Put the cursor at its home coordinates.

   SetConsoleCursorPosition( hConsole, coordScreen );
}

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);
    
    return 0;
}
```

 

 




