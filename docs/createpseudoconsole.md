---
title: CreatePseudoConsole (funzione)
description: Vedere le informazioni di riferimento sulla funzione CreatePseudoConsole, che alloca un nuovo pseudoconsole per il processo chiamante.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: f10a77781d555a76fdfcea8c8f10ae6bc1f72047
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038299"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole (funzione)

Crea un nuovo oggetto pseudoconsole per il processo chiamante.

## <a name="syntax"></a>Sintassi

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a>Parametri

*dimensioni* \[ in\]  
Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati durante la creazione iniziale del pseudoconsole. Questa operazione può essere modificata in un secondo momento con [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[ in\]  
Handle aperto per un flusso di dati che rappresenta l'input dell'utente per il dispositivo. Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*hOutput* \[ in\]  
Handle aperto per un flusso di dati che rappresenta l'output dell'applicazione dal dispositivo. Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*dwFlags* \[ in\]  
I possibili valori sono i seguenti:

| Valore | Significato |
|-|-|
| **0** | Eseguire una creazione pseudoconsole standard. |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1 | La sessione pseudoconsole creata tenterà di ereditare la posizione del cursore della console di paernt. |

*phPC* \[ out\]  
Puntatore a una posizione che riceverà un handle per il nuovo dispositivo pseudoconsole.

## <a name="return-value"></a>Valore restituito

Tipo: **HRESULT**

Se questo metodo ha esito positivo, restituisce **S_OK** . In caso contrario, restituisce un codice di errore **HRESULT** .

## <a name="remarks"></a>Commenti

Questa funzione viene utilizzata principalmente dalle applicazioni che tentano di essere una finestra del terminale per un'applicazione con interfaccia utente della riga di comando. I chiamanti diventano responsabili della presentazione delle informazioni sul flusso di output e della raccolta dell'input utente e della relativa serializzazione nel flusso di input.

I flussi di input e di output codificati come UTF-8 contengono testo normale con sequenze di [terminali virtuali](console-virtual-terminal-sequences.md).

Nel flusso di output, le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) possono essere decodificate dall'applicazione chiamante per il layout e presentano il testo normale in una finestra di visualizzazione.

Nel flusso di input, il testo normale rappresenta i tasti di scelta rapida standard di un utente. Le operazioni più complesse sono rappresentate da chiavi di controllo codificate e da movimenti del mouse come [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) incorporate in questo flusso.

L'handle creato da questa funzione deve essere chiuso con [ClosePseudoConsole](closepseudoconsole.md) al termine delle operazioni.

Se `PSEUDOCONSOLE_INHERIT_CURSOR` si utilizza, l'applicazione chiamante deve essere preparata a rispondere alla richiesta per lo stato del cursore in modo asincrono in un thread in background tramite l'inoltro o l'interpretazione della richiesta di informazioni di cursore che verranno ricevute `hOutput` e in risposta `hInput` . In caso contrario, può causare il blocco dell'applicazione chiamante durante l'esecuzione di un'altra richiesta del sistema pseudoconsole.

## <a name="examples"></a>Esempio

Per una procedura dettagliata sull'uso di questa funzione per stabilire una sessione pseudoconsole, vedere [creazione di una sessione pseudoconsole](creating-a-pseudoconsole-session.md).

## <a name="requirements"></a>Requisiti

| &nbsp; | &nbsp; |
|-|-|
| Client minimo supportato | Aggiornamento di Windows 10 ottobre 2018 (versione 1809) \[ solo app desktop\] |
| Server minimo supportato | \[Solo app desktop Windows Server 2019\] |
| Intestazione | ConsoleApi. h (tramite WinCon. h, Includi Windows. h) |
| Libreria | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Vedi anche

[Pseudoconsoles](pseudoconsoles.md)

[Creazione di una sessione di pseudoconsole](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
