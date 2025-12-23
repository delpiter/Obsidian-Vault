>[!definizione]
>Un'***interfaccia*** è un oggetto che permette il dialogo tra due entità.
>Nel gergo elettronico permette il *transito di informazioni* tra due dispositivi o sistemi.

>[!example] Paradigmi di Interazione

> ***Terminale Scrivente***
- Scrivi e leggi.

> ***Terminale Video***
- Scegli e riempi.

> ***Personal Computer***
- "*What If*".
- Paradigma dovuto alla possibilità di *undo* e *redo*, è uno stimolo alla sperimentazione.

> ***Sistemi Multimediali***
- Parla ed Ascolta.

> ***Realtà Virtuale***
- Entra ed Agisci.

## Graphical User Interface
---
>[!info]
>Le `GUI` sono state sviluppate per ***esaltare le potenzialità del cervello umano***:
>- Riconoscere e associare.
>- Generalizzare e dedurre.

Questo viene fatto attraverso la visualizzazione di *molte informazioni contemporaneamente* con metafore e colori.

### Fattori Chiave nella Progettazione
> Nella progettazione dell'interfaccia ci sono 3 aspetti fondamentali.

>[!question] Chi utilizza l'interfaccia?
- Un professionista, un utente qualunque, etc...

>[!hint] Per cosa viene usata?
- Quali sono gli obbiettivi?

>[!caution] Che tecnologia viene usata?

#### Scelta della Tecnologia per l'Interfaccia
>[!todo] In Funzione degli Obbiettivi
- Rapidità o Efficacia.
- Che cosa è la qualità.
- Utilizzo di Strategie a lungo o breve termine.

>[!abstract] In Funzione degli Utenti
- Numero di Utenti.
- Esperienza nell'utilizzo della tecnologia.
- Età media.
- Resistenza al cambiamento (*scetticismo* o *motivazione*).
- Eterogeneità dei gruppi d'appartenenza.
- Utilizzatori ***assidui o saltuari***.

### Tipologie di Interfacce
#### Interfacce Code-Based
>[!info]
>L'interazione avviene attraverso comandi (*codici*)

> *Ottimale per*:
- Moli di lavoro elevate che richiedono attenzione in punti lontani dal video.

>[!fail] Problemi
> Occorre mantenere basso il **numero di codici usabili**.
> **Nessuna riusabilità** delle conoscenze acquisite.


| Mole di Lavoro da Svolgere | Qualità | Facilità di Apprendimento | Riutilizzo Conoscenza | Soddisfazione |
|:--------------------------:|:-------:|:-------------------------:|:---------------------:|:-------------:|
|             🙂             |   😐    |            ☹️             |          ☹️           |      ☹️       |

#### Interfacce 3270
>[!info]
>Interfaccia a caratteri ***ottimale per data-entry*** e editing di dati altamente strutturati.

Workflow fortemente predefinito (basa flessibilità).
- La navigazione e tasti funzionali complicano l'*apprendimento e riusabilità delle conoscenze*.

| Mole di Lavoro da Svolgere | Qualità | Facilità di Apprendimento | Riutilizzo Conoscenza | Soddisfazione |
|:--------------------------:|:-------:|:-------------------------:|:---------------------:|:-------------:|
|             🙂             |   🙂    |            😐             |          ☹️           |      ☹️       |

#### Pseudo-GUI
>[!info]
>Interfaccia grafica che ***richiama la strutturazione di un'interfaccia a caratteri***.

Ottimale per applicazioni che devono gestire dati fortemente strutturati *garantendo una buona flessibilità*.
- **Se** standard consente riusabilità delle conoscenze acquisite

| Mole di Lavoro da Svolgere | Qualità | Facilità di Apprendimento | Riutilizzo Conoscenza | Soddisfazione |
|:--------------------------:|:-------:|:-------------------------:|:---------------------:|:-------------:|
|             🙂             |   🙂    |            😐             |          🙂           |      😐       |

#### Standard GUI
>[!info]
>Interfaccia progettata e sviluppata per un ***ambiente grafico***.

Esaltate le potenzialità di manipolazione diretta (**cut & paste**, **drag & drop**, etc...).
- Ottimale per user-driven application (alta flessibilità).

| Mole di Lavoro da Svolgere | Qualità | Facilità di Apprendimento | Riutilizzo Conoscenza | Soddisfazione |
|:--------------------------:|:-------:|:-------------------------:|:---------------------:|:-------------:|
|             🙂             |   🙂    |            😐             |          🙂           |      🙂       |

#### Special GUI
>[!info]
>Enfasi massima alla ***presentazione grafica***.

L'obbiettivo prioritario è l'***autoesplicazione***.
- Il cliente "si serve" da solo.
- L'utente target potrebbe non avere esperienza sull'utilizzo del computer.

| Mole di Lavoro da Svolgere | Qualità | Facilità di Apprendimento | Riutilizzo Conoscenza | Soddisfazione |
|:--------------------------:|:-------:|:-------------------------:|:---------------------:|:-------------:|
|             😐             |   🙂    |            🙂             |          ☹️           |      🙂       |

### Strutturazione
> Una `GUI` viene strutturata in base alle **possibilità offerte**.

>[!abstract] Bassa e Larga

- Fornisce all'utente una visione migliore delle possibilità offerte e **facilita la navigazione**.

![[GUIStructure.png]]

### Strutture di Riferimento
#### Multi-Window
>[!summary] Info
> Il ***Modello Multi Window*** consiste in molte *main window* ciascuna con un menu.

C'è un rapporto $1:1$ tra *main window* e *business object*.
- Ogni *main window* può avere più **child window**.

>[!danger] Problema
>Più main window navigabili contemporaneamente comportano una *navigazione complessa* con ***alto rischio di smarrimento***.

#### Multi-Document
>[!todo] Info
>Nel ***Modello Multi Document*** è presente una sola *top window* con menu.
>La top window guida una **serie di document window**.
>>[!warning] La top window deve rimanere sempre aperta

Il modello multi document ha una flessibilità **minore** rispetto a quella *multi window*.
- È ottimale per utenti inesperti

#### Multi Paned
>[!tl;dr] Info
>Nel ***Modello Multi Paned*** una window viene divisa in aree (*pane*) **monofunzionali** e **monoposizionali**.

Modello adatto per `GUI` speciali in applicazioni self service.

>[!danger] Assenza di Flessibilità

### Project Standard
> Vengono definiti degli **standard** per la terminologia, le metafore, le icone e le caratteristiche delle finestre.

>[!hint] Obbiettivo
>L'obbiettivo è quello di ***agevolare l'utilizzo*** da parte dell'utente.

>[!example] Esempio: Bottone con testo troppo lungo

![[ProjectStandardExample.png]]

> Soluzioni possibili (in ordine di priorità consigliata):
1. Testo più corto compreso e approvato dall'utente (`Stampa Bolla`).
2. Abbreviazione compresa e approvata dall'utente (`Stampa B.A.M.`).
3. Allargare tutti i bottoni del *gruppo*.
4. Allargare solo il "bottone incriminato".
5. Inserire un simbolo al posto del testo.
6. Ridisegnare la window e inserire una scelta nel menù (Sconsigliato).

### Comunicazione Visiva
>[!done] Affordance
>Enfatizza gli aspetti di un oggetto che invitano a ***manipolarlo in un certo modo***.

> Esempio
- Tridimensionalità, ombreggiature e puntamento.

>[!caution] Metafora
>Una **parola**, **frase** o **figura** che dipinge un oggetto o un concetto ***attraverso una somiglianza*** o un'analogia con un altro oggetto o concetto del *mondo reale*.

> Metafore comuni:
- Documento -> File.
- Cartella -> Directory.
- Lettera -> E-mail.
- Cestino -> Cancella.
- Gomma -> Undo.

>[!summary] Layout
>Il ***layout*** è determinato dalla **posizione** del testo, dei disegni e dei controlli all'*interno di un'area considerata*.

La posizione degli elementi è un'***importante strumento di comunicazione***.
- Le distanze devono essere scelte in relazione al **grado di associazione tra gli elementi**.
> Fra gli standard di progetto c'è:
- Distanza tra i *campi correlati*.
- Distanza tra i *gruppi*.
- Distanza tra *riquadro ed elementi contenuti*.
- Distanza tra *margine dell'area principale ed elementi contenuti*.

>[!hint] Colori
>I ***colori*** sono utili per focalizzare l'attenzione o per **creare associazioni**.

> Consigli per l'utilizzo
- ***Non abusare*** dei colori in un ambiente monocromatico.
- Se il colore è usato come codice: usare $3-5$ colori, ricordarsi la semantica.
- Colori **vivaci** per *aree piccole* e **neutri** per *aree grandi*.
- Ricercare un **contrasto** efficace tra testo e sfondo.
- Colori troppo brillanti causano alterazione visiva sui tempi lunghi.
	- **Sconsigliati** nelle *applicazioni gestionali*, **ottimali** per applicazioni *self-service*.

>[!bug] Icone
>Le ***icone*** sono piccoli disegni semplici e metaforici.

> Una icona è strutturata in:
- Una **immagine**.
- Uno **sfondo**.
- Un *testo facoltativo*.

> Una icona deve essere:
- Facilmente distinguibile e con alto valore informativo.
- Deve presentare esplicitamente la metafora.
- Deve essere auto esplicativo anche se prive di testo.

> Linee Guida per l'utilizzo
- Disegni ***semplici e schematici***.
- ***Colori differenti*** in icone differenti.
- Il testo è il titolo della finestra collegata.
- Bisogna cercare di usare uno ***stile coerente*** in tutta l'applicazione.

> Tipologie
- *Desktop Icon*: Obbiettivo di partenza e riapertura.
	- Per applicazioni collegate andrebbero usate *icone simili graficamente*.
- *Menu Icon* (*Palette icon*):
	- Sono sempre visibili e accanto ai **menu**.
	- È un overview delle funzioni **sempre attivabili** (modo veloce di selezione).
	- Per comandi esprimibili più facilmente attraverso disegni.
- *Button Icon*:
	- In aggiunta al testo di un bottone **rafforza graficamente la funzione del bottone**.

>[!check] Font
>Rappresenta la ***leggibilità*** in relazione al tipo di caratteristiche del carattere.

> Linee Guida
- ***Sans Serif*** per singole righe
- <span style="font-family: 'Times New Roman'; font-weight: bold;">Serif</span> per testi articolati su molte righe (aiuta a creare un "binario" per gli occhi).
- Attenzione all'utilizzo del **maiuscolo**.

### Usabilità
> Definizioni Importanti

>[!done] Efficacia
>In che misura i compiti previsti dal funzionamento vengono eseguiti.

>[!caution] Efficienza
>Risorse da impegnare per *eseguire i compiti previsti*.

>[!tldr] Soddisfazione
>Misura l'accettabilità del funzionamento da parte dell'utente.

#### Criteri di Usabilità
>[!hint] Apprendibilità
- L'$80\%$ dei nuovi utenti deve essere in grado di svolgere compiutamente una singola attività dell'applicazione in $30$ **minuti**.

>[!abstract] Velocità

>[!done] Soddisfazione
- $9$ utenti su $10$ dichiarano che è "***bello da usare***".

>[!caution] Facilità di Navigazione
- Possibilità di innescare $6$ diverse attività su un singolo oggetto senza ritornare al menu principale.

>[!tldr] Memorabilità
- Riutilizzo, senza ulteriore training, di una applicazione inattiva da $12$ mesi.