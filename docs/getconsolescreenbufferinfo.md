---
title: GetConsoleScreenBufferInfo (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleScreenBufferInfo, che recupera le informazioni sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358911"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo (funzione)

Recupera le informazioni sul buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfo* \[ out\]  
Puntatore a una struttura [**di \_ \_ \_ informazioni sul buffer dello schermo della console**](console-screen-buffer-info-str.md) che riceve le informazioni sul buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Il rettangolo restituito nel membro **srWindow** della struttura di [**\_ informazioni sul \_ buffer \_ dello schermo della console**](console-screen-buffer-info-str.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.

Tutte le coordinate restituite nella struttura delle [**\_ \_ \_ informazioni del buffer dello schermo della console**](console-screen-buffer-info-str.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.

> [!TIP]
> Questa API non ha un equivalente del **[terminale virtuale](console-virtual-terminal-sequences.md)** . Il suo utilizzo potrebbe essere ancora necessario per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione per recuperare le dimensioni della finestra. Questo stato della finestra viene gestito da TTY/PTY/Pseudoconsole all'esterno del flusso di flusso normale ed è in genere considerato un privilegio utente non modificabile dall'applicazione client. Gli aggiornamenti possono essere ricevuti in [**ReadConsoleInput**](readconsoleinput.md).

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).

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

[**\_informazioni sul \_ buffer dello schermo della console \_**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Dimensioni del buffer della finestra e dello schermo](window-and-screen-buffer-size.md)