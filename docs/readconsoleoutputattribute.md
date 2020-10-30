---
title: ReadConsoleOutputAttribute (funzione)
description: Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f64e39b7b68e24e6c2aa7e9704c285bbbbc234f0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039509"
---
# <a name="readconsoleoutputattribute-function"></a>ReadConsoleOutputAttribute (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copia un numero specificato di attributi di caratteri da celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpAttribute* \[ out\]  
Puntatore a un buffer che riceve gli attributi utilizzati dal buffer dello schermo della console.

Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).

*nLength* \[ in\]  
Numero di celle di caratteri del buffer dello schermo da cui eseguire la lettura. La dimensione del buffer a cui punta il parametro *lpAttribute* deve essere `nLength * sizeof(WORD)` .

*dwReadCoord* \[ in\]  
Coordinate della prima cella nel buffer dello schermo della console da cui leggere, in caratteri. Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.

*lpNumberOfAttrsRead* \[ out\]  
Puntatore a una variabile che riceve il numero di attributi effettivamente letti.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Se il numero di attributi da leggere da si estende oltre la fine della riga del buffer dello schermo specificata, gli attributi vengono letti dalla riga successiva. Se il numero di attributi da leggere da si estende oltre la fine del buffer dello schermo della console, vengono letti gli attributi fino alla fine del buffer dello schermo della console.

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Funzioni console](console-functions.md)

[**COORD**](coord-str.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
