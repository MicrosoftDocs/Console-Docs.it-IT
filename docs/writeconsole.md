---
title: Funzione WriteConsole
description: Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357611"
---
# <a name="writeconsole-function"></a>Funzione WriteConsole

Scrive una stringa di caratteri in un buffer dello schermo della console iniziando dalla posizione corrente del cursore.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Puntatore a un buffer che contiene caratteri da scrivere nel buffer dello schermo della console. È previsto che sia una matrice di `char` per `WriteConsoleA` o `wchar_t` per `WriteConsoleW`.

*nNumberOfCharsToWrite* \[in\]  
Numero di caratteri da scrivere. Se la dimensione totale del numero specificato di caratteri supera l'heap disponibile, la funzione avrà esito negativo con **ERROR\_NOT\_ENOUGH\_MEMORY**.

*lpNumberOfCharsWritten* \[out, optional\]  
Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.

*lpReserved* riservato; deve essere **NULL**.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

La funzione **WriteConsole** scrive i caratteri nel buffer dello schermo della console in corrispondenza della posizione corrente del cursore. La posizione del cursore viene spostata man mano che i caratteri vengono scritti. La funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) imposta la posizione corrente del cursore.

I caratteri vengono scritti usando gli attributi del colore di primo piano e di sfondo associati al buffer dello schermo della console. La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifica questi colori. Per determinare gli attributi di colore correnti e la posizione corrente del cursore, usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Tutte le modalità di input che influiscono sul comportamento della funzione [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) hanno lo stesso effetto su **WriteConsole**. Per recuperare e impostare le modalità di output di un buffer dello schermo della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md).

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** ha esito negativo se viene usata con un handle standard che viene reindirizzato a un file. Se un'applicazione elabora l'output multilingue che può essere reindirizzato, determinare se l'handle di output è un handle della console (un metodo consiste nel chiamare la funzione [**GetConsoleMode**](getconsolemode.md) e verificare se l'operazione ha esito positivo). Se l'handle è un handle della console, chiamare **WriteConsole**. Se l'handle non è un handle della console, l'output viene reindirizzato ed è necessario chiamare [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) per eseguire le funzioni di I/O. Assicurarsi di anteporre un prefisso a un file di testo normale Unicode con un indicatore dell'ordine dei byte. Per altre informazioni, vedere [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks) (Uso degli indicatori dell'ordine dei byte).

Sebbene un'applicazione possa usare **WriteConsole** in modalità ANSI per scrivere caratteri ANSI, le console non supportano le sequenze di "escape ANSI" o "terminale virtuale", a meno che non siano abilitate. Per altre informazioni e per l'applicabilità della versione del sistema operativo, vedere [**Sequenze del terminale virtuale della console**](console-virtual-terminal-sequences.md).

Quando le sequenze di escape del terminale virtuale non sono abilitate, le funzioni della console possono fornire funzionalità equivalenti. Per altre informazioni, vedere [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) e [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **WriteConsoleW** (Unicode) e **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Metodi di input e output](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)