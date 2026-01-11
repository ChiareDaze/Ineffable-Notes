## Web Application

Il codice di un'applicazione web viene eseguito in diversi "posti":
- Il codice della logica locale, come ad esempio la validazione di alcuni dati o in generale piccole elaborazioni e quello dell'interfaccia grafica vengono eseguiti nel browser web
- La logica dell'applicazione quindi elaborazioni più pesanti e anche il DBMS vengono eseguiti su un server

Possiamo dividere un web app in due parti:
- **Front-end**: comprende la UI e in generale quello che riguarda i client. Si utilizzano principalmente linguaggi come HTML CSS, JavaScript e Asynchronous request (AJAX).
- **Back-end**: Comprende quindi delle API, uno storage e un DBMS. Principalmente vengono usati linguaggi come PHP, Python, C#, Java, Go...

>[!tip] Cosa sono le API?
>Le API sono un’interfaccia che permette la comunicazione tra il backend e il frontend (tra browser e server).
## Git

>[!info] Termini
>- **Repository**: set di commit, branch e tag
>	- Assumiamo che 1 progetto sia 1 repo
>- **Working copy**: set di file tracciati nella copia locale
>- **Commit**: codice del progetto in un determinato momento
>- **Branch**: linea di sviluppo. E' un insieme ordinato di commit
>- **Merge**: l'azione di fondere due o più branch
>- **Tag**: un'etichetta personalizzata allegata a un commit
>- **Fork**: un nuovo repository che è una copia di uno esistente
>- **Pull/Merge request**: una richiesta di unire il codice da un fork o branch al repository/branch padre

**Commit**
E' un'istantanea del repository in un determinato momento.
Identificato dallo `SHA1` (algoritmo usato per l'hashing di git) del commit stesso.

Metadati:
- data + autore, data + committer
- commento obbligatorio
- $0$, $1$, o più genitori
- tree: hash di tutti (~) i file nel commit

**Staging**
Il commit può contenere un sotto insieme delle modifiche

---
### Branch

>[!tip] Comandi
>``` js
>git branch <nome> //crea un nuovo puntatore branch
>git checkout <nome> //passa al branch specificato
>git checkout -b <nome> //crea e passa immediatamente al nuovo branch
>```

>[!info] Checkout e cherrypick
>- **checkout**: sposta la cwd alla branch specifica
>- **cherrypick**: è una sorta di rebase, ma non sull'ultima versione. Quindi, non aggiunge, ma sovrascrive

**Main**
- Solo codice stabile, testato e rilasciato
- Merge in: solo da realise
- Tag: ogni merge su main riceve un tag di versione

**Develop**
- Cronologia completa delle funzionalità in sviluppo
- Merge da: riceve le nuove feature da `feature-*`

**Feature-\***
- Lavoro isolato su una nuova funzionalità
- Ramifica da develop
- Unisce in develop
- Regola: Non interagisce mai con `main`

### Remote

Riferimenti ai branch in repository remoti. **Origin** è il nome remoto predefinito.
Il tracking avviene attraverso branch locali con relazione diretta a un remoto.
Facilita l'uso dei comandi `git pull` e `git push`.

---
#### REST

E' uno stile architetturale per sistemi  ipermediali distribuiti.
L'obiettivo è quello di trasferire la rappresentazione delle risorse

Gli identificatori sono usati per indentificare (no way) una risorsa, in particolare si utilizzano gli URL.

---
### JSON e YAML

#### JSON (JavaScript Object Notation)

E' un formato leggero per lo scambio di dati, utilizzato anche per archiviare dati.

```json
{
	"user": {
		"firstName": "John",
		"lastName": "Smith",
		"age": 27
	}
}
```

Utilizza solo due concetti familiari:
- `object`
- `array`

**Oggetto**
E' una collezione non ordinata di coppie (nome, valore), racchiusa tra parentesi graffe.
- *nome*: stringa tra " ", unica all'interno dell'oggetto (come chiave dei dizionari python)
- *valore*: numero, stringa, booleano, null, array, object

```json
{
	"WASA": {
		"name": "Web and Software Architecture",
		"semester": 1
	}
}
```

**Array**
E' un elenco ordinato di valori, separati da virgole, racchiuso tra parentesi quadre.

```json
{
	"wasaWeekdays": ["tuesday", "thursday"]
}
```

>[!example]
>```json
>{
>	"anyObject": {
>		"aNumber": 42,
>		"aString": "This is a string",
>		"aBoolean": true,
>		"nothing": null,
>		"anArray": [1, {"name": value, "anotherName": 12}, "someting else"]
>	}
>}
>```

#### YAML

E' un linguaggio di serializzazione dei dati, utile per i file di configurazione per archiviare o scambiare dati.

```yaml
user: 
	firsName: John
	lastName: Smith
	age: 27
```

---
### API

> [!info] ![[4648b89d193fcf365bc70138e959553c.jpg|70]]
> E' la definizione delle interazione consentite tra due parti di un software.

La sua funzione è quella di *"contratto"*, specificando come un pezzo di codice o un servizio può interagire con un altro.

#### Elementi di un'API

Un'API definisce il contratto di interazione tra il *consumer* e *provider*.
Essa specifica:
- Le richieste possibili
- I parametri delle richieste
- I valori di ritorno
- Qualsiasi formato di dato richiesto (JSON, XML, YAML,...)

>[!tip] Benefici
>- Interfaccia esplicita: definisce chiaramente le aspettative e le modalità di interazione
>- Contratto Infrangibile: Stabilisce un insieme di regole che entrambe le parti devono rispettare
>- Information Hiding: La logica interna del provider rimane nascosta al consumer. Il client deve solo conoscere l'interfaccia

>[!info] API locali e remote
>**Locali**
>- API per linguaggi di programmazione
>- API del sistema operativo
>- API delle librerie software
>- API hardware
>
>**Remote**
>- Interfacce di programmazione basate su protocolli di rete (tipicamente HTTP)



---
### Go

Le funzioni Go sono raggruppate in pacchetti. Un pacchetto è uguale a una directory.

Ogni pacchetto è composto da uno o più file nella stessa directory.

>[!info] Import
>Un file può importare altri pacchetti
>``` Go
>import (
>	"fmt"
>	"math/rand"
>)
>```

>[!example] Hello word
>Importiamo il pacchetto `fmt`, che contiene funzioni per la formattazione e lal stampa del testo
>```Go
>package main
>
>import "fmt"
>
>func main(){
>	fmt.Println("Hello, world!")
>}
>```
>>[!tip]
>>E' possibile utilizzare le funzioni del pacchetto importato se il loro nome inizia con la lettera *maiuscola* e lo stesso vale per le variabili (es. `math.Pi`)

>[!info] Dichiarazione variabili
>```Go
>var i int
>//stessa sintassi per i 'const' invece di 'var'
>var i int = 3
>//stessa sintassi per 'const'
>var i = 3
>//tipo inferito; funziona per 'const', ma è senza tipo (untyped)
>i := 3
>//non si può usare con 'const'
>```

>[!info] Tipi di dati di base
>- `bool`
>- `string`
>- `int`, `int8`, `in16`, `int32`, `int64`
>- `uint`, `uint8`, `uint16`, `uint32`, `uint64`, `uintptr`
>- `byte` (alias di `uint8`)
>- `rune` (rappresenta un codepoint Unicode)
>- `float32`, `float64`
>- `complex64`, `complex128`

>[!warning] Costanti numeriche
>Le costanti senza tipo `untyped` assumono un tipo solo quando vengono usate. Possono essere utilizzate in contesti che richiedono tipi numerici diversi (com `int` o `float64`), purché il valore rientri nel range.

#### Web backend con Go

Go include una libreria completa nello standard package `net/http`.
>[!info]
>- `http.Handler`: è un'interfaccia usata per gestire le richieste
>- `http.HandleFunc`: funzione per associare un percorso a una funzione gestore
>- `http.ListenAndServe`: avvia il server HTTP
>>[!example]
>>```Go
>>func handler(w http.ResponseWriter, r *http.Request)
>>```

---
### Frontend

#### HTML
E' un linguaggio *markup* standard per le pagine web ed è un linguaggio *descrittivo*.

E' definito da un tag di *apertura*, il contenuto e un tag di *chiusura*.

```html
<tagname> content </tagname>
```

>[!info] Struttura del documento
>![[Pasted image 20251120142059.png]]

>[!example] Hello World
>
>
>```html
><!DOCTYPE html>
><html>
><head>
>	<title> Titolo della Pagina </title>
></head>
>	<body>
>		<h1> Questa è un'intesazione </h1>
>		<p> Questo è un paragrafo. </p>
>		<p> Questo è un altro paragrafo. </p>
>	</body>
></html>
>```

---
### JavaScript

E' un linguaggio compilato just-in-time (il browser ottiene il codice JavaScript dal sito, lo compila utilizzando il JavaScript engine del browser e lo esegue).

Può essere aggiunto al documento html in tre modi:
1. Interno/inline: all'interno del tag `<script>` nella sezione `<head>` o `<body>`
2. Esterno: collegando un file `.js` esterno usando il tag `<script scr = "file.j"></script>`
	- Best practice: collocare gli script esterni prima della chiusura del tag `</body>` per migliorare la velocità di caricamento 
3. HTML event header: direttamente negli attributi html, sebbene questa pratica sia sconsigliata

>[!example]
>```js
>let a = 1; // uno statement
>let b = 2; // un altro statement
>// commento su riga singola
>/* Commento
>multilinea
>*/
>```

#### Variabili

- **var**: con scope di funzione
- **let**: con scope di blocco
- **const**: con scope di blocco, non può essere riassegnata
- **assegnazione senza dichiarazione**: assegnazione deprecata

>[!info] Scope di blocco vs scope di funzione
>- Scope di funzione (var): le variabili dichiarate con `var` sono accessibili ovunque all'interno della funzione
>- Scope di blocco: le variabili dichiarate con `let` e `const` sono limitate al blocco di codice immediato (delimitato da parentesi graffe {}) in cui sono definite

#### Hoisting (sollevamento)

JavaScript sposta le dichiarazioni (ma non le inizializzazioni) in cima allo scope in fase di compilazione.

- `var`: sia la dichiarazione che l'inizializzazione implicita a `undefined` vengono sollevate
- `let/const`: la dichiarazione viene sollevata, ma non l'inizializzazione. L'accesso prima della dichiarazione esplicita causa un `ReferenceError`

 