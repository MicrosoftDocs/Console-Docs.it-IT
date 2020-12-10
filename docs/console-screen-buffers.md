---
title: Buffer dello schermo della console
description: Un buffer dello schermo è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni di terminale, api della console
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.localizationpriority: high
ms.openlocfilehash: 4c5740be3b60d54f9e7b586b41e962a4102222a0
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420200"
---
# <a name="console-screen-buffers"></a>Buffer dello schermo della console

Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console. Una console può avere più buffer dello schermo. Il *buffer dello schermo attivo* è quello visualizzato sullo schermo.

Il sistema crea un buffer dello schermo ogni volta che viene creata una nuova console. Per aprire un handle per un buffer dello schermo attivo della console, specificare il valore **CONOUT$** in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858). Per creare buffer dello schermo aggiuntivi per la relativa console, un processo può usare la funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md). Un nuovo buffer dello schermo non è attivo fino a quando non viene specificato il relativo handle in una chiamata alla funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). È tuttavia possibile accedere ai buffer dello schermo per la lettura e la scrittura se sono attivi o inattivi.

Ogni buffer dello schermo presenta una matrice bidimensionale di record di informazioni sui caratteri. I dati per ogni carattere vengono archiviati in una struttura [**CHAR\_INFO**](char-info-str.md) che specifica il carattere Unicode o ANSI e i colori di primo piano e di sfondo in cui viene visualizzato tale carattere.

Per ogni buffer dello schermo, è possibile impostare una serie di proprietà associate a un buffer dello schermo in modo indipendente. Ciò significa che la modifica del buffer dello schermo attivo può avere un effetto significativo sull'aspetto della finestra della console. Le proprietà associate a un buffer dello schermo includono:

- Dimensioni del buffer dello schermo, in righe e colonne di tipo carattere.
- Attributi di testo (colori di primo piano e di sfondo per la visualizzazione di testo che deve essere scritto dalla funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md)).
- Dimensioni e posizione della finestra (area rettangolare del buffer dello schermo della console visualizzata nella finestra della console).
- Posizione, aspetto e visibilità del cursore.
- Modalità di output (**ENABLE\_PROCESSED\_OUTPUT** e **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**). Per altre informazioni sulle modalità di output della console, vedere [Modalità della console di alto livello](high-level-console-modes.md).

Quando viene creato, un buffer dello schermo contiene caratteri di spazio in ogni posizione. Il cursore è visibile e posizionato in corrispondenza dell'origine del buffer (0,0) e la finestra è posizionata con l'angolo superiore sinistro in corrispondenza dell'origine del buffer. Le dimensioni del buffer dello schermo della console, le dimensioni della finestra, gli attributi del testo e l'aspetto del cursore sono determinati dall'utente o dalle impostazioni predefinite del sistema. Per recuperare i valori correnti delle varie proprietà associate al buffer dello schermo della console, usare le funzioni [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md) e [**GetConsoleMode**](getconsolemode.md).

Le applicazioni che modificano le proprietà del buffer dello schermo della console devono creare il proprio buffer dello schermo o salvare lo stato del buffer dello schermo ereditato durante l'avvio e ripristinarlo all'uscita. Questo comportamento cooperativo è necessario per garantire che le modifiche non influiscano sulle altre applicazioni che condividono la stessa sessione della console.

> [!TIP]
> Da ora in poi, è consigliabile usare la [**modalità del buffer alternativo**](console-virtual-terminal-sequences.md#alternate-screen-buffer), se possibile, anziché creare un secondo buffer dello schermo per questo scopo. La **modalità del buffer alternativo** offre una maggiore compatibilità tra dispositivi remoti e con altre piattaforme. Per altre informazioni, vedere la discussione sul [**confronto tra le API della console classica e le sequenze di terminale virtuale**](classic-vs-vt.md).

## <a name="cursor-appearance-and-position"></a>Aspetto e posizione del cursore

Il cursore di un buffer dello schermo può essere visibile o nascosto. Quando è visibile, l'aspetto può variare, dal riempire completamente una cella di caratteri all'apparire come linea orizzontale nella parte inferiore della cella. Per recuperare informazioni sull'aspetto e sulla visibilità del cursore, usare la funzione [**GetConsoleCursorInfo**](getconsolecursorinfo.md). Questa funzione indica se il cursore è visibile e descrive l'aspetto del cursore come percentuale di una cella di caratteri riempita. Per impostare l'aspetto e la visibilità del cursore, usare la funzione [**SetConsoleCursorInfo**](setconsolecursorinfo.md).

I caratteri scritti dalle [funzioni di I/O della console di alto livello](high-level-console-i-o.md) vengono scritti nella posizione corrente del cursore, avanzando il cursore alla posizione successiva. Per determinare la posizione corrente del cursore nel sistema di coordinate di un buffer dello schermo, usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Per impostare la posizione del cursore e, di conseguenza, controllare il posizionamento del testo scritto o visualizzato dalle funzioni di I/O di alto livello, è possibile usare [**SetConsoleCursorPosition**](setconsolecursorposition.md). Se si sposta il cursore, il testo in corrispondenza della posizione del nuovo cursore verrà sovrascritto.

> [!NOTE]
> L'uso delle funzioni di basso livello per individuare la posizione del cursore è sconsigliato. È consigliabile usare [sequenze di terminale virtuale](console-virtual-terminal-sequences.md) per eseguire una query su questa posizione, se necessario, per i layout avanzati. Altre informazioni sulla preferenza delle sequenze di terminale virtuale sono disponibili nel documento di **[confronto tra le funzioni classiche e le sequenze di terminale virtuale](classic-vs-vt.md)** .

La posizione, l'aspetto e la visibilità del cursore sono impostate in modo indipendente per ogni buffer dello schermo.

## <a name="character-attributes"></a>Attributi di tipo carattere

Gli attributi di tipo carattere possono essere divisi in due classi: colore e DBCS. Gli attributi seguenti sono definiti nel file di intestazione `WinCon.h`.

| Attributo | Significato |
|-|-|
| **FOREGROUND\_BLUE** | Il colore del testo contiene il blu. |
| **FOREGROUND\_GREEN** | Il colore del testo contiene il verde. |
| **FOREGROUND\_RED** | Il colore del testo contiene il rosso. |
| **FOREGROUND\_INTENSITY** | Il colore del testo è accentuato. |
| **BACKGROUND\_BLUE** | Il colore di sfondo contiene il blu. |
| **BACKGROUND\_GREEN** | Il colore di sfondo contiene il verde. |
| **BACKGROUND\_RED** | Il colore di sfondo contiene il rosso. |
| **BACKGROUND\_INTENSITY** | Il colore di sfondo è accentuato. |
| **COMMON\_LVB\_LEADING\_BYTE** | Byte iniziale. |
| **COMMON\_LVB\_TRAILING\_BYTE** | Byte finale. |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | Orizzontale superiore. |
| **COMMON\_LVB\_GRID\_LVERTICAL** | Verticale sinistro. |
| **COMMON\_LVB\_GRID\_RVERTICAL** | Verticale destro. |
| **COMMON\_LVB\_REVERSE\_VIDEO** | Attributi di sfondo e primo piano inversi. |
| **COMMON\_LVB\_UNDERSCORE** | Sottolineatura. |

Gli attributi di primo piano specificano il colore del testo. Gli attributi di sfondo specificano il colore usato per riempire lo sfondo della cella. Gli altri attributi vengono usati con [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794) (Double Byte Character Set).

Un'applicazione può combinare le costanti di primo piano e di sfondo per ottenere colori diversi. Ad esempio, la combinazione seguente restituisce un testo in colore ciano acceso su uno sfondo blu.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Se non viene specificata alcuna costante di sfondo, quest'ultimo sarà nero e se non viene specificata alcuna costante di primo piano, il testo sarà nero. Ad esempio, la combinazione seguente restituisce un testo nero su uno sfondo bianco.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Ogni cella di caratteri del buffer dello schermo archivia gli attributi di colore per i colori usati per disegnare il primo piano (testo) e lo sfondo di tale cella. Un'applicazione può impostare singolarmente i dati relativi al colore per ogni cella di caratteri, archiviando i dati nel membro **Attributes** della struttura [**CHAR\_INFO**](char-info-str.md) per ogni cella. Gli attributi di testo correnti di ogni buffer dello schermo vengono usati per i caratteri successivamente scritti o visualizzati dalle funzioni di alto livello.

Un'applicazione può usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per determinare gli attributi di testo correnti di un buffer dello schermo e la funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) per impostare gli attributi di tipo carattere. La modifica degli attributi di un buffer dello schermo non influisce sulla visualizzazione dei caratteri scritti in precedenza. Questi attributi di testo non influiscono sui caratteri scritti dalle funzioni di I/O della console di basso livello (ad esempio la funzione [**WriteConsoleOutput**](writeconsoleoutput.md) o [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)), che specificano in modo esplicito gli attributi per ogni cella scritta o lasciano invariati gli attributi.

> [!NOTE]
> Per modificare gli attributi di testo predefiniti e specifici, è sconsigliato l'uso delle funzioni di basso livello. Per impostare gli attributi di testo, è consigliabile usare [sequenze di terminale virtuale](console-virtual-terminal-sequences.md). Altre informazioni sulla preferenza delle sequenze di terminale virtuale sono disponibili nel documento di **[confronto tra le funzioni classiche e le sequenze di terminale virtuale](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Attributi dei tipi di carattere

La funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) recupera le informazioni sul tipo di carattere della console corrente. Le informazioni archiviate nella struttura [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) includono la larghezza e l'altezza di ogni carattere nel tipo di carattere.

La funzione [**GetConsoleFontSize**](getconsolefontsize.md) recupera le dimensioni del tipo di carattere usato dal buffer dello schermo della console specificato.

> [!NOTE]
> L'uso delle funzioni per individuare e modificare le informazioni sui tipi di carattere è sconsigliato. Si consiglia di usare le applicazioni da riga di comando in modo neutro, per garantire la compatibilità multipiattaforma e la compatibilità con gli ambienti host che consentono all'utente di personalizzare il tipo di carattere. Per altre informazioni sulle preferenze utente e sugli ambienti host, inclusi i terminali, vedere la **[roadmap dell'ecosistema](ecosystem-roadmap.md)** .
