---
title: WriteConsoleOutput (funzione)
description: Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 1f10285cfc5c671ac5d31b8a575e84b1fd0f6a14
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359031"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Scrive i dati dell'attributo character e color in un blocco rettangolare specificato di celle di tipo carattere in un buffer dello schermo della console. I dati da scrivere vengono ricavati da un blocco rettangolare di dimensioni corrispondenti in una posizione specificata nel buffer di origine.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_WRITE**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Dati da scrivere nel buffer dello schermo della console. Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [**\_ informazioni char**](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .

*dwBufferSize* \[ in\]  
Dimensioni del buffer a cui punta il parametro *lpBuffer* , in celle di tipo carattere. Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.

*dwBufferCoord* \[ in\]  
Coordinate della cella superiore sinistra nel buffer a cui punta il parametro *lpBuffer* . Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.

*lpWriteRegion* \[ in uscita\]  
Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) . In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console in cui scrivere. Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

**WriteConsoleOutput** considera il buffer di origine e il buffer dello schermo di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere). Il rettangolo a cui punta il parametro *lpWriteRegion* specifica le dimensioni e la posizione del blocco in cui scrivere nel buffer dello schermo della console. Un rettangolo con le stesse dimensioni si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* . I dati delle celle presenti nell'intersezione tra il rettangolo e il rettangolo del buffer di origine (le cui dimensioni sono specificate dal parametro *dwBufferSize* ) vengono scritti nel rettangolo di destinazione.

Le celle nel rettangolo di destinazione il cui percorso di origine corrispondente si trova al di fuori dei limiti del rettangolo del buffer di origine non vengono influenzate dall'operazione di scrittura. In altre parole, queste sono le celle per le quali non sono disponibili dati da scrivere.

Prima della restituzione di **WriteConsoleOutput** , imposta i membri di *lpWriteRegion* sul rettangolo del buffer dello schermo effettivo interessato dall'operazione di scrittura. Questo rettangolo riflette le celle del rettangolo di destinazione per cui esiste una cella corrispondente nel buffer di origine, perché **WriteConsoleOutput** Ritaglia le dimensioni del rettangolo di destinazione ai limiti del buffer dello schermo della console.

Se il rettangolo specificato da *lpWriteRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di origine, non viene scritto alcun dato. In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpWriteRegion* , in modo tale che il membro **destro** sia minore della **sinistra** o che il membro **inferiore** sia minore della **parte superiore**. Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

**WriteConsoleOutput** non ha alcun effetto sulla posizione del cursore.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Questa API ha un **[terminale virtuale](console-virtual-terminal-sequences.md)** equivalente nelle sequenze di **[formattazione del testo](console-virtual-terminal-sequences.md#text-formatting)** e posizionamento del **[cursore](console-virtual-terminal-sequences.md#cursor-positioning)** . Spostare il cursore sul percorso da inserire, applicare la formattazione desiderata e scrivere il testo. Le _sequenze di terminali virtuali_ sono consigliate per lo sviluppo nuovo e continuo.

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
| Nomi Unicode e ANSI | **WriteConsoleOutputW** (Unicode) e **WriteConsoleOutputA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[**\_informazioni char**](char-info-str.md)

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**\_Rect piccolo**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)