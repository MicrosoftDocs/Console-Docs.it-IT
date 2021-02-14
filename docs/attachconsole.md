---
title: AttachConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione AttachConsole, che consente di alleghi il processo chiamante alla console del processo specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357841"
---
# <a name="attachconsole-function"></a>AttachConsole (funzione)

Connette il processo chiamante alla console del processo specificato come applicazione client.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a>Parametri

*dwProcessId* \[ in\]  
Identificatore del processo di cui si desidera utilizzare la console. Questo parametro può avere uno dei valori seguenti.

| Valore | Significato |
|-|-|
| *pid* | Utilizzare la console del processo specificato. |
| **Connetti \_ \_processo padre**`(DWORD)-1` | Utilizzare la console dell'elemento padre del processo corrente. |

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Un processo può essere collegato al massimo da una console. Se il processo chiamante è già collegato a una console, il codice di errore restituito è **errore \_ accesso \_ negato** ( `5` ). Se il processo specificato non dispone di una console, il codice di errore restituito **è \_ errore \_ handle non valido** ( `6` ). Se il processo specificato non esiste, il codice di errore restituito è **errore \_ \_ parametro non valido** ( `87` ).

Un processo può utilizzare la funzione [**FreeConsole**](freeconsole.md) per scollegarsi dalla console. Se altri processi condividono la console, la console non viene distrutta, ma il processo che ha chiamato **FreeConsole** non può farvi riferimento. Una console viene chiusa quando l'ultimo processo collegato termina o chiama **FreeConsole**. Dopo che un processo chiama **FreeConsole**, può chiamare la funzione [**AllocConsole**](allocconsole.md) per creare una nuova console o **AttachConsole** per connettersi a un'altra console.

Questa funzione è utile principalmente per le applicazioni collegate con [**/SUBSYSTEM: Windows**](/cpp/build/reference/subsystem-specify-subsystem), che implica al sistema operativo che non è necessaria una console prima di immettere il metodo Main del programma. In tal caso, gli handle standard recuperati con [**GetStdHandle**](getstdhandle.md) probabilmente non saranno validi all'avvio fino a quando non viene chiamato **AttachConsole** . L'eccezione è rappresentata dall'avvio dell'applicazione con la gestione dell'ereditarietà da parte del processo padre.

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come `0x0501` o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | ConsoleApi.h (tramite WinCon.h, con Windows.h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Console](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)