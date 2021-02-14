---
title: WriteConsoleInput (funzione)
description: Vedere informazioni di riferimento sulla funzione WriteConsoleInput, che consente di scrivere dati direttamente nel buffer di input della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e4b9cdae52da2e23ff93e1904c4cb24ebac62831
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357781"
---
# <a name="writeconsoleinput-function"></a>WriteConsoleInput (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Scrive i dati direttamente nel buffer di input della console.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a>Parametri

*hConsoleInput* \[ in\]  
Handle per il buffer di input della console. L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Puntatore a una matrice di strutture [**di \_ record di input**](input-record-str.md) che contengono dati da scrivere nel buffer di input.

*nLength* \[ in\]  
Numero di record di input da scrivere.

*lpNumberOfEventsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di record di input effettivamente scritti.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

**WriteConsoleInput** inserisce i record di input nel buffer di input dietro tutti gli eventi in sospeso nel buffer. Il buffer di input aumenta in modo dinamico, se necessario, per mantenere il numero di eventi scritti.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** . Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi. Questa operazione viene considerata come un **[verbo errato](console-buffer-security-and-access-rights.md#wrong-way-verbs)** per questo buffer. Le applicazioni remote con utilità multipiattaforma e trasporti come SSH potrebbero non funzionare come previsto se si usa questa API.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **WriteConsoleInputW** (Unicode) e **WriteConsoleInputA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**RECORD di INPUT \_**](input-record-str.md)

[Funzioni di input della console di basso livello](low-level-console-input-functions.md)

[**MapVirtualKey**](/windows/win32/api/winuser/nf-winuser-mapvirtualkeya)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](/windows/win32/api/winuser/nf-winuser-vkkeyscana)