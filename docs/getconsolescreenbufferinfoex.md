---
title: GetConsoleScreenBufferInfoEx (funzione)
description: Recupera le informazioni estese sul buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 482aaefbeed22475f6f9301d13f480ba5a416fa9
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358901"
---
# <a name="getconsolescreenbufferinfoex-function"></a>GetConsoleScreenBufferInfoEx (funzione)

Recupera le informazioni estese sul buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpConsoleScreenBufferInfoEx* \[ out\]  
Struttura [**\_ INFOEX del \_ buffer \_ dello schermo della console**](console-screen-buffer-infoex.md) che riceve le informazioni sul buffer dello schermo della console richieste.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Il rettangolo restituito nel membro **srWindow** della struttura [**INFOEX del \_ \_ buffer dello \_ schermo della console**](console-screen-buffer-infoex.md) può essere modificato e quindi passato alla funzione [**SetConsoleWindowInfo**](setconsolewindowinfo.md) per scorrere il buffer dello schermo della console nella finestra, per modificare le dimensioni della finestra o entrambi.

Tutte le coordinate restituite nella struttura [**\_ \_ \_ INFOEX buffer dello schermo della console**](console-screen-buffer-infoex.md) si trovano in coordinate di celle di tipo carattere, dove l'origine (0,0) si trova nell'angolo superiore sinistro del buffer dello schermo della console.

> [!TIP]
> Questa API non ha un equivalente del **[terminale virtuale](console-virtual-terminal-sequences.md)** . Il suo utilizzo potrebbe essere ancora necessario per le applicazioni che tentano di creare colonne, griglie o riempire la visualizzazione per recuperare le dimensioni della finestra. Questo stato della finestra viene gestito da TTY/PTY/Pseudoconsole all'esterno del flusso di flusso normale ed è in genere considerato un privilegio utente non modificabile dall'applicazione client. Gli aggiornamenti possono essere ricevuti in [**ReadConsoleInput**](readconsoleinput.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop di Windows Vista\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2008\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**\_INFOEX buffer dello schermo della console \_ \_**](console-screen-buffer-infoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)