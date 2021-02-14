---
title: GetConsoleFontSize (funzione)
description: Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96086720ee2c4ae787d2b52eee5439d54f081b8e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358341"
---
# <a name="getconsolefontsize-function"></a>GetConsoleFontSize (funzione)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.

## <a name="syntax"></a>Sintassi

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a>Parametri

*hConsoleOutput* \[in\]  
Handle per il buffer dello schermo della console. L'handle deve disporre del diritto di accesso **GENERIC\_READ**. Per altre informazioni, vedere [Sicurezza dei buffer della console e diritti di accesso](console-buffer-security-and-access-rights.md).

*nFont* \[ in\]  
Indice del tipo di carattere di cui è necessario recuperare le dimensioni. Questo indice viene ottenuto chiamando la funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .

## <a name="return-value"></a>Valore restituito

Se la funzione ha esito positivo, il valore restituito è una struttura [**Coord**](coord-str.md) che contiene la larghezza e l'altezza di ogni carattere del tipo di carattere, in unità logiche. Il membro **X** contiene la larghezza, mentre il membro **Y** contiene l'altezza.

Se la funzione ha esito negativo, la larghezza e l'altezza sono pari a zero. Per informazioni dettagliate sull'errore, chiamare [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Osservazioni

Per compilare un'applicazione che usa questa funzione, definire **\_ Win32 \_ WinNT** come 0x0500 o versione successiva. Per ulteriori informazioni, vedere [utilizzo delle intestazioni di Windows](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | \[Solo app desktop Windows XP\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2003\] |
| Intestazione | ConsoleApi3. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedere anche

[Funzioni della console](console-functions.md)

[Buffer dello schermo della console](console-screen-buffers.md)

[**COORD**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)