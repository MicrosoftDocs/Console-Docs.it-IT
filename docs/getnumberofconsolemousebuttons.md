---
title: GetNumberOfConsoleMouseButtons (funzione)
description: Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060444"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="0e963-104">GetNumberOfConsoleMouseButtons (funzione)</span><span class="sxs-lookup"><span data-stu-id="0e963-104">GetNumberOfConsoleMouseButtons function</span></span>


<span data-ttu-id="0e963-105">Recupera il numero di pulsanti sul mouse utilizzato dalla console corrente.</span><span class="sxs-lookup"><span data-stu-id="0e963-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="0e963-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0e963-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a><span data-ttu-id="0e963-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="0e963-107">Parameters</span></span>
----------

<span data-ttu-id="0e963-108">*lpNumberOfMouseButtons* \[ out\]</span><span class="sxs-lookup"><span data-stu-id="0e963-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="0e963-109">Puntatore a una variabile che riceve il numero di pulsanti del mouse.</span><span class="sxs-lookup"><span data-stu-id="0e963-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

<a name="return-value"></a><span data-ttu-id="0e963-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0e963-110">Return value</span></span>
------------

<span data-ttu-id="0e963-111">Se la funzione ha esito positivo, il valore restituito è diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="0e963-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0e963-112">Se la funzione ha esito negativo, il valore restituito è zero.</span><span class="sxs-lookup"><span data-stu-id="0e963-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0e963-113">Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0e963-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0e963-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0e963-114">Remarks</span></span>
-------

<span data-ttu-id="0e963-115">Quando una console riceve l'input del mouse, una struttura di [\*\* \_ record di input\*\*](input-record-str.md) contenente una struttura di [\*\* \_ \_ record di eventi del mouse\*\*](mouse-event-record-str.md) viene inserita nel buffer di input della console.</span><span class="sxs-lookup"><span data-stu-id="0e963-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="0e963-116">Il membro **dwButtonState** del \*\* \_ \_ record dell'evento del mouse\*\* presenta un bit che indica lo stato di ogni pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="0e963-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="0e963-117">Il bit è 1 se il pulsante è inattivo e 0 se il pulsante è attivo.</span><span class="sxs-lookup"><span data-stu-id="0e963-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="0e963-118">Per determinare il numero di bit significativi, utilizzare **GetNumberOfConsoleMouseButtons**.</span><span class="sxs-lookup"><span data-stu-id="0e963-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

<a name="requirements"></a><span data-ttu-id="0e963-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0e963-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0e963-120">Client minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0e963-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0e963-121">Windows 2000 Professional [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0e963-121">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0e963-122">Server minimo supportato</span><span class="sxs-lookup"><span data-stu-id="0e963-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0e963-123">Windows 2000 Server [solo app desktop]</span><span class="sxs-lookup"><span data-stu-id="0e963-123">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0e963-124">Intestazione</span><span class="sxs-lookup"><span data-stu-id="0e963-124">Header</span></span></p></td>
<td><span data-ttu-id="0e963-125">ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0e963-125">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0e963-126">Libreria</span><span class="sxs-lookup"><span data-stu-id="0e963-126">Library</span></span></p></td>
<td><span data-ttu-id="0e963-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0e963-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0e963-128">DLL</span><span class="sxs-lookup"><span data-stu-id="0e963-128">DLL</span></span></p></td>
<td><span data-ttu-id="0e963-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0e963-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0e963-130"><span id="see_also"></span>Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e963-130"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0e963-131">Funzioni console</span><span class="sxs-lookup"><span data-stu-id="0e963-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0e963-132">Buffer di input della console</span><span class="sxs-lookup"><span data-stu-id="0e963-132">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="0e963-133">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0e963-133">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="0e963-134">**RECORD di INPUT \_**</span><span class="sxs-lookup"><span data-stu-id="0e963-134">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="0e963-135">**\_record evento \_ mouse**</span><span class="sxs-lookup"><span data-stu-id="0e963-135">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

 

 




