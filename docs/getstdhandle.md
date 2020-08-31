---
title: GetStdHandle (funzione)
description: Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059625"
---
# <a name="getstdhandle-function"></a>GetStdHandle (funzione)


Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).

<a name="syntax"></a>Sintassi
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a>Parametri
----------

*nStdHandle* \[ in\]  
Il dispositivo standard. Questo parametro può essere uno dei valori seguenti.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</td>
<td><p>Dispositivo di input standard. Inizialmente, si tratta del buffer di input della console, CONIn $.</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>Dispositivo di output standard. Inizialmente, si tratta del buffer dello schermo della console attivo, CONOUT $.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>Dispositivo di errore standard. Inizialmente, si tratta del buffer dello schermo della console attivo, CONOUT $.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente a [**SetStdHandle**](setstdhandle.md). L'handle dispone di diritti di accesso di ** \_ lettura** e ** \_ scrittura** generici, a meno che l'applicazione non abbia utilizzato **SetStdHandle** per impostare un handle standard con accesso minore.

Se la funzione ha esito negativo, il valore restituito è un ** \_ \_ valore di handle non valido**. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo e non è stato reindirizzato, il valore restituito è **null**.

<a name="remarks"></a>Osservazioni
-------

Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console. Quando viene creata una console, l'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle del buffer dello schermo attivo della console. Questi handle possono essere usati dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o da qualsiasi funzione console che accede al buffer di input della console o a un buffer dello schermo (ad esempio, le funzioni [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato. Se gli handle standard sono stati reindirizzati, è possibile specificare il valore CONIn $ in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console. Analogamente, è possibile specificare il valore CONOUT $ per ottenere un handle per il buffer dello schermo attivo di una console.

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportamento di collegamento/scollegamento

Quando ci si connette a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF \_ USESTDHANDLES** durante la creazione del processo.

Se il valore esistente dell'handle standard è **null**o il valore esistente dell'handle standard è simile a un pseudohandle della console, l'handle viene sostituito con un handle della console.

Quando un elemento padre usa sia **Create \_ New \_ console** che **STARTF \_ USESTDHANDLES** per creare un processo console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia null o un pseudohandle console.

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

<a name="requirements"></a>Requisiti
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimo supportato</p></td>
<td><p>Windows 2000 Professional [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows 2000 Server [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ProcessEnv. h (tramite Winbase. h, Includi Windows. h)</td>
</tr>
<tr class="even">
<td><p>Libreria</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[Funzioni console](console-functions.md)

[Handle della console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




