# Analisi del sistema

## Analisi del dominio
<!--- TODO inserire analisi del dominio, in cui si esplicitano i concetti in maniera chiara -->

Durante l'analisi del dominio, si sono dovuti esplicitare in maniera chiara alcuni concetti:
- Turno: il periodo di tempo in cui il giocatore possiede il controllo della partita.
- Rank: viene definito _rank_ ogni riga della scacchiera.
- File: viene definita _file_ ogni colonna della scacchiera.
- Mossa doppia: la mossa per cui un pedone solo dalla sua posizione iniziale effettui un movimento di 2
  caselle, invece che soltanto una, come da regola generale.

## Requisiti di sistema
Durante l'analisi del problema sono stati individuati i seguenti requisiti del sistema da realizzare.

### Business
- Creare un sistema in grado di poter effettuare una partita a scacchi,
  completa di tutte le regole di cui è provvisto il gioco originale.
- Permettere di giocare le partite in modalità interattiva tra due utenti reali,
  in modalità _hotseat_.

<!--- TODO discutere se mantenere i requisiti utente in questa maniera o comprimerli -->
### Utente
- Gli utenti dovranno interagire con il sistema tramite un'interfaccia grafica (GUI).
- Gli utenti possono visualizzare i diversi fattori che rappresentano lo stato attuale della partita:
    - la disposizione delle pedine
    - il giocatore di turno
    - la pedina selezionata
    - le mosse disponibili della pedina selezionata
    - l'ultima mossa effettuata dall'altro giocatore
    - il tempo disponibile per eseguire la propria mossa
    - lo stato finale della partita
- Gli utenti possono interagire col sistema:
    - impostare la modalità di gioco
    - impostare i vincoli temporali
    - impostare il proprio nome
    - avviare la partita
    - selezionare/deselezionare una pedina
    - eseguire una mossa per la pedina selezionata
    - selezionare il pezzo a cui promuovere il pedone
    - eseguire la resa

### Funzionali
- La partita deve essere avviata con una certa configurazione che comprende:
    - i tipi di giocatore (umano)
    - i vincoli temporali (senza limiti, con limite per mossa definito dall'utente)
    - i nominativi del giocatore bianco e del giocatore nero
- Il gioco si svolge in maniere interattiva, facendo eseguire le mosse dei giocatori una volta a testa***.
- Il campo da gioco deve essere rappresentato da una scacchiera, ossia una griglia in cui righe e colonne
  siano identificate rispettivamente da un numero da 1 a 8 e da una lettera da A a H,
  per cui le singole celle siano univoche rispetto alla combinazione dei due valori.
- A ogni giocatore devono essere assegnati i propri pezzi degli scacchi, disposti in maniera adeguata, e suddivisi
  per tipo, ossia 2 torri ("rook"), 2 alfieri("bishop"), 2 cavalli("knight"), 8 pedoni("pawn"), 1 regina("queen") e 1 
  re("king").
- Ogni tipo di pezzo deve sapere le proprie regole di movimento, al fine di poter vedere le mosse disponibili:
    - Torre: la torre può muoversi orizzontalmente o verticalmente di N posizioni.
    - Alfiere: l'alfiere può muoversi diagonalmente di N posizioni.
    - Cavallo: il cavallo può muoversi seguendo una traiettoria ad _L_.
    - Pedone: il pedone può muoversi solo in avanti di una posizione.
    - Regina: la regina può muoversi in tutte le direzioni di N posizioni.
    - Re: il re può muoversi in tutte le direzioni di una sola posizione.
- Sono presenti alcune eccezioni (di prima mossa) a tali regole di movimento:
    - il pedone che si muove di 2 all'inizio (mossa doppia)
    - l'arrocco
- Ogni pezzo che si muove in modalità rettilinea deve fermarsi prima di un altro pezzo, nei limiti della scacchiera [DA 
  RILEGGERE].
- Ogni pezzo può effettuare la cattura di un altro pezzo dell'avversario, muovendosi nella posizione di tale
  pezzo, causando la rimozione dalla scacchiera.
- Sono presenti alcune eccezioni alle regole di cattura:
    - Il pedone effettua la cattura sempre e solo, muovendosi di una posizione in avanti in diagonale.
    - Il pedone, nel caso in cui un pedone avversario effettui la _mossa doppia_ e si ritrovi affianco al
      pedone in questione, esso può catturare il pedone avversario posizionandosi nella casella dietro di lui.
      Tale mossa viene definita _presa al varco_.
- Quando un pedone avversario, effettuando la _mossa doppia_ finisce esattamente accanto, ovvero sulla stessa traversa
  e su colonna adiacente, al pedone del giocatore del turno successivo, quest'ultimo in tale turno può catturarlo come
  se il pedone avversario si fosse mosso di un passo solo. Tale mossa viene definita _en passant_.
- Il sistema deve essere in grado di riconoscere particolari stati del gioco:
    - scacco
    - scacco matto
    - stallo
    - resa

<!--- TODO da rivedere i seguenti -->
### Non funzionali
- Realizzazione di software in grado di essere facilmente ampliabile.
- Realizzazione di un'interfaccia grafica che aiuti l'utente a realizzare le mosse in maniera intuitiva e rapida.
- Realizzazione di un algoritmo di analisi delle mosse disponibili che venga effettuata in modo sufficientemente rapido.
- Sviluppo di una notazione standard per le mosse che sia interoperabile con altri sistemi.

### Di implementazione:
- Utilizzo di Scala 3.x
- Utilizzo di TuProlog
- Utilizzo di JDK + IDE + tutti i framework)

### Opzionali:
- Aggiunta di un'ulteriore modalità di gioco che consiste nella sfida contro un'intelligenza artificiale
- Aggiunta di un ulteriore vincolo temporale in cui la partita ha una durata preimpostata al termine della quale ...
- Sviluppo di una funzionalità di tracciamento dei pezzi mangiati di ciascun giocatore
- Sviluppo di un sistema di leaderboard con il numero di vittorie dei giocatori
- Sviluppo di un sistema di replay delle partite
- Impostazioni aggiuntive relative alla GUI.

[Back to index](../index.md) | 
[Previous Chapter](../2-development-process/index.md) | 
[Next Chapter](../4-architectural-design/index.md)
