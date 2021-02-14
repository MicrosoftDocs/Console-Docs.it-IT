---
title: GetConsoleWindow (funzione)
description: Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: ead8c4216fd0d1beb2a5fa6a6acfe3f4ce20df6f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358891"
---
# <a name="getconsolewindow-function"></a>GetConsoleWindow (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera l'handle della finestra utilizzato dalla console di associata al processo chiamante.

## <a name="syntax"></a>Sintassi

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a>Parametri

Questa funzione non ha parametri.

## <a name="return-value"></a>Valore restituito

Il valore restituito è un handle per la finestra utilizzata dalla console associata al processo chiamante oppure **null** se tale console associata non è presente.

## <a name="remarks"></a>Commenti

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

Per un'applicazione ospitata all'interno di una sessione [**pseudoconsole**](pseudoconsoles.md) , questa funzione restituisce un handle di finestra solo per la coda dei messaggi. La finestra associata non viene visualizzata localmente perché _pseudoconsole_ esegue la serializzazione di tutte le azioni in un flusso per la presentazione in un'altra finestra del terminale altrove.

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Windows 2000 Professional \[solo app desktop\] |
| Server minimo supportato | Windows 2000 Server \[solo app desktop\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

</table>

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)