# EX - Animali preferiti

## 📌 Milestone 1: Inserire un Componente React
1. Monta un componente React all’interno dell’elemento con classe .lista-animali.

2. Il componente deve includere:
 - Un elemento <details> con titolo "Animali", che contiene:
 - Una lista <ul> statica che viene creata a partire da un array di stringhe (animals) dove ciascuna stringa rappresenta il nome di un animale.

Obiettivo: Mostrare la struttura base della lista di animali con un <details> che può essere espanso o contratto.

## 📌 Milestone 2: Aggiungere Animali Casuali
1. Trasforma l’array animals usando useState (l’array è inizialmente vuoto).
2. Aggiungi un bottone "Aggiungi Animale" sopra il <details>.
3. Cliccando il bottone, un animale casuale viene aggiunto alla lista.
4. Usa un array predefinito per scegliere casualmente:

```
const animalsChoices = ["Cane", "Gatto", "Pappagallo", "Cavallo", "Panda"];
```

5. L’animale selezionato deve essere aggiunto all’interno della lista <ul> come <li>.

Obiettivo: L’utente può vedere gli animali aggiunti dinamicamente nella lista.


## 📌 Milestone 3: Usare una Modale per Aggiungere Animali

Partendo da questo componente Modal:

```
function Modal({
      title, 
      content, 
      show = false, 
      onClose = () => {}
  }){
      return show && ReactDOM.createPortal(
          <div className="modal-container">
              <div className="modal">
                  <h2>{title}</h2>
                  <p>{content}</p>
                  <button onClick={onClose}>Annulla</button>
              </div>
          </div>,
          document.body
      )
  }
```

```
.modal-container{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal{
    background-color: white;
    padding: 20px;
    border-radius: 5px;
}
```

Espandilo affinché:

- La vecchia prop content può essere usata per passare un componente qualsiasi.
- Un nuovo div in fondo alla modale contiene il bottone Annulla e un nuovo bottone Conferma.
- Una nuova prop onConfirm si aspetta una funzione per gestire l’azione di conferma.
- Sostituisci l’aggiunta casuale dell’animale con una modale interattiva:
  - Cliccando il bottone "Aggiungi Animale," si apre una modale.
  - La modale include un input di testo (passato al prop content) per inserire il nome di un animale.
  - Conferma: Aggiunge l’animale alla lista e chiude la modale.
  - Annulla: Chiude la modale senza modificare la lista.

Obiettivo: L’utente può aggiungere animali specifici utilizzando la modale.


## 🎯 Bonus: Utilizzare l'API per Creare Card

```
Nota: a differenza di quanto visto finora negli esempi, per accedere all'API utilizzare l'url base:
http://localhost:3333
al posto di:
https://freetestapi.com/api/v1
Ad esempio:
http://localhost:3333/users
per chiamare l'endpoint /users
```

Utilizza l'API:
/animals?search=[animalName]
per effettuare una ricerca dell'animale basata sul contenuto dell'input: 
- Sostituisci [animalName] con il valore inserito dall'utente.
- Assicurati di gestire lo stato di caricamento mentre l'API è in fase di risposta (mostra un messaggio come "Caricamento...").
1. Dal primo risultato restituito dall'array (se presente), crea un oggetto che abbia queste proprietà:
  - name: Il nome dell'animale.
  - description: La descrizione dell'animale (o un messaggio predefinito come "Descrizione non disponibile" se manca).
  - image: L'immagine dell'animale (usa un'immagine di default se non è disponibile).
2. Aggiungi l'oggetto alla lista degli animali e visualizzalo come una card, con:
  - Titolo: Il nome dell'animale.
  - Immagine (se presente).
  - Descrizione.
3. Gestione degli errori:
  - Se la ricerca non restituisce risultati, informa l'utente con un messaggio di errore. (es.: "Nessun animale trovato")
  - Mostra un messaggio in caso di problemi di rete o altri errori. (es.: "Errore durante la ricerca dell'animale")

Obiettivo: Permetti agli utenti di aggiungere animali specifici utilizzando l'API per ottenere informazioni, mostrando eventuali errori in modo chiaro.