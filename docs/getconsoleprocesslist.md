---
title: GetConsoleProcessList (funzione)
description: Vedere le informazioni di riferimento sulla funzione GetConsoleProcessList, che recupera un elenco dei processi collegati alla console corrente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bfc16edccb2f1be2b22c81992800d8f62d86cf4f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037984"
---
# <a name="getconsoleprocesslist-function"></a>GetConsoleProcessList (funzione)

Recupera un elenco dei processi collegati alla console corrente.

## <a name="syntax"></a>Sintassi

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a>Parametri

*lpdwProcessList* \[ out\]  
Puntatore a un buffer che riceve una matrice di identificatori di processo al completamento dell'operazione. Deve essere un buffer valido e non può essere `NULL` . Il buffer deve avere spazio per ricevere almeno 1 ID processo restituito.

*dwProcessCount* \[ in\]  
Numero massimo di identificatori di processo che è possibile archiviare nel buffer *lpdwProcessList* . Deve essere maggiore di 0.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è minore o uguale a *dwProcessCount* e rappresenta il numero di identificatori di processo archiviati nel buffer *lpdwProcessList* .

Se il buffer è troppo piccolo per conservare tutti gli identificatori di processo validi, il valore restituito è il numero necessario di elementi di matrice. La funzione non avrà archiviato identificatori nel buffer. In questa situazione, utilizzare il valore restituito per allocare un buffer sufficientemente grande da archiviare l'intero elenco e chiamare di nuovo la funzione.

Se il valore restituito è zero, la funzione non è riuscita perché a ogni console è associato almeno un processo. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Se `NULL` è stato specificato un elenco di processi o il numero di processi è pari a 0, la chiamata restituirà 0 e restituirà `GetLastError` `ERROR_INVALID_PARAMETER` . Fornire un buffer di almeno un elemento per chiamare questa funzione. Allocare un buffer più grande e chiamare di nuovo se il codice restituito è più grande della lunghezza del buffer fornito.

## <a name="remarks"></a>Commenti

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[**AttachConsole**](attachconsole.md)

[Funzioni console](console-functions.md)
