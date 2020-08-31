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
ms.openlocfilehash: 7d707423d7fca7c55d06bff11d6cbc904512e62b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059929"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole (funzione)


Crea un nuovo oggetto pseudoconsole per il processo chiamante.

<a name="syntax"></a>Sintassi
------

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

<a name="parameters"></a>Parametri
----------

*dimensioni* \[ in\]  
Dimensioni della finestra o del buffer in numero di caratteri che verranno utilizzati durante la creazione iniziale del pseudoconsole. Questa operazione può essere modificata in un secondo momento con [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[ in\]  
Handle aperto per un flusso di dati che rappresenta l'input dell'utente per il dispositivo. Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*hOutput* \[ in\]  
Handle aperto per un flusso di dati che rappresenta l'output dell'applicazione dal dispositivo. Questa operazione è attualmente limitata all'I/O [sincrono](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*dwFlags* \[ in\]  
I possibili valori sono i seguenti:
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>valore</th>
<th>Significato</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>0</strong></td>
<td><p>Eseguire una creazione pseudoconsole standard.</p></td>
</tr>
<tr class="even">
<td><span id="PSEUDOCONSOLE_INHERIT_CURSOR"></span><span id="pseudoconsole_inherit_cursor"></span>
<strong>PSEUDOCONSOLE_INHERIT_CURSOR</strong> (DWORD) 1</td>
<td><p>La sessione pseudoconsole creata tenterà di ereditare la posizione del cursore della console padre.</p></td>
</tr>
</tbody>
</table>

*phPC* \[ out\]  
Puntatore a una posizione che riceverà un handle per il nuovo dispositivo pseudoconsole.

<a name="return-value"></a>Valore restituito
------------

Tipo: **HRESULT**

Se questo metodo ha esito positivo, restituisce **S_OK**. In caso contrario, restituisce un codice di errore **HRESULT** .

<a name="remarks"></a>Osservazioni
-------

Questa funzione viene utilizzata principalmente dalle applicazioni che tentano di essere una finestra del terminale per un'applicazione con interfaccia utente della riga di comando. I chiamanti diventano responsabili della presentazione delle informazioni sul flusso di output e della raccolta dell'input utente e della relativa serializzazione nel flusso di input.

I flussi di input e di output codificati come UTF-8 contengono testo normale con sequenze di [terminali virtuali](console-virtual-terminal-sequences.md). 

Nel flusso di output, le [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) possono essere decodificate dall'applicazione chiamante per il layout e presentano il testo normale in una finestra di visualizzazione. 

Nel flusso di input, il testo normale rappresenta i tasti di scelta rapida standard di un utente. Le operazioni più complesse sono rappresentate da chiavi di controllo codificate e da movimenti del mouse come [sequenze di terminali virtuali](console-virtual-terminal-sequences.md) incorporate in questo flusso.

L'handle creato da questa funzione deve essere chiuso con [ClosePseudoConsole](closepseudoconsole.md) al termine delle operazioni.

Se `PSEUDOCONSOLE_INHERIT_CURSOR` si utilizza, l'applicazione chiamante deve essere preparata a rispondere alla richiesta per lo stato del cursore in modo asincrono in un thread in background tramite l'inoltro o l'interpretazione della richiesta di informazioni di cursore che verranno ricevute `hOutput` e in risposta `hInput` . In caso contrario, può causare il blocco dell'applicazione chiamante durante l'esecuzione di un'altra richiesta del sistema pseudoconsole.

<a name="examples"></a>Esempi
--------

Per una procedura dettagliata sull'uso di questa funzione per stabilire una sessione psuedoconsole, vedere [creazione di una sessione Pseudoconsole](creating-a-pseudoconsole-session.md).

<a name="requirements"></a>Requisiti
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Client minimo supportato</p></td>
<td><p>Windows 10 1809 [solo app desktop]</p></td>
</tr>
<tr class="even">
<td><p>Server minimo supportato</p></td>
<td><p>Windows Server 2019 [solo app desktop]</p></td>
</tr>
<tr class="odd">
<td><p>Intestazione</p></td>
<td>ConsoleApi. h (tramite wincon. h, Includi Windows. h)</td>
</tr>
<tr class="even">
<td><p>Libreria</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vedere anche


[Pseudoconsoles](pseudoconsoles.md)

[Creazione di una sessione Pseudoconsole](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
