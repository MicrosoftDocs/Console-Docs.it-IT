---
title: SetConsoleOutputCP (funzione)
description: Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060501"
---
# <a name="setconsoleoutputcp-function"></a>SetConsoleOutputCP (funzione)


Imposta la tabella codici di output utilizzata dalla console di associata al processo chiamante. Una console di usa la relativa tabella codici di output per tradurre i valori di carattere scritti dalle varie funzioni di output nelle immagini visualizzate nella finestra della console.

<a name="syntax"></a>Sintassi
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a>Parametri
----------

*wCodePageID* \[ in\]  
Identificatore della tabella codici da impostare. Per altre informazioni, vedere la sezione Osservazioni.

<a name="return-value"></a>Valore restituito
------------

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Osservazioni
-------

Una tabella codici esegue il mapping di 256 codici carattere a singoli caratteri. Diverse tabelle codici contengono caratteri speciali differenti, in genere personalizzati per un linguaggio o per un gruppo di linguaggi.

Se il tipo di carattere corrente è un tipo di carattere Unicode a passo fisso, **SetConsoleOutputCP** modifica il mapping dei valori di carattere nel set di glifi del tipo di carattere, anziché caricare un tipo di carattere separato ogni volta che viene chiamato. Ciò influiscono sul modo in cui i caratteri estesi (valore ASCII maggiore di 127) vengono visualizzati in una finestra della console. Tuttavia, se il tipo di carattere corrente è un tipo di carattere raster, **SetConsoleOutputCP** non influisce sulla modalità di visualizzazione dei caratteri estesi.

Per trovare le tabelle codici installate o supportate dal sistema operativo, usare la funzione [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) . Gli identificatori delle tabelle codici disponibili nel computer locale vengono archiviati anche nel registro di sistema con la seguente chiave:

**Tabella \_ \_ \\ \\ \\ codici NLS del controllo CurrentControlSet \\ di HKEY Local Machine System \\**

Tuttavia, è preferibile usare [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) per enumerare le tabelle codici, perché il registro di sistema può variare nelle diverse versioni di Windows.
Per determinare se una determinata tabella codici è valida, utilizzare la funzione [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) . Per recuperare ulteriori informazioni su una tabella codici, incluso il relativo nome, utilizzare la funzione [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Per un elenco degli identificatori di tabella codici disponibili, vedere [identificatori](https://msdn.microsoft.com/library/windows/desktop/dd317756)delle tabelle codici.

Per determinare la tabella codici di output corrente di una console, usare la funzione [**GetConsoleOutputCP**](getconsoleoutputcp.md) . Per impostare e recuperare la tabella codici di input di una console, usare le funzioni [**SetConsoleCP**](setconsolecp.md) e [**GetConsoleCP**](getconsolecp.md) .

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


[Tabelle codici della console](console-code-pages.md)

[Funzioni console](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

 

 




