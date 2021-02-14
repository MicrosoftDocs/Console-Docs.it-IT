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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358751"
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

*nStdHandle* \[in\]  
Il dispositivo standard. Questo parametro può avere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | Il dispositivo di input standard. Inizialmente si tratta del buffer di input della console, ovvero `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | Il dispositivo di output standard. Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | Il dispositivo di errore standard. Inizialmente si tratta del buffer dello schermo della console attivo, ovvero `CONOUT$`. |

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è un handle per il dispositivo specificato o un handle reindirizzato impostato da una chiamata precedente su [**SetStdHandle**](setstdhandle.md). L'handle dispone dei diritti di accesso **GENERIC\_READ** e **GENERIC\_WRITE**, a meno che l'applicazione non abbia usato **SetStdHandle** per impostare un handle standard con un livello di accesso inferiore.

Se la funzione ha esito negativo, il valore restituito è **INVALID\_HANDLE\_VALUE**. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

Se a un'applicazione non sono associati handle standard, ad esempio un servizio in esecuzione su un desktop interattivo, e non sono stati reindirizzati, il valore restituito sarà **NULL**.

## <a name="remarks"></a>Osservazioni

Gli handle restituiti da **GetStdHandle** possono essere usati dalle applicazioni che devono leggere o scrivere nella console. Al momento della creazione di una console, l'handle di input standard è un handle per il buffer di input della console e gli handle di output standard e di errore standard sono handle del buffer dello schermo attivo della console. Questi handle possono essere usati dalle funzioni [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) e [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o da qualsiasi funzione della console che accede al buffer di input della console o a un buffer dello schermo, ad esempio [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Gli handle standard di un processo possono essere reindirizzati da una chiamata a [**SetStdHandle**](setstdhandle.md), nel qual caso **GetStdHandle** restituisce l'handle reindirizzato. Se gli handle standard sono stati reindirizzati, è possibile specificare il valore `CONIN$` in una chiamata alla funzione [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) per ottenere un handle per il buffer di input di una console. Analogamente, è possibile specificare il valore `CONOUT$` per ottenere un handle per il buffer dello schermo attivo di una console.

Gli handle standard di un processo all'immissione del metodo principale sono determinati dalla configurazione del flag [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) passato al linker al momento della compilazione dell'applicazione. Se si specifica **/SUBSYSTEM:CONSOLE**, si richiede al sistema operativo di riempire gli handle con una sessione della console all'avvio, se il padre non ha già riempito la tabella di handle standard mediante ereditarietà. Viceversa, **/SUBSYSTEM:WINDOWS** implica che l'applicazione non necessita di una console e probabilmente non userà gli handle standard. Altre informazioni sull'ereditarietà degli handle sono disponibili nella documentazione relativa a [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Alcune applicazioni operano all'esterno dei limiti del sottosistema dichiarato. Ad esempio, un'applicazione **/SUBSYSTEM:WINDOWS** potrebbe controllare/usare gli handle standard per la registrazione o il debug, ma funzionare normalmente con un'interfaccia utente grafica. Queste applicazioni dovranno verificare accuratamente lo stato degli handle standard all'avvio e usare [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) per aggiungere/rimuovere una console, se necessario.

Alcune applicazioni possono anche variare il comportamento in base al tipo di handle ereditato. La distinzione del tipo tra console, pipe, file e altri può essere eseguita con [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportamento di collegamento/scollegamento

Quando ci si collega a una nuova console, gli handle standard vengono sempre sostituiti con gli handle della console, a meno che non sia stato specificato **STARTF\_USESTDHANDLES** durante la creazione del processo.

Se il valore esistente dell'handle standard è **NULL** o se ha l'aspetto di uno pseudohandle della console, l'handle viene sostituito con un handle della console.

Quando un padre usa sia **CREATE\_NEW\_CONSOLE** che **STARTF\_USESTDHANDLES** per creare un processo della console, gli handle standard non verranno sostituiti, a meno che il valore esistente dell'handle standard non sia **NULL** o uno pseudohandle della console.

> [!NOTE]
>I processi della console *devono* iniziare con gli handle standard riempiti, altrimenti verranno riempiti automaticamente con gli handle appropriati per una nuova console. Le applicazioni GUI (interfaccia utente grafica) possono essere avviate senza gli handle standard e non verranno riempite automaticamente.

## <a name="examples"></a>Esempi

Un esempio è disponibile in [Lettura di eventi del buffer di input](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ProcessEnv.h (tramite Winbase.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Handle della console](console-handles.md)

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)