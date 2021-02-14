---
title: ReadConsole (funzione)
description: Legge l'input di caratteri dal buffer di input della console e lo rimuove dal buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358281"
---
# <a name="readconsole-function"></a>ReadConsole (funzione)

Legge l'input di caratteri dal buffer di input della console e lo rimuove dal buffer.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a>Parametri

*hConsoleInput* \[ in\]  
Handle per il buffer di input della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ out\]  
Puntatore a un buffer che riceve i dati letti dal buffer di input della console.

*nNumberOfCharsToRead* \[ in\]  
Numero di caratteri da leggere. La dimensione del buffer a cui punta il parametro *lpBuffer* deve essere di almeno `nNumberOfCharsToRead * sizeof(TCHAR)` byte.

*lpNumberOfCharsRead* \[ out\]  
Puntatore a una variabile che riceve il numero di caratteri effettivamente letti.

*pInputControl* \[ in, facoltativo\]  
Puntatore a una struttura [**di \_ \_ controllo READCONSOLE della console**](console-readconsole-control.md) che specifica un carattere di controllo per segnalare la fine dell'operazione di lettura. Questo parametro può essere **NULL**.

Per impostazione predefinita, questo parametro richiede l'input Unicode. Per la modalità ANSI, impostare questo parametro su **null**.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

**ReadConsole** legge l'input da tastiera da un buffer di input della console. Si comporta come la funzione [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) , ad eccezione del fatto che può leggere in modalità Unicode (wide character) o ANSI. Per avere applicazioni che gestiscono un singolo set di origini compatibili con entrambe le modalità, usare **ReadConsole** anziché **ReadFile**. Sebbene **ReadConsole** possa essere usato solo con un handle del buffer di input della console, **ReadFile** può essere usato con altri handle, ad esempio file o pipe. **ReadConsole** ha esito negativo se usato con un handle standard che è stato reindirizzato a un elemento diverso da un handle di console.

Tutte le modalità di input che influiscono sul comportamento di [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) hanno lo stesso effetto su **ReadConsole**. Per recuperare e impostare le modalità di input di un buffer di input della console, usare le funzioni [**GetConsoleMode**](getconsolemode.md) e [**SetConsoleMode**](setconsolemode.md) .

Se il buffer di input contiene eventi di input diversi dagli eventi di tastiera, ad esempio gli eventi del mouse o gli eventi di ridimensionamento delle finestre, vengono eliminati. Questi eventi possono essere letti solo tramite la funzione [**ReadConsoleInput**](readconsoleinput.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

Il parametro *pInputControl* può essere usato per abilitare riattivazioni intermedie dalla lettura in risposta a un carattere di controllo di completamento file specificato in una struttura di [**\_ \_ controllo READCONSOLE console**](console-readconsole-control.md) . Questa funzionalità richiede l'abilitazione delle estensioni del comando, l'handle di output standard come handle di output della console e l'input come Unicode.

**Windows Server 2003 e Windows XP/2000:** La funzionalità di lettura intermedia non è supportata.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **ReadConsoleW** (Unicode) e **ReadConsoleA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**\_controllo READCONSOLE \_ console**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Metodi di input e output](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)