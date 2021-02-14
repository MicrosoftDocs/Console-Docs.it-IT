---
title: CreateConsoleScreenBuffer (funzione)
description: La funzione CreateConsoleScreenBuffer crea un buffer dello schermo per la console di Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357961"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Crea un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a>Parametri

*dwDesiredAccess* \[ in\]  
Accesso al buffer dello schermo della console. Per un elenco dei diritti di accesso, vedere [diritti di accesso e sicurezza del buffer della console](console-buffer-security-and-access-rights.md).

*dwShareMode* \[ in\]  
Questo parametro può essere zero, a indicare che il buffer non può essere condiviso oppure può essere uno o più dei valori seguenti.

| Valore | Significato |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | È possibile eseguire altre operazioni aperte sul buffer dello schermo della console per l'accesso in lettura. |
| **FILE_SHARE_WRITE** 0x00000002 | È possibile eseguire altre operazioni aperte sul buffer dello schermo della console per l'accesso in scrittura. |

*lpSecurityAttributes* \[ in, facoltativo\]  
Puntatore a una struttura [**di \_ attributi di sicurezza**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) che determina se l'handle restituito può essere ereditato dai processi figlio. Se *lpSecurityAttributes* è **null**, l'handle non può essere ereditato. Il membro **lpSecurityDescriptor** della struttura specifica un descrittore di sicurezza per il nuovo buffer dello schermo della console. Se *lpSecurityAttributes* è **null**, il buffer dello schermo della console ottiene un descrittore di sicurezza predefinito. Gli ACL nel descrittore di sicurezza predefinito per un buffer dello schermo della console provengono dal token primario o di rappresentazione del creatore.

*dwFlags* \[ in\]  
Tipo di buffer dello schermo della console da creare. L'unico tipo di buffer dello schermo supportato è il **\_ \_ buffer testuale della console**.

*lpScreenBufferData*  
Riservati deve essere **null**.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è un handle per il nuovo buffer dello schermo della console.

Se la funzione ha esito negativo, il valore restituito è **INVALID\_HANDLE\_VALUE**. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Una console può avere più buffer dello schermo, ma solo un buffer attivo dello schermo. È possibile accedere ai buffer dello schermo inattivi per la lettura e la scrittura, ma viene visualizzato solo il buffer attivo dello schermo. Per fare in modo che la nuova schermata ripresenti il buffer dello schermo attivo, utilizzare la funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .

Il buffer dello schermo appena creato copierà alcune proprietà dal buffer dello schermo attivo nel momento in cui viene chiamata la funzione. Il comportamento è il seguente:

- `Font` -copiato dal buffer dello schermo attivo
- `Display Window Size` -copiato dal buffer dello schermo attivo
- `Buffer Size` -corrispondente a `Display Window Size` (**non** copiato)
- `Default Attributes` (colori)-copiato dal buffer dello schermo attivo
- `Default Popup Attributes` (colori)-copiato dal buffer dello schermo attivo

Il processo chiamante può usare l'handle restituito in qualsiasi funzione che richiede un handle a un buffer dello schermo della console, in base alle limitazioni di accesso specificate dal parametro *dwDesiredAccess* .

Il processo chiamante può utilizzare la funzione [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) per creare un handle duplicato del buffer dello schermo con accesso o ereditarietà diversi dall'handle originale. Tuttavia, non è possibile usare **DuplicateHandle** per creare un duplicato valido per un processo diverso (tranne tramite ereditarietà).

Per chiudere l'handle del buffer dello schermo della console, usare la funzione [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) .

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Esempio

Per un esempio, vedere [lettura e scrittura di blocchi di caratteri e attributi](reading-and-writing-blocks-of-characters-and-attributes.md).

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

[**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**attributi di sicurezza \_**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)