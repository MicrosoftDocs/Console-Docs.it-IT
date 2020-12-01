---
title: GetStdHandle (funzione)
description: Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
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
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420210"
---
# <a name="getstdhandle-function"></a>GetStdHandle (funzione)

Recupera un handle per il dispositivo standard specificato (input standard, output standard o errore standard).

## <a name="syntax"></a>Sintassi

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Parametri

*nStdHandle* \[ in\]  
Il dispositivo standard. Questo parametro può essere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Dispositivo di input standard. Inizialmente, si tratta del buffer di input della console `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Dispositivo di output standard. Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Dispositivo di errore standard. Inizialmente, si tratta del buffer dello schermo della console attivo, `CONOUT$` . |

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente a [**SetStdHandle**](setstdhandle.md). L'handle dispone di diritti di accesso di **\_ lettura** e **\_ scrittura** generici, a meno che l'applicazione non abbia utilizzato **SetStdHandle** per impostare un handle standard con accesso minore.

Se la funzione ha esito negativo, il valore restituito è un **\_ \_ valore di handle non valido**. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo e non è stato reindirizzato, il valore restituito è **null**.

## <a name="remarks"></a>Commenti

Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console. Quando viene creata una console, l'handle di input standard è un handle per il buffer di input della console e l'output standard e gli handle di errore standard sono handle del buffer dello schermo attivo della console. Questi handle possono essere usati dalle funzioni [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) e [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o da qualsiasi funzione console che accede al buffer di input della console o a un buffer dello schermo (ad esempio, le funzioni [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato. Se gli handle standard sono stati reindirizzati, è possibile specificare il `CONIN$` valore in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) per ottenere un handle per il buffer di input di una console. Analogamente, è possibile specificare il `CONOUT$` valore per ottenere un handle per il buffer dello schermo attivo di una console.

Gli handle standard di un processo all'immissione del metodo Main sono determinati dalla configurazione del flag [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) passato al linker quando è stata compilata l'applicazione. Specificando **/SUBSYSTEM: console** richiede che il sistema operativo riempia gli handle con una sessione della console all'avvio, se l'elemento padre non ha già riempito la tabella di handle standard in base all'ereditarietà. Al contrario, **/SUBSYSTEM: Windows** implica che l'applicazione non necessita di una console e probabilmente non utilizzerà gli handle standard. Altre informazioni sull'ereditarietà dell'handle sono reperibili nella documentazione di [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Alcune applicazioni operano all'esterno dei limiti del sottosistema dichiarato; ad esempio, un'applicazione **/SUBSYSTEM: Windows** potrebbe controllare/utilizzare handle standard a scopo di registrazione o di debug, ma funzionare normalmente con un'interfaccia utente grafica. Queste applicazioni dovranno verificare accuratamente lo stato degli handle standard all'avvio e usare [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md)e [**FreeConsole**](freeconsole.md) per aggiungere o rimuovere una console, se necessario.

Alcune applicazioni possono anche variare il comportamento del tipo di handle ereditato. Distinguere il tipo tra la console, la pipe, il file e altri possono essere eseguiti con [**FileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportamento di collegamento/scollegamento

Quando ci si connette a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF \_ USESTDHANDLES** durante la creazione del processo.

Se il valore esistente dell'handle standard è **null** o il valore esistente dell'handle standard è simile a un pseudohandle della console, l'handle viene sostituito con un handle della console.

Quando un elemento padre usa sia **Create \_ New \_ console** che **STARTF \_ USESTDHANDLES** per creare un processo console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia **null** o un pseudohandle console.

> [!NOTE]
>I processi della console *devono* iniziare con gli handle standard pieni o verranno riempiti automaticamente con handle appropriati per una nuova console. Le applicazioni GUI (Graphical User Interface) possono essere avviate senza gli handle standard e non verranno compilate automaticamente.

## <a name="examples"></a>Esempi

Per un esempio, vedere [lettura degli eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ProcessEnv. h (tramite Winbase. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[Handle della console](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
