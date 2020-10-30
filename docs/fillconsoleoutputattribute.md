---
title: FillConsoleOutputAttribute (funzione)
description: Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039069"
---
# <a name="fillconsoleoutputattribute-function"></a>FillConsoleOutputAttribute (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta gli attributi carattere per un numero specificato di celle di caratteri, a partire dalle coordinate specificate in un buffer dello schermo.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ scrittura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*wAttribute* \[ in\]  
Attributi da utilizzare durante la scrittura nel buffer dello schermo della console. Per altre informazioni, vedere [attributi carattere](console-screen-buffers.md#character-attributes).

*nLength* \[ in\]  
Numero di celle di tipo carattere da impostare sugli attributi di colore specificati.

*dwWriteCoord* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella i cui attributi devono essere impostati.

*lpNumberOfAttrsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di celle di tipo carattere i cui attributi sono stati effettivamente impostati.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Se il numero di celle di tipo carattere i cui attributi devono essere impostati si estende oltre la fine della riga specificata nel buffer dello schermo della console, vengono impostate le celle della riga successiva. Se il numero di celle in cui scrivere si estende oltre la fine del buffer dello schermo della console, le celle vengono scritte fino alla fine del buffer dello schermo della console.

I valori di carattere nelle posizioni scritte in non vengono modificati.

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** specifico. Il riempimento dell'area esterna alla finestra visualizzabile non è supportato ed è riservato per lo spazio della cronologia del terminale. Il riempimento di un'area visibile con nuovo testo o colore viene eseguito tramite **[lo scorrimento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)** , **[l'impostazione dei nuovi attributi](console-virtual-terminal-sequences.md#text-formatting)** , la scrittura del testo desiderato per l'area, la ripetizione dei caratteri, se necessario, per la durata dell'esecuzione del riempimento. È possibile che venga richiesto lo spostamento del cursore aggiuntivo seguito dalla scrittura del testo desiderato per riempire un'area rettangolare. Si prevede che l'applicazione client mantenga la propria memoria dello schermo e non sia in grado di eseguire query sullo stato remoto. Altre informazioni sono reperibili nella documentazione della **[console classica rispetto al terminale virtuale](classic-vs-vt.md)** .

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

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
