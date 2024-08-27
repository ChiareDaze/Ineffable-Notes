### Cos'è e a cosa serve

Fornisce nuovi strumenti per rappresentare elementi nello spazio del problema.
Gli elementi sono chiamati **oggetti**. 

### Tutto è un oggetto

Un oggetto è un po' come un piccolo computer: ha uno **stato** e ha delle operazioni che possono essere eseguite

#### Ex. Modellare una lampadina

- Stato: accesa vs. spenta
- Operazioni: collega, scollega

Per effettuare una richiesta, si invia un messaggio a quell'oggetto.
Un oggetto è una richiesta di chiamata a una funzione (**metodo**) che appartiene a un particolare oggetto (collega(), scollega())

Ogni oggetto ha una propria memoria fatta di altri oggetti (incapsulamento e information hiding)

Un nuovo tipo di oggetto può essere creato utilizzando oggetti esistenti

Un programma può nascondere la sua complessità mediante la semplicità degli oggetti


### Metodi e classi

Ogni oggetto ha un suo **tipo** (classe).
Ogni oggetto è un istanza di una classe e la classe è identificata dai **messaggi** (metodi) che essa possiede.

Tutti gli oggetti di uno stesso tipo possono ricevere gli stessi messaggi

![[Pasted image 20240711125551.png|500]]

### Ereditarietà

Vogliamo evitare di ricreare nuove classi di oggetti quando esse hanno una funzionalità simili

![[Pasted image 20240711125920.png|500]]

### Polimorfismo

E' possibile utilizzare la classe base, senza dover conoscere necessariamente la classe specifica di un oggetto e permette di scrivere codice che non dipende dalla classe specifica.
Si possono aggiungere nuove sottoclassi anche in seguito.
