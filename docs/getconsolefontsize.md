---
title: GetConsoleFontSize (funzione)
description: Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96086720ee2c4ae787d2b52eee5439d54f081b8e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358341"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="4e169-104">GetConsoleFontSize (funzione)</span><span class="sxs-lookup"><span data-stu-id="4e169-104">GetConsoleFontSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4e169-105">Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.</span><span class="sxs-lookup"><span data-stu-id="4e169-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e169-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4e169-106">Syntax</span></span>

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a><span data-ttu-id="4e169-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="4e169-107">Parameters</span></span>

<span data-ttu-id="4e169-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4e169-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4e169-109">Handle per il buffer dello schermo della console.</span><span class="sxs-lookup"><span data-stu-id="4e169-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4e169-110">L'handle deve disporre del diritto di accesso **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="4e169-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4e169-111">Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4e169-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4e169-112">*nFont* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4e169-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="4e169-113">Indice del tipo di carattere di cui è necessario recuperare le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="4e169-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="4e169-114">Questo indice viene ottenuto chiamando la funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="4e169-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="4e169-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4e169-115">Return value</span></span>

<span data-ttu-id="4e169-116">Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche.</span><span class="sxs-lookup"><span data-stu-id="4e169-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="4e169-117">Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.</span><span class="sxs-lookup"><span data-stu-id="4e169-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="4e169-118">Se la funzione ha esito negativo, la larghezza e l'altezza sono pari a zero.</span><span class="sxs-lookup"><span data-stu-id="4e169-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="4e169-119">Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="4e169-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="4e169-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4e169-120">Remarks</span></span>

<span data-ttu-id="4e169-121">Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="4e169-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="4e169-122">Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="4e169-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="4e169-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4e169-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4e169-124">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4e169-124">Minimum supported client</span></span> | <span data-ttu-id="4e169-125">\[Solo app desktop Windows XP\]</span><span class="sxs-lookup"><span data-stu-id="4e169-125">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="4e169-126">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="4e169-126">Minimum supported server</span></span> | <span data-ttu-id="4e169-127">\[Solo app desktop Windows Server 2003\]</span><span class="sxs-lookup"><span data-stu-id="4e169-127">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="4e169-128">Intestazione</span><span class="sxs-lookup"><span data-stu-id="4e169-128">Header</span></span> | <span data-ttu-id="4e169-129">ConsoleApi3. h (tramite WinCon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4e169-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4e169-130">Libreria</span><span class="sxs-lookup"><span data-stu-id="4e169-130">Library</span></span> | <span data-ttu-id="4e169-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="4e169-131">Kernel32.lib</span></span> |
| <span data-ttu-id="4e169-132">DLL</span><span class="sxs-lookup"><span data-stu-id="4e169-132">DLL</span></span> | <span data-ttu-id="4e169-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4e169-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4e169-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4e169-134">See also</span></span>

[<span data-ttu-id="4e169-135">Funzioni della console</span><span class="sxs-lookup"><span data-stu-id="4e169-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4e169-136">Buffer dello schermo della console</span><span class="sxs-lookup"><span data-stu-id="4e169-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="4e169-137">**COORD**</span><span class="sxs-lookup"><span data-stu-id="4e169-137">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4e169-138">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="4e169-138">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)