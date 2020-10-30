---
title: ScrollConsoleScreenBuffer (funzione)
description: Vedere informazioni di riferimento sulla funzione ScrollConsoleScreenBuffer, che consente di spostare un blocco di dati in un buffer dello schermo.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4ebe6efa246d627add041a5ef188fbb81294fb61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039459"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sposta un blocco di dati in un buffer dello schermo. Gli effetti dello spostamento possono essere limitati specificando un rettangolo di ritaglio, in modo che il contenuto del buffer dello schermo della console all'esterno del rettangolo di ritaglio non sia modificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*lpScrollRectangle* \[ in\]  
Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console da spostare.

*lpClipRectangle* \[ in, facoltativo\]  
Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) i cui membri specificano le coordinate superiore sinistro e inferiore destra del rettangolo del buffer dello schermo della console interessato dallo scorrimento. Questo puntatore può essere **null** .

*dwDestinationOrigin* \[ in\]  
Struttura [**Coord**](coord-str.md) che specifica l'angolo superiore sinistro della nuova posizione del contenuto di *lpScrollRectangle* , in caratteri.

*lpFill* \[ in\]  
Puntatore a una struttura [**di \_ informazioni char**](char-info-str.md) che specifica gli attributi di caratteri e colori da utilizzare per riempire le celle all'interno dell'intersezione tra *lpScrollRectangle* e *lpClipRectangle* che sono stati lasciati vuoti come risultato dello spostamento.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

**ScrollConsoleScreenBuffer** copia il contenuto di un'area rettangolare di un buffer dello schermo, specificato dal parametro *lpScrollRectangle* , in un'altra area del buffer dello schermo della console. Il rettangolo di destinazione ha le stesse dimensioni del rettangolo *lpScrollRectangle* con l'angolo superiore sinistro in corrispondenza delle coordinate specificate dal parametro *dwDestinationOrigin* . Le parti di *lpScrollRectangle* che non si sovrappongono al rettangolo di destinazione vengono compilate con gli attributi di carattere e colore specificati dal parametro *lpFill* .

Il rettangolo di ritaglio si applica alle modifiche apportate sia nel rettangolo *lpScrollRectangle* che nel rettangolo di destinazione. Se, ad esempio, il rettangolo di ridimensionamento non include un'area che verrebbe compilata con il contenuto di *lpFill* , il contenuto originale dell'area viene lasciato invariato.

Se le aree di scorrimento o di destinazione si estendono oltre le dimensioni del buffer dello schermo della console, vengono ritagliate. Ad esempio, se *lpScrollRectangle* è l'area contenuta da (0,0) e (19, 19) e *dwDestinationOrigin* è (10, 15), il rettangolo di destinazione è l'area contenuta da (10, 15) e (29, 34). Tuttavia, se il buffer dello schermo della console ha una larghezza di 50 caratteri e 30 caratteri di altezza, il rettangolo di destinazione viene ritagliato in (10, 15) e (29, 29). Anche le modifiche apportate al buffer dello schermo della console vengono ritagliate in base a *lpClipRectangle* , se il parametro specifica una struttura [**\_ Rect di piccole dimensioni**](small-rect-str.md) . Se il rettangolo di ritaglio viene specificato come (0, 0) e (49, 19), vengono effettuate solo le modifiche che si verificano in tale area del buffer dello schermo della console.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Questa API non è consigliata e non ha un equivalente **[terminale virtuale](console-virtual-terminal-sequences.md)** . L'utilizzo può essere approssimato ai **[margini di scorrimento](console-virtual-terminal-sequences.md#scrolling-margins)** per correggere un'area dello schermo, **[posizionare il cursore](console-virtual-terminal-sequences.md#cursor-positioning)** per impostare la posizione attiva al di fuori dell'area e le nuove righe per forzare lo spostamento del testo. Lo spazio rimanente può essere riempito spostando il cursore, **[impostando gli attributi grafici](console-virtual-terminal-sequences.md#text-formatting)** e scrivendo il testo normale.

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento del contenuto di un buffer dello schermo](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi2. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **ScrollConsoleScreenBufferW** (Unicode) e **ScrollConsoleScreenBufferA** (ANSI) |

## <a name="see-also"></a>Vedi anche

[**\_informazioni char**](char-info-str.md)

[Funzioni console](console-functions.md)

[**COORD**](coord-str.md)

[Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**\_Rect piccolo**](small-rect-str.md)
