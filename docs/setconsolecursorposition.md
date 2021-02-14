---
title: SetConsoleCursorPosition (funzione)
description: Vedere le informazioni di riferimento sulla funzione SetConsoleCursorPosition, che imposta la posizione del cursore nel buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 48671b9c54e61733c2936ac1f112e2d499f31a1a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357671"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta la posizione del cursore nel buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*dwCursorPosition* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica la nuova posizione del cursore, in caratteri. Le coordinate sono la colonna e la riga di una cella del carattere del buffer dello schermo. Le coordinate devono trovarsi all'interno dei limiti del buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

La posizione del cursore determina la posizione in cui vengono visualizzati i caratteri scritti dalla funzione [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md) o con la funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) . Per determinare la posizione corrente del cursore, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

Se la nuova posizione del cursore non si trova all'interno dei limiti della finestra del buffer dello schermo della console, l'origine della finestra cambia per rendere visibile il cursore.

> [!TIP]
> Questa API dispone di un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sezioni **[posizionamento semplice del cursore](console-virtual-terminal-sequences.md#simple-cursor-positioning)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** . L'uso delle sequenze di nuova riga, ritorno a capo, BACKSPACE e controllo tab può supportare anche il posizionamento del cursore.

## <a name="examples"></a>Esempio

Per un esempio, vedere [uso delle funzioni di input e output di High-Level](using-the-high-level-input-and-output-functions.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Buffer dello schermo della console](console-screen-buffers.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)