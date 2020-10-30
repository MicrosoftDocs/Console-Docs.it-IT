---
title: WriteConsole (funzione)
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
ms.openlocfilehash: 9023372cf585e9b3645e7dc0a54e46a665935ad4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037129"
---
# <a name="writeconsole-function"></a>WriteConsole (funzione)

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

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Puntatore a un buffer che contiene caratteri da scrivere nel buffer dello schermo della console. È previsto che sia una matrice di `char` per `WriteConsoleA` o `wchar_t` per `WriteConsoleW` .

*nNumberOfCharsToWrite* \[ in\]  
Numero di caratteri da scrivere. Se la dimensione totale del numero specificato di caratteri supera l'heap disponibile, la funzione ha esito negativo e l' **errore non è sufficiente per la \_ \_ \_ memoria** .

*lpNumberOfCharsWritten* \[ out, facoltativo\]  
Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti.

*lpReserved* Riservati deve essere **null** .

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

La funzione **WriteConsole** scrive i caratteri nel buffer dello schermo della console in corrispondenza della posizione corrente del cursore. La posizione del cursore viene spostata come caratteri. La funzione [**SetConsoleCursorPosition**](setconsolecursorposition.md) imposta la posizione corrente del cursore.

I caratteri vengono scritti usando gli attributi del colore di primo piano e di sfondo associati al buffer dello schermo della console. La funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) modifica questi colori. Per determinare gli attributi di colore correnti e la posizione corrente del cursore, utilizzare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Tutte le modalità di input che influiscono sul comportamento della funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) hanno lo stesso effetto su **WriteConsole** . Per recuperare e impostare le modalità di output di un buffer dello schermo della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** ha esito negativo se viene usato con un handle standard che viene reindirizzato a un file. Se un'applicazione elabora l'output multilingue che può essere reindirizzato, determinare se l'handle di output è un handle della console (un metodo consiste nel chiamare la funzione [**GetConsoleMode**](getconsolemode.md) e controllare se ha esito positivo). Se l'handle è un handle di console, chiamare **WriteConsole** . Se l'handle non è un handle di console, l'output viene reindirizzato ed è necessario chiamare [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) per eseguire l'i/O. Assicurarsi di anteporre un prefisso a un file di testo normale Unicode con un byte order mark. Per ulteriori informazioni, vedere [utilizzo dei byte order mark](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Sebbene un'applicazione possa usare **WriteConsole** in modalità ANSI per scrivere caratteri ANSI, le console di non supportano le sequenze "escape ANSI" o "terminale virtuale", a meno che non siano abilitate. Per ulteriori informazioni e per l'applicabilità della versione del sistema operativo, vedere [**sequenze di terminali virtuali della console**](console-virtual-terminal-sequences.md) .

Quando le sequenze di escape di terminali virtuali non sono abilitate, le funzioni della console possono fornire funzionalità equivalenti. Per ulteriori informazioni, vedere [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)e [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **WriteConsoleW** (Unicode) e **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

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

[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
