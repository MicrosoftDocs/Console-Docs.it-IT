---
title: GetConsoleAliasesLength (funzione)
description: Recupera la dimensione richiesta per il buffer usato dalla funzione GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 78f9d718c960478e491b76a12f2a670c03529242
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357500"
---
# <a name="getconsolealiaseslength-function"></a>GetConsoleAliasesLength (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera la dimensione richiesta per il buffer usato dalla funzione [**GetConsoleAliases**](getconsolealiases.md) .

## <a name="syntax"></a>Sintassi

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a>Parametri

*lpExeName* \[ in\]  
Nome del file eseguibile di cui devono essere recuperati gli alias della console.

## <a name="return-value"></a>Valore restituito

Dimensioni del buffer necessarie per archiviare tutti gli alias di console definiti per il file eseguibile, in byte.

## <a name="remarks"></a>Commenti

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0501 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |
| Nomi Unicode e ANSI | **GetConsoleAliasesLengthW** (Unicode) e **GetConsoleAliasesLengthA** (ANSI) |

## <a name="see-also"></a>Vedi anche

[**AddConsoleAlias**](addconsolealias.md)

[Alias di console](console-aliases.md)

[Funzioni della console](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)