---
title: ReadConsoleOutput (funzione)
description: Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e scrive i dati nel buffer di destinazione.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c17f9c3b44ba0d64fcf47659cf24d08d5c76cfdc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358731"
---
# <a name="readconsoleoutput-function"></a>ReadConsoleOutput (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legge i dati degli attributi di tipo carattere e colore da un blocco rettangolare di celle di tipo carattere in un buffer dello schermo della console e la funzione scrive i dati in un blocco rettangolare in una posizione specificata nel buffer di destinazione.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ out\]  
Puntatore a un buffer di destinazione che riceve i dati letti dal buffer dello schermo della console. Questo puntatore viene considerato l'origine di una matrice bidimensionale di strutture di [**\_ informazioni char**](char-info-str.md) la cui dimensione è specificata dal parametro *dwBufferSize* .

*dwBufferSize* \[ in\]  
Dimensioni del parametro *lpBuffer* , in celle di tipo carattere. Il membro **X** della struttura [**Coord**](coord-str.md) è il numero di colonne; il membro **Y** è il numero di righe.

*dwBufferCoord* \[ in\]  
Coordinate della cella superiore sinistra nel parametro *lpBuffer* che riceve i dati letti dal buffer dello schermo della console. Il membro **X** della struttura [**Coord**](coord-str.md) è la colonna e il membro **Y** è la riga.

*lpReadRegion* \[ in uscita\]  
Puntatore a una struttura [**di \_ Rect di piccole dimensioni**](small-rect-str.md) . In input, i membri della struttura specificano le coordinate in alto a sinistra e in basso a destra del rettangolo del buffer dello schermo della console da cui la funzione deve essere letta. Nell'output, i membri della struttura specificano il rettangolo effettivo utilizzato.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

**ReadConsoleOutput** considera il buffer dello schermo della console e il buffer di destinazione come matrici bidimensionali (colonne e righe di celle di tipo carattere). Il rettangolo a cui punta il parametro *lpReadRegion* specifica le dimensioni e la posizione del blocco da leggere dal buffer dello schermo della console. Un rettangolo di destinazione della stessa dimensione si trova con la cella superiore sinistra in corrispondenza delle coordinate del parametro *dwBufferCoord* nella matrice *lpBuffer* . I dati letti dalle celle del rettangolo di origine buffer dello schermo della console vengono copiati nelle celle corrispondenti nel buffer di destinazione. Se la cella corrispondente non rientra nei limiti del rettangolo del buffer di destinazione (le cui dimensioni sono specificate dal parametro *dwBufferSize* ), i dati non vengono copiati.

Le celle del buffer di destinazione corrispondenti alle coordinate che non rientrano nei limiti del buffer dello schermo della console rimangono invariate. In altre parole, queste sono le celle per le quali non sono disponibili dati del buffer dello schermo da leggere.

Prima della restituzione di **ReadConsoleOutput** , imposta i membri della struttura a cui punta il parametro *lpReadRegion* sul rettangolo del buffer dello schermo effettivo le cui celle sono state copiate nel buffer di destinazione. Questo rettangolo riflette le celle del rettangolo di origine per cui esiste una cella corrispondente nel buffer di destinazione, perché **ReadConsoleOutput** Ritaglia le dimensioni del rettangolo di origine per adattarsi ai limiti del buffer dello schermo della console.

Se il rettangolo specificato da *lpReadRegion* si trova completamente all'esterno dei limiti del buffer dello schermo della console o se il rettangolo corrispondente è posizionato completamente all'esterno dei limiti del buffer di destinazione, non vengono copiati dati. In questo caso, la funzione restituisce con i membri della struttura a cui punta il set di parametri *lpReadRegion* , in modo tale che il membro **destro** sia minore della **sinistra** o che il membro **inferiore** sia minore della **parte superiore**. Per determinare le dimensioni del buffer dello schermo della console, usare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

La funzione **ReadConsoleOutput** non ha alcun effetto sulla posizione del cursore del buffer dello schermo della console. Il contenuto del buffer dello schermo della console non viene modificato dalla funzione.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

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
| Nomi Unicode e ANSI | **ReadConsoleOutputW** (Unicode) e **ReadConsoleOutputA** (ANSI) |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Funzioni di output della console di basso livello](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**\_Rect piccolo**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**\_informazioni char**](char-info-str.md)

[**COORD**](coord-str.md)