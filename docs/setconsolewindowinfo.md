---
title: SetConsoleWindowInfo (funzione)
description: Imposta la dimensione e la posizione correnti della finestra di un buffer dello schermo della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc1190aee7cb1a29c60579f5e00daf1f7280d292
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039309"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Imposta la dimensione e la posizione correnti della finestra di un buffer dello schermo della console.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[ in\]  
Handle per il buffer dello schermo della console. L'handle deve avere il diritto di accesso in **\_ lettura generico** . Per altre informazioni, vedere [sicurezza e diritti di accesso del buffer della console](console-buffer-security-and-access-rights.md).

*bAbsolute* \[ in\]  
Se questo parametro è **true** , le coordinate specificano i nuovi angoli superiore sinistro e inferiore destro della finestra. Se è **false** , le coordinate sono relative alle coordinate dell'angolo finestra correnti.

*lpConsoleWindow* \[ in\]  
Puntatore a una struttura [**small \_ Rect**](small-rect-str.md) che specifica i nuovi angoli superiore sinistro e inferiore destro della finestra.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è diverso da zero.

Se la funzione ha esito negativo, il valore restituito è zero. Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

La funzione ha esito negativo se il rettangolo della finestra specificato si estende oltre i limiti del buffer dello schermo della console. Ciò significa che i membri **Top** e **Left** del rettangolo *lpConsoleWindow* (o le coordinate Top e Left calcolate, se *bAbsolute* è false) non possono essere minori di zero. Analogamente, i membri **inferiore** e **destro** (oppure le coordinate in basso e a destra calcolata) non possono essere maggiori di (altezza del buffer dello schermo – 1) e (larghezza del buffer dello schermo – 1), rispettivamente. La funzione ha esito negativo anche se il membro **destro** (o la coordinata destra calcolata) è minore o uguale al membro a **sinistra** (o a una coordinata sinistra calcolata) o se il membro **inferiore** (o la coordinata inferiore calcolata) è minore o uguale al membro **superiore** (o coordinata superiore calcolata).

Per le console con più di un buffer dello schermo, la modifica della posizione della finestra per un buffer dello schermo non influisce sulle posizioni della finestra degli altri buffer dello schermo.

Per determinare le dimensioni e la posizione correnti della finestra di un buffer dello schermo, utilizzare la funzione [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) . Questa funzione restituisce anche le dimensioni massime della finestra, date le dimensioni correnti del buffer dello schermo, le dimensioni correnti del carattere e le dimensioni dello schermo. La funzione [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) restituisce le dimensioni massime della finestra in base al tipo di carattere e alle dimensioni dello schermo correnti, ma non considera le dimensioni del buffer dello schermo della console.

**SetConsoleWindowInfo** può essere usato per scorrere il contenuto del buffer dello schermo della console spostando la posizione del rettangolo della finestra senza modificarne le dimensioni.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a>Esempio

Per un esempio, vedere [scorrimento della finestra di un buffer dello schermo](scrolling-a-screen-buffer-s-window.md).

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Scorrimento del buffer dello schermo](scrolling-the-screen-buffer.md)

[**\_Rect piccolo**](small-rect-str.md)
