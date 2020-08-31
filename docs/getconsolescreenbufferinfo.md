---
title: GetConsoleScreenBufferInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleScreenBufferInfo, che recupera le informazioni sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059716"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo (funzione)


Recupera le informazioni sul buffer dello schermo della console specificato.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfo* \[ out\]  
Puntatore a una struttura [**di \_ \_ \_ informazioni sul buffer dello schermo della console**](console-screen-buffer-info-str.md) che riceve le informazioni sul buffer dello schermo della console.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Il rettangolo restituito nel membro **srWindow** della struttura di [** \_ informazioni sul \_ buffer \_ dello schermo della console**](console-screen-buffer-info-str.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.

Tutte le coordinate restituite nella struttura delle [** \_ \_ \_ informazioni del buffer dello schermo della console**](console-screen-buffer-info-str.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.

<a name="examples"></a>Esempi
--------

Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).

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
<td>ConsoleApi2. h (tramite wincon. h, Includi Windows. h)</td>
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

[**\_informazioni sul \_ buffer dello schermo della console \_**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)

 

 




