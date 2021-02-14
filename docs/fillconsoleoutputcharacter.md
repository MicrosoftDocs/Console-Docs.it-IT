---
title: FillConsoleOutputCharacter (funzione)
description: Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 95efbcc261943a2986fe6fbb1f3d54aaae1b2d2b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357511"
---
# <a name="fillconsoleoutputcharacter-function"></a>FillConsoleOutputCharacter (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Scrive un carattere nel buffer dello schermo della console per un numero specificato di volte, a partire dalle coordinate specificate.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*cCharacter* \[ in\]  
Carattere da scrivere nel buffer dello schermo della console.

*nLength* \[ in\]  
Numero di celle di caratteri in cui deve essere scritto il carattere.

*dwWriteCoord* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica le coordinate dei caratteri della prima cella in cui deve essere scritto il carattere.

*lpNumberOfCharsWritten* \[ out\]  
Puntatore a una variabile che riceve il numero di caratteri effettivamente scritti nel buffer dello schermo della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Se il numero di caratteri in cui scrivere si estende oltre la fine della riga specificata nel buffer dello schermo della console, i caratteri vengono scritti nella riga successiva. Se il numero di caratteri in cui scrivere si estende oltre la fine del buffer dello schermo della console, i caratteri vengono scritti fino alla fine del buffer dello schermo della console.

I valori di attributo nelle posizioni scritte non vengono modificati.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** specifico. Il riempimento dell'area esterna alla finestra visualizzabile non è supportato ed è riservato per lo spazio della cronologia del terminale. Il riempimento di un'area visibile con nuovo testo o colore viene eseguito tramite **[lo scorrimento del cursore](console-virtual-terminal-sequences.md#cursor-positioning)**, **[l'impostazione dei nuovi attributi](console-virtual-terminal-sequences.md#text-formatting)**, la scrittura del testo desiderato per l'area, la ripetizione dei caratteri, se necessario, per la durata dell'esecuzione del riempimento. È possibile che venga richiesto lo spostamento del cursore aggiuntivo seguito dalla scrittura del testo desiderato per riempire un'area rettangolare. Si prevede che l'applicazione client mantenga la propria memoria dello schermo e non sia in grado di eseguire query sullo stato remoto. Altre informazioni sono reperibili nella documentazione della **[console classica rispetto al terminale virtuale](classic-vs-vt.md)** .

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **FillConsoleOutputCharacterW** (Unicode) e **FillConsoleOutputCharacterA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**COORD**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)