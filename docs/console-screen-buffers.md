---
title: Buffer dello schermo della console
description: Un buffer dello schermo è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Console, applicazioni in modalità carattere, applicazioni da riga di comando, applicazioni Terminal, API console
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.openlocfilehash: 24998a88e19eb05c66dce5d54bed28e777d0d058
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060044"
---
# <a name="console-screen-buffers"></a>Buffer dello schermo della console


Un *buffer dello schermo* è una matrice bidimensionale di dati di tipo carattere e colore per l'output in una finestra della console. Una console può avere più buffer dello schermo. Il *buffer dello schermo attivo* corrisponde a quello visualizzato sullo schermo.

Il sistema crea un buffer dello schermo ogni volta che viene creata una nuova console. Per aprire un handle per il buffer dello schermo attivo di una console, specificare il valore **CONOUT $** in una chiamata alla funzione [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) . Un processo può utilizzare la funzione [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) per creare buffer dello schermo aggiuntivi per la relativa console. Un nuovo buffer dello schermo non è attivo fino a quando non viene specificato il relativo handle in una chiamata alla funzione [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . È tuttavia possibile accedere ai buffer dello schermo per la lettura e la scrittura se sono attivi o inattivi.

Ogni buffer dello schermo presenta una matrice bidimensionale di record di informazioni sui caratteri. I dati per ogni carattere vengono archiviati in una struttura di [** \_ informazioni char**](char-info-str.md) che specifica il carattere Unicode o ANSI e i colori di primo piano e di sfondo in cui viene visualizzato tale carattere.

Una serie di proprietà associate a un buffer dello schermo può essere impostata in modo indipendente per ogni buffer dello schermo. Ciò significa che la modifica del buffer dello schermo attivo può avere un effetto significativo sull'aspetto della finestra della console. Le proprietà associate a un buffer dello schermo includono:

- Dimensioni del buffer dello schermo, in righe e colonne di tipo carattere.
- Attributi di testo (colori di primo piano e di sfondo per la visualizzazione di testo da scrivere tramite la funzione [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) ).
- Dimensioni e posizione della finestra (area rettangolare del buffer dello schermo della console visualizzato nella finestra della console).
- Posizione, aspetto e visibilità del cursore.
- Modalità di output **( \_ Abilita \_ output elaborato** e **Abilita \_ wrapping \_ all' \_ \_ output EOL**). Per altre informazioni sulle modalità di output della console, vedere [modalità console di alto livello](high-level-console-modes.md).

Quando viene creato, un buffer dello schermo contiene spazi vuoti. Il cursore è visibile e posizionato in corrispondenza dell'origine del buffer (0, 0) e la finestra viene posizionata con l'angolo superiore sinistro dell'origine del buffer. La dimensione del buffer dello schermo della console, le dimensioni della finestra, gli attributi di testo e l'aspetto del cursore sono determinati dall'utente o dalle impostazioni predefinite del sistema. Per recuperare i valori correnti delle varie proprietà associate al buffer dello schermo della console, usare le funzioni [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md)e [**GetConsoleMode**](getconsolemode.md) .

Le applicazioni che modificano le proprietà del buffer dello schermo della console devono creare il proprio buffer dello schermo o salvare lo stato del buffer dello schermo ereditato durante l'avvio e ripristinarlo all'uscita.

## <a name="span-id_win32_cursor_appearance_and_positionspanspan-id_win32_cursor_appearance_and_positionspancursor-appearance-and-position"></a><span id="_win32_cursor_appearance_and_position"></span><span id="_WIN32_CURSOR_APPEARANCE_AND_POSITION"></span>Aspetto e posizione del cursore


Il cursore di un buffer dello schermo può essere visibile o nascosto. Quando è visibile, l'aspetto può variare, da riempire completamente una cella di caratteri per apparire come linea orizzontale nella parte inferiore della cella. Per recuperare informazioni sull'aspetto e la visibilità del cursore, utilizzare la funzione [**GetConsoleCursorInfo**](getconsolecursorinfo.md) . Questa funzione indica se il cursore è visibile e descrive l'aspetto del cursore come percentuale di una cella di caratteri riempita. Per impostare l'aspetto e la visibilità del cursore, utilizzare la funzione [**SetConsoleCursorInfo**](setconsolecursorinfo.md) .

I caratteri scritti dalle funzioni di I/O della console di alto livello vengono scritti nella posizione corrente del cursore, avanzando il cursore alla posizione successiva. Per determinare la posizione corrente del cursore nel sistema di coordinate di un buffer dello schermo, utilizzare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). È possibile utilizzare [**SetConsoleCursorPosition**](setconsolecursorposition.md) per impostare la posizione del cursore e, di conseguenza, controllare il posizionamento del testo scritto o ripreso dalle funzioni di i/O di alto livello. Se si sposta il cursore, il testo in corrispondenza della posizione del nuovo cursore verrà sovrascritto.

La posizione, l'aspetto e la visibilità del cursore sono impostate in modo indipendente per ogni buffer dello schermo.

## <a name="span-id_win32_character_attributesspanspan-id_win32_character_attributesspancharacter-attributes"></a><span id="_win32_character_attributes"></span><span id="_WIN32_CHARACTER_ATTRIBUTES"></span>Attributi carattere


Gli attributi di tipo carattere possono essere divisi in due classi: color e DBCS. Gli attributi seguenti vengono definiti nel file di intestazione wincon. h.


| Attributo                         | Significato                                       |
|-----------------------------------|-----------------------------------------------|
| **blu in primo piano \_**              | Il colore del testo contiene il blu.                     |
| **verde primo piano \_**             | Il colore del testo contiene verde.                    |
| **rosso in primo piano \_**               | Il colore del testo contiene rosso.                      |
| **intensità in primo piano \_**         | Il colore del testo viene intensificato.                    |
| **\_blu sfondo**              | Il colore di sfondo contiene blu.               |
| **\_verde sfondo**             | Il colore di sfondo contiene verde.              |
| **\_rosso sfondo**               | Il colore di sfondo contiene rosso.                |
| **intensità di sfondo \_**         | Il colore di sfondo viene intensificato.              |
| **\_ \_ byte principale LVB \_ comune**    | Byte iniziali.                                 |
| **\_ \_ byte finale LVB comune \_**   | Byte finale.                                |
| **\_griglia LVB \_ comune \_ orizzontale** | Orizzontale superiore.                               |
| **COMMON \_ LVB \_ Grid \_ LVERTICAL**  | Sinistra verticale.                                |
| **COMMON \_ LVB \_ Grid \_ RVERTICAL**  | Diritto verticale.                               |
| **\_video comune LVB \_ inverso \_**   | Attributi in primo piano e in background. |
| **carattere \_ di \_ sottolineatura LVB comune**       | Sottolineatura.                                   |


Gli attributi di primo piano specificano il colore del testo. Gli attributi di sfondo specificano il colore utilizzato per riempire lo sfondo della cella. Gli altri attributi vengono utilizzati con [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794).

Un'applicazione può combinare le costanti in primo piano e in background per ottenere colori diversi. Ad esempio, la combinazione seguente restituisce un testo cyan luminoso su uno sfondo blu.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Se non viene specificata alcuna costante in background, lo sfondo è nero e se non viene specificata alcuna costante di primo piano, il testo è nero. Ad esempio, la combinazione seguente produce testo nero su uno sfondo bianco.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Ogni cella di caratteri del buffer dello schermo archivia gli attributi di colore per i colori utilizzati per disegnare il primo piano (testo) e lo sfondo di tale cella. Un'applicazione può impostare singolarmente i dati relativi al colore per ogni cella di caratteri, archiviando i dati nel membro **Attributes** della struttura di [** \_ informazioni char**](char-info-str.md) per ogni cella. Gli attributi di testo correnti di ogni buffer dello schermo vengono utilizzati per i caratteri successivamente scritti o restituiti dalle funzioni di alto livello.

Un'applicazione può usare [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) per determinare gli attributi di testo correnti di un buffer dello schermo e la funzione [**SetConsoleTextAttribute**](setconsoletextattribute.md) per impostare gli attributi dei caratteri. La modifica degli attributi di un buffer dello schermo non influisce sulla visualizzazione dei caratteri precedentemente scritti. Questi attributi di testo non influiscono sui caratteri scritti dalle funzioni di I/O della console di basso livello, ad esempio la funzione [**WriteConsoleOutput**](writeconsoleoutput.md) o [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) , che specificano in modo esplicito gli attributi per ogni cella scritta o lasciano invariati gli attributi.

## <a name="span-id_win32_font_attributesspanspan-id_win32_font_attributesspanfont-attributes"></a><span id="_win32_font_attributes"></span><span id="_WIN32_FONT_ATTRIBUTES"></span>Attributi del tipo di carattere


La funzione [**GetCurrentConsoleFont**](getcurrentconsolefont.md) recupera le informazioni sul tipo di carattere della console corrente. Le informazioni archiviate nella struttura delle [** \_ \_ informazioni sul tipo di carattere della console**](console-font-info-str.md) includono la larghezza e l'altezza di ogni carattere del tipo di carattere.

La funzione [**GetConsoleFontSize**](getconsolefontsize.md) recupera la dimensione del tipo di carattere utilizzato dal buffer dello schermo della console specificato.








