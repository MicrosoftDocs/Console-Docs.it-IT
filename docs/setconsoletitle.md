---
title: SetConsoleTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleTitle, che imposta il titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- base.setconsoletitle
- consoles.setconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4
topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: e1789243fd5c184221dd53038d8ec87c9b010749
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060483"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="e02e8-104">SetConsoleTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="e02e8-104">SetConsoleTitle function</span></span>


<span data-ttu-id="e02e8-105">Imposta il titolo per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="e02e8-105">Sets the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="e02e8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e02e8-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

<a name="parameters"></a><span data-ttu-id="e02e8-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="e02e8-107">Parameters</span></span>
----------

<span data-ttu-id="e02e8-108">*lpConsoleTitle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e02e8-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="e02e8-109">Stringa da visualizzare nella barra del titolo della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="e02e8-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="e02e8-110">Le dimensioni totali devono essere inferiori a 64K.</span><span class="sxs-lookup"><span data-stu-id="e02e8-110">The total size must be less than 64K.</span></span>

<a name="return-value"></a><span data-ttu-id="e02e8-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e02e8-111">Return value</span></span>
------------

<span data-ttu-id="e02e8-112">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="e02e8-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e02e8-113">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="e02e8-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e02e8-114">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e02e8-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e02e8-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e02e8-115">Remarks</span></span>
-------

<span data-ttu-id="e02e8-116">Al termine del processo, il sistema ripristina il titolo originale della console.</span><span class="sxs-lookup"><span data-stu-id="e02e8-116">When the process terminates, the system restores the original console title.</span></span>

<span data-ttu-id="e02e8-117">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="e02e8-117">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="e02e8-118">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="e02e8-118">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="e02e8-119">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="e02e8-119">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="e02e8-120">Esempi</span><span class="sxs-lookup"><span data-stu-id="e02e8-120">Examples</span></span>
--------

<span data-ttu-id="e02e8-121">Nell'esempio seguente viene illustrato come recuperare e modificare il titolo della console.</span><span class="sxs-lookup"><span data-stu-id="e02e8-121">The following example shows how to retrieve and modify the console title.</span></span>

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

<a name="requirements"></a><span data-ttu-id="e02e8-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e02e8-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e02e8-123">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e02e8-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e02e8-124">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e02e8-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e02e8-125">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="e02e8-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e02e8-126">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="e02e8-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e02e8-127">Intestazione</span><span class="sxs-lookup"><span data-stu-id="e02e8-127">Header</span></span></p></td>
<td><span data-ttu-id="e02e8-128">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e02e8-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e02e8-129">Libreria</span><span class="sxs-lookup"><span data-stu-id="e02e8-129">Library</span></span></p></td>
<td><span data-ttu-id="e02e8-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e02e8-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e02e8-131">DLL</span><span class="sxs-lookup"><span data-stu-id="e02e8-131">DLL</span></span></p></td>
<td><span data-ttu-id="e02e8-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e02e8-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e02e8-133">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="e02e8-133">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="e02e8-134"><strong>SetConsoleTitleW</strong> (Unicode) e <strong>SetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e02e8-134"><strong>SetConsoleTitleW</strong> (Unicode) and <strong>SetConsoleTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e02e8-135"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e02e8-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e02e8-136">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="e02e8-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e02e8-137">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="e02e8-137">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="e02e8-138">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="e02e8-138">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="e02e8-139">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="e02e8-139">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="e02e8-140">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e02e8-140">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




