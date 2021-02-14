---
title: GenerateConsoleCtrlEvent (funzione)
description: Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357531"
---
# <a name="generateconsolectrlevent-function"></a>GenerateConsoleCtrlEvent (funzione)

Invia un segnale specificato a un gruppo di processi della console che condivide la console di associata al processo chiamante.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a>Parametri

*dwCtrlEvent* \[ in\]  
Tipo di segnale da generare. Questo parametro può avere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| **CTRL_C_EVENT** 0 | Genera un segnale CTRL + C. Non è possibile generare questo segnale per i gruppi di processi. Se *dwProcessGroupId* è diverso da zero, questa funzione avrà esito positivo, ma il segnale CTRL + C non verrà ricevuto dai processi all'interno del gruppo di processi specificato. |
| **CTRL_BREAK_EVENT** 1 | Genera un segnale CTRL + BREAK. |

*dwProcessGroupId* \[ in\]  
Identificatore del gruppo di processi per ricevere il segnale. Un gruppo di processi viene creato quando il flag **Crea \_ nuovo \_ \_ gruppo di processi** viene specificato in una chiamata alla funzione [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) . L'identificatore del processo del nuovo processo è anche l'identificatore del gruppo di processi di un nuovo gruppo di processi. Il gruppo di processi include tutti i processi discendenti dal processo radice. Solo i processi del gruppo che condividono la stessa console del processo chiamante ricevono il segnale. In altre parole, se un processo del gruppo crea una nuova console, il processo non riceve il segnale, né i relativi discendenti.

Se questo parametro è zero, il segnale viene generato in tutti i processi che condividono la console del processo chiamante.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

**GenerateConsoleCtrlEvent** fa sì che vengano chiamate le funzioni del gestore di controllo dei processi nel gruppo di destinazione. Tutti i processi della console hanno una funzione di gestione predefinita che chiama la funzione [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) . Un processo console può utilizzare la funzione [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) per installare o rimuovere altre funzioni del gestore.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) può anche abilitare un attributo ereditabile che fa in modo che il processo chiamante ignori i segnali CTRL + C. Se **GenerateConsoleCtrlEvent** Invia un segnale CTRL + C a un processo per il quale questo attributo è abilitato, le funzioni del gestore per tale processo non vengono chiamate. I segnali CTRL + BREAK determinano sempre la chiamata delle funzioni del gestore.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Gestori di controllo della console](console-control-handlers.md)

[Funzioni della console](console-functions.md)

[**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)