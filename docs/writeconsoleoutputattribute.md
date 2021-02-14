---
title: WriteConsoleOutputAttribute (funzione)
description: Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4c940243b8367e2f66923c14ffa90de7c9a384b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357761"
---
# <a name="writeconsoleoutputattribute-function"></a>WriteConsoleOutputAttribute (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copia un numero di attributi carattere in celle consecutive di un buffer dello schermo della console, a partire da una posizione specificata.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpAttribute* \[ in\]  
Attributi da utilizzare durante la scrittura nel buffer dello schermo della console. Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).

*nLength* \[ in\]  
Numero di celle di caratteri del buffer dello schermo in cui verranno copiati gli attributi.

*dwWriteCoord* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella nel buffer dello schermo della console in cui verranno scritti gli attributi.

*lpNumberOfAttrsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di attributi effettivamente scritti nel buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Se il numero di attributi da scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, gli attributi vengono scritti nella riga successiva. Se il numero di attributi da scrivere si estende oltre la fine del buffer dello schermo della console, gli attributi vengono scritti fino alla fine del buffer dello schermo della console.

I valori di carattere nelle posizioni scritte in non vengono modificati.

> [!TIP]
> Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** . Spostare il cursore nella posizione da inserire, applicare la formattazione desiderata e scrivere il testo da riempire. Non esiste alcun equivalente per applicare il colore a un'area senza emettere anche testo. Questa decisione allinea intenzionalmente la piattaforma Windows con altri sistemi operativi in cui è previsto che la singola applicazione client memorizzi il proprio stato disegnato per un'ulteriore manipolazione.

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

[**COORD**](coord-str.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)