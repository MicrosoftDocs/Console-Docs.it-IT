---
title: SetConsoleTitle (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleTitle, che imposta il titolo per la finestra della console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: fa4f79925af870f3d345f384dab52ff4b98c182c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037035"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="dd5ae-104">SetConsoleTitle (funzione)</span><span class="sxs-lookup"><span data-stu-id="dd5ae-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="dd5ae-105">Imposta il titolo per la finestra della console corrente.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd5ae-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dd5ae-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="dd5ae-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="dd5ae-107">Parameters</span></span>

<span data-ttu-id="dd5ae-108">*lpConsoleTitle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="dd5ae-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="dd5ae-109">Stringa da visualizzare nella barra del titolo della finestra della console.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="dd5ae-110">Le dimensioni totali devono essere inferiori a 64K.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="dd5ae-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="dd5ae-111">Return value</span></span>

<span data-ttu-id="dd5ae-112">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="dd5ae-113">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="dd5ae-114">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="dd5ae-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="dd5ae-115">Commenti</span><span class="sxs-lookup"><span data-stu-id="dd5ae-115">Remarks</span></span>

<span data-ttu-id="dd5ae-116">Al termine del processo, il sistema ripristina il titolo originale della console.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="dd5ae-117">Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze del **[titolo della finestra](console-virtual-terminal-sequences.md#window-title)** .</span><span class="sxs-lookup"><span data-stu-id="dd5ae-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="dd5ae-118">Le _sequenze di terminali virtuali_ sono consigliate per lo sviluppo nuovo e continuo.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="dd5ae-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="dd5ae-119">Examples</span></span>

<span data-ttu-id="dd5ae-120">Nell'esempio seguente viene illustrato come recuperare e modificare il titolo della console.</span><span class="sxs-lookup"><span data-stu-id="dd5ae-120">The following example shows how to retrieve and modify the console title.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="dd5ae-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dd5ae-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="dd5ae-122">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="dd5ae-122">Minimum supported client</span></span> | <span data-ttu-id="dd5ae-123">\[Solo app desktop Windows 2000 Professional\]</span><span class="sxs-lookup"><span data-stu-id="dd5ae-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="dd5ae-124">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="dd5ae-124">Minimum supported server</span></span> | <span data-ttu-id="dd5ae-125">Solo app desktop di Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="dd5ae-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="dd5ae-126">Intestazione</span><span class="sxs-lookup"><span data-stu-id="dd5ae-126">Header</span></span> | <span data-ttu-id="dd5ae-127">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="dd5ae-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="dd5ae-128">Libreria</span><span class="sxs-lookup"><span data-stu-id="dd5ae-128">Library</span></span> | <span data-ttu-id="dd5ae-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="dd5ae-129">Kernel32.lib</span></span> |
| <span data-ttu-id="dd5ae-130">DLL</span><span class="sxs-lookup"><span data-stu-id="dd5ae-130">DLL</span></span> | <span data-ttu-id="dd5ae-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="dd5ae-131">Kernel32.dll</span></span> |
| <span data-ttu-id="dd5ae-132">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="dd5ae-132">Unicode and ANSI names</span></span> | <span data-ttu-id="dd5ae-133">**SetConsoleTitleW** (Unicode) e **SetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="dd5ae-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="dd5ae-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="dd5ae-134">See also</span></span>

[<span data-ttu-id="dd5ae-135">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="dd5ae-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="dd5ae-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="dd5ae-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="dd5ae-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="dd5ae-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="dd5ae-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
