---
title: WriteConsoleInput (funzione)
description: Vedere informazioni di riferimento sulla funzione WriteConsoleInput, che consente di scrivere dati direttamente nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060564"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="ce0d7-104">WriteConsoleInput (funzione)</span><span class="sxs-lookup"><span data-stu-id="ce0d7-104">WriteConsoleInput function</span></span>


<span data-ttu-id="ce0d7-105">Scrive i dati direttamente nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-105">Writes data directly to the console input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ce0d7-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ce0d7-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a><span data-ttu-id="ce0d7-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ce0d7-107">Parameters</span></span>
----------

<span data-ttu-id="ce0d7-108">*hConsoleInput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="ce0d7-109">Handle per il buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-109">A handle to the console input buffer.</span></span> <span data-ttu-id="ce0d7-110">L'handle deve avere il diritto di accesso in \*\* \_ scrittura generico\*\* .</span><span class="sxs-lookup"><span data-stu-id="ce0d7-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="ce0d7-111">Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ce0d7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ce0d7-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="ce0d7-113">Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che contengono dati da scrivere nel buffer di input.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="ce0d7-114">*nLength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="ce0d7-115">Numero di record di input da scrivere.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-115">The number of input records to be written.</span></span>

<span data-ttu-id="ce0d7-116">*lpNumberOfEventsWritten* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="ce0d7-117">Puntatore a una variabile che riceve il numero di record di input effettivamente scritti.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-117">A pointer to a variable that receives the number of input records actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="ce0d7-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ce0d7-118">Return value</span></span>
------------

<span data-ttu-id="ce0d7-119">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ce0d7-120">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ce0d7-121">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ce0d7-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ce0d7-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ce0d7-122">Remarks</span></span>
-------

<span data-ttu-id="ce0d7-123">**WriteConsoleInput** inserisce i record di input nel buffer di input dietro tutti gli eventi in sospeso nel buffer.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="ce0d7-124">Il buffer di input aumenta in modo dinamico, se necessario, per mantenere il numero di eventi scritti.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

<span data-ttu-id="ce0d7-125">Questa funzione usa i caratteri Unicode o i caratteri a 8 bit della tabella codici corrente della console.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="ce0d7-126">Il valore predefinito della tabella codici della console inizialmente è la tabella codici OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="ce0d7-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="ce0d7-127">Per modificare la tabella codici della console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) oppure usare i comandi **chcp** o **mode con CP SELECT =** .</span><span class="sxs-lookup"><span data-stu-id="ce0d7-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="ce0d7-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ce0d7-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ce0d7-129">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ce0d7-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ce0d7-130">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ce0d7-131">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="ce0d7-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ce0d7-132">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="ce0d7-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ce0d7-133">Intestazione</span><span class="sxs-lookup"><span data-stu-id="ce0d7-133">Header</span></span></p></td>
<td><span data-ttu-id="ce0d7-134">ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ce0d7-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ce0d7-135">Libreria</span><span class="sxs-lookup"><span data-stu-id="ce0d7-135">Library</span></span></p></td>
<td><span data-ttu-id="ce0d7-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ce0d7-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ce0d7-137">DLL</span><span class="sxs-lookup"><span data-stu-id="ce0d7-137">DLL</span></span></p></td>
<td><span data-ttu-id="ce0d7-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ce0d7-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ce0d7-139">Nomi Unicode e ANSI</span><span class="sxs-lookup"><span data-stu-id="ce0d7-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ce0d7-140"><strong>WriteConsoleInputW</strong> (Unicode) e <strong>WriteConsoleInputA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ce0d7-140"><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ce0d7-141"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce0d7-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ce0d7-142">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="ce0d7-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ce0d7-143">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-143">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="ce0d7-144">Funzioni di input della console di basso livello</span><span class="sxs-lookup"><span data-stu-id="ce0d7-144">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="ce0d7-145">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-145">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="ce0d7-146">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-146">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="ce0d7-147">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-147">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="ce0d7-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ce0d7-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ce0d7-150">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="ce0d7-150">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




