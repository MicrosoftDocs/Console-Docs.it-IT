---
title: AddConsoleAlias (funzione)
description: Vedere le informazioni di riferimento sulla funzione AddConsoleAlias, che definisce un alias di console per il file eseguibile specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037554"
---
# <a name="addconsolealias-function"></a>AddConsoleAlias (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Definisce un alias di console per il file eseguibile specificato.

## <a name="syntax"></a>Sintassi

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a>Parametri

*Origine* \[ dati in\]  
Alias della console di cui eseguire il mapping al testo specificato dalla *destinazione* .

*Destinazione* \[ in\]  
Testo da sostituire con l' *origine* . Se questo parametro è **null** , l'alias della console verrà rimosso.

*Exename* \[ in\]  
Nome del file eseguibile per cui definire l'alias della console.

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è **true** .

Se la funzione ha esito negativo, il valore restituito è **false** . Per ottenere informazioni estese sull'errore, chiamare [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Commenti

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Esempio

Per un esempio, vedere [alias di console](console-aliases.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows 2000 Professional\] |
| Server minimo supportato | Solo app desktop di Windows 2000 Server \[\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **AddConsoleAliasW** (Unicode) e **AddConsoleAliasA** (ANSI) |

## <a name="see-also"></a>Vedi anche

[Alias di console](console-aliases.md)

[Funzioni console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
