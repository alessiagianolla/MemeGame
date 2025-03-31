### Progettazione del Gioco "Meme Game"

Progetta e implementa un'applicazione web per giocare a una versione single-player del gioco da tavolo "What Do You Meme?".

Nel gioco, il giocatore riceve un'immagine meme casuale e sette possibili didascalie per quel meme: il giocatore deve indovinare la didascalia "giusta" per il meme.

Il gioco si basa su un archivio di diverse immagini meme. Ogni immagine meme è associata esattamente a 3 didascalie "giuste" che si abbinano meglio all'immagine, e ognuna di esse è associata a un punteggio che il giocatore guadagnerà. In particolare, una didascalia vale 1 punto, un'altra 2 punti e un'altra ancora 3 punti. È possibile che una didascalia sia associata a più immagini.

---

### Modalità di gioco

Il gioco si svolge in più round. Ogni round propone un meme, nel seguente modo:

1. Il **giocatore** riceve un'**immagine meme** casuale e sette possibili **didascalie** per quel meme in ordine casuale. Sia l'immagine che le didascalie devono essere generate dal server. Tra le sette didascalie, devono essere presenti le tre "giuste".
    
2. Il giocatore deve selezionare la didascalia che meglio si abbina al meme.
    
3. Se il giocatore seleziona una delle didascalie più appropriate, guadagna i punti associati e un messaggio mostra la fine del **round** e i punti ottenuti.
    
4. Se il giocatore sceglie una delle altre didascalie, ottiene 0 punti. In questo caso, l'applicazione mostra un messaggio adeguato insieme alle due didascalie che erano le più adatte per quel meme.

---

### Modalità per utenti registrati

Gli utenti registrati giocano una **partita** composta da **3 round**. Inoltre, tutti i loro giochi e round vengono registrati e, alla fine della partita, la cronologia dei punteggi è visibile nella pagina del profilo utente. La cronologia deve mostrare tutte le immagini meme giocate, con il punteggio ottenuto per ciascuna, il punteggio della partita e il punteggio totale di tutti i giochi effettuati.

- **Uno stesso meme non può ripetersi in round diversi della stessa partita**, ma potrebbe riapparire in partite diverse.
    
- Dopo 3 round, il gioco termina e viene visualizzato il punteggio totale della partita, insieme a un riepilogo dei meme correttamente associati e delle didascalie selezionate.
    
- **Se il giocatore non completa la partita, essa non viene registrata e nessun punto viene assegnato.**
    
- Dopo la fine della partita, il giocatore può iniziare una nuova partita.

---

### Modalità per utenti anonimi

Gli utenti anonimi possono giocare solo **partite di un singolo round**. Non avranno accesso a nessuna delle funzionalità riservate agli utenti registrati.

---

### Creazione di nuove associazioni

Gli utenti registrati possono **creare nuove associazioni** tra immagini meme (già presenti nel database) e didascalie (nuove o esistenti), assegnando loro i punti relativi.

L'organizzazione di queste specifiche in diverse schermate (e possibilmente in percorsi differenti) è lasciata allo sviluppatore.

---

### Struttura dei dati

#### Giocatore
```json
{
  "id": "string",
  "nome": "string",
  "username": "string",
  "email": "string",
  "password": "string",
  "punteggio": "number",
  "meme": "array"
}
```

#### Meme
```json
{
  "id": "string",
  "url": "string",
  "didascalia1id": "array",
  "didascalia2id": "array",
  "didascalia3id": "array"
}
```

#### Didascalia
```json
{
  "id": "string",
  "testo": "string",
  "punteggio": "number"
}
```

#### Round
```json
{
  "partitaid": "string",
  "meme": "string",
  "didascalia": ["array"],
  "score": "number",
  "giocatoreid": "string"
}
```

#### Partita
```json
{
  "id": "string",
  "giocatoreid": "string",
  "data": "string",
  "numero_di_round": "number",
  "round": ["array"],
  "score_totale": "number"
}
```