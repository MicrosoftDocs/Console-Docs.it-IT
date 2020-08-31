---
title: GetConsoleFontSize (funzione)
description: Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
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
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059796"
---
# <a name="getconsolefontsize-function"></a>GetConsoleFontSize (funzione)


Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.

<a name="syntax"></a>Sintassi
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a>Parametri
----------

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in ** \_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*nFont* \[ in\]  
Indice del tipo di carattere di cui è necessario recuperare le dimensioni. Questo indice viene ottenuto chiamando la funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche. Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.

Se la funzione ha esito negativo, la larghezza e l'altezza sono pari a zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Per compilare un'applicazione che usa questa funzione, definire ** \_ Win32 \_ WinNT** come 0x0500 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows Server 2003 [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ConsoleApi3. h (tramite wincon. h, Includi Windows. h)</td>
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

[Buffer dello schermo della console](console-screen-buffers.md)

[**COORD**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)

 

 




