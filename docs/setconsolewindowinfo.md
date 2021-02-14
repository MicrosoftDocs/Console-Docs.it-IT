---
title: SetConsoleWindowInfo (funzione)
description: Imposta la dimensione e la posizione correnti della finestra di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af3f9d63b01697a2ab0735014a4836d9ab11d8cf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358531"
---
# <a name="setconsolewindowinfo-function"></a><span data-ttu-id="6e677-104">SetConsoleWindowInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="6e677-104">SetConsoleWindowInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="6e677-105">Imposta la dimensione e la posizione correnti della finestra di un buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6e677-105">Sets the current size and position of a console screen buffer's window.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e677-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6e677-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a><span data-ttu-id="6e677-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="6e677-107">Parameters</span></span>

<span data-ttu-id="6e677-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6e677-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6e677-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6e677-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6e677-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="6e677-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6e677-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6e677-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6e677-112">*bAbsolute* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6e677-112">*bAbsolute* \[in\]</span></span>  
<span data-ttu-id="6e677-113">Se questo parametro è **true**, le coordinate specificano i nuovi angoli superiore sinistro e inferiore destro della finestra.</span><span class="sxs-lookup"><span data-stu-id="6e677-113">If this parameter is **TRUE**, the coordinates specify the new upper-left and lower-right corners of the window.</span></span> <span data-ttu-id="6e677-114">Se è **false**, le coordinate sono relative alle coordinate dell'angolo finestra correnti.</span><span class="sxs-lookup"><span data-stu-id="6e677-114">If it is **FALSE**, the coordinates are relative to the current window-corner coordinates.</span></span>

<span data-ttu-id="6e677-115">*lpConsoleWindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6e677-115">*lpConsoleWindow* \[in\]</span></span>  
<span data-ttu-id="6e677-116">Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) che specifica i nuovi angoli superiore sinistro e inferiore destro della finestra.</span><span class="sxs-lookup"><span data-stu-id="6e677-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.</span></span>

## <a name="return-value"></a><span data-ttu-id="6e677-117">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6e677-117">Return value</span></span>

<span data-ttu-id="6e677-118">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="6e677-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6e677-119">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="6e677-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6e677-120">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="6e677-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6e677-121">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6e677-121">Remarks</span></span>

<span data-ttu-id="6e677-122">La funzione ha esito negativo se il rettangolo della finestra specificato si estende oltre i limiti del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6e677-122">The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer.</span></span> <span data-ttu-id="6e677-123">Ciò significa che i membri **Top** e **Left** del rettangolo *lpConsoleWindow* (o le coordinate Top e Left calcolate, se *bAbsolute* è false) non possono essere minori di zero.</span><span class="sxs-lookup"><span data-stu-id="6e677-123">This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero.</span></span> <span data-ttu-id="6e677-124">Analogamente, i membri **inferiore** e **destro** (oppure le coordinate in basso e a destra calcolata) non possono essere maggiori di (altezza del buffer dello schermo – 1) e (larghezza del buffer dello schermo – 1), rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="6e677-124">Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively.</span></span> <span data-ttu-id="6e677-125">La funzione ha esito negativo anche se il membro **destro** (o la coordinata destra calcolata) è minore o uguale al membro a **sinistra** (o a una coordinata sinistra calcolata) o se il membro **inferiore** (o la coordinata inferiore calcolata) è minore o uguale al membro **superiore** (o coordinata superiore calcolata).</span><span class="sxs-lookup"><span data-stu-id="6e677-125">The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).</span></span>

<span data-ttu-id="6e677-126">Per le console con più di un buffer dello schermo, la modifica della posizione della finestra per un buffer dello schermo non influisce sulle posizioni della finestra degli altri buffer dello schermo.</span><span class="sxs-lookup"><span data-stu-id="6e677-126">For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.</span></span>

<span data-ttu-id="6e677-127">Per determinare le dimensioni e la posizione correnti della finestra di un buffer dello schermo, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6e677-127">To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="6e677-128">Questa funzione restituisce anche le dimensioni massime della finestra, date le dimensioni correnti del buffer dello schermo, le dimensioni correnti del carattere e le dimensioni dello schermo.</span><span class="sxs-lookup"><span data-stu-id="6e677-128">This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size.</span></span> <span data-ttu-id="6e677-129">La funzione [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) restituisce le dimensioni massime della finestra in base al tipo di carattere e alle dimensioni dello schermo correnti, ma non considera le dimensioni del buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="6e677-129">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.</span></span>

<span data-ttu-id="6e677-130">**SetConsoleWindowInfo** può essere usato per scorrere il contenuto del buffer dello schermo della console spostando la posizione del rettangolo della finestra senza modificarne le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="6e677-130">**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a><span data-ttu-id="6e677-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="6e677-131">Examples</span></span>

<span data-ttu-id="6e677-132">Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="6e677-132">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6e677-133">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6e677-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6e677-134">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e677-134">Minimum supported client</span></span> | <span data-ttu-id="6e677-135">Windows 2000 Professional \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="6e677-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6e677-136">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="6e677-136">Minimum supported server</span></span> | <span data-ttu-id="6e677-137">Windows 2000 Server \[solo app desktop\]</span><span class="sxs-lookup"><span data-stu-id="6e677-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6e677-138">Intestazione</span><span class="sxs-lookup"><span data-stu-id="6e677-138">Header</span></span> | <span data-ttu-id="6e677-139">ConsoleApi2. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6e677-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6e677-140">Libreria</span><span class="sxs-lookup"><span data-stu-id="6e677-140">Library</span></span> | <span data-ttu-id="6e677-141">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6e677-141">Kernel32.lib</span></span> |
| <span data-ttu-id="6e677-142">DLL</span><span class="sxs-lookup"><span data-stu-id="6e677-142">DLL</span></span> | <span data-ttu-id="6e677-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6e677-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e677-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6e677-144">See also</span></span>

[<span data-ttu-id="6e677-145">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="6e677-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6e677-146">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="6e677-146">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="6e677-147">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="6e677-147">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="6e677-148">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="6e677-148">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="6e677-149">Scorrimento del buffer dello schermo</span><span class="sxs-lookup"><span data-stu-id="6e677-149">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="6e677-150">**\_Rect piccolo**</span><span class="sxs-lookup"><span data-stu-id="6e677-150">**SMALL\_RECT**</span></span>](small-rect-str.md)