### Ciclo di vita di un software

1. Studio di fattibilità 
	- comprendere i requisiti di alto livello 
	- valutare costi e benefici 
	-  pianificare le attività e le risorse del progetto 
	-  individuare l’ambiente di programmazione (hardware/software)  

2. Raccolta dei requisiti 
	- Raccolta dei requisiti presso i diversi attori 
	- Stesura e sintesi iniziali 
	- Raffinamento dei requisiti 
	
3. Analisi concettuale dei requisiti 
	- *Obiettivo*: produrre lo schema concettuale dell'applicazione, che definisca in dettaglio cosa l’applicazione dovrà realizzare, indipendentemente dal come 
	- Lo schema concettuale: 
		- Modella i dati di interesse, le loro articolazioni, interrelazioni ed evoluzioni possibili 
		- Specifica i servizi computazionali che l'applicazione dovrà offrire ai diversi utenti
		- Lo schema concettuale è un modello logico-matematico dell’applicazione, e sarà la base da cui partire per le successive attività di progettazione

4. Design dell'applicazione
	-  specifica come l'applicazionen realizza le sue funzioni

5. Realizzazione dell'applicazione (implementazione)
	- Equivale alla scrittura del codice e scrivere la documentazione

6. Integrazione dei componenti e verifica dell'applicazione
	- Le diverse componenti dell’applicazione, sviluppate separatamente, vengono integrate 
	- Si valuta se l’applicazione svolge correttamente, completamente ed efficientemente i suoi compiti 

7. Messa in esercizio
	- L’applicazione viene messa in esercizio ed inizia a funzionare 

8. Manutenzione dell’applicazione 
	- L’applicazione viene monitorata durante l’esercizio 
	- Correzioni ed aggiornamenti vengono prodotti ove e quando necessario


>[!info] Modelli di ciclo di vita del software
>
>
**Modello a cascata (waterfall model)**
>Questo significa che ogni attività inizia quando termina il precedente e ha uno scopo interamente didattico.
>
>**Modello a spirale (o iterativo)**
![[Pasted image 20250226154809.png|300]]
>
>E' come una pipeline

### Analisi concettuale

#### Diagramma delle classi e degli oggetti

**Oggetti UML**

E' una porzione del mondo reale
Identificato attraverso l'identificatore di oggetto

![[Pasted image 20250226162938.png]]

Libro è la classe più specifica di cui `Libro` è l'istamza

**Classe**

Modella un insieme di oggetti omogenei ai quali sono associate proprietà statiche (attributi) e dinamiche (operazioni)

Ogni classe è descritta da: 
-  un nome 
- un insieme di proprietà (astrazioni delle proprietà comuni degli oggetti che sono istanze delle classi)

![[Pasted image 20250226163257.png]]

Un oggetto è identificato da un identificatore univoco
Un diagramma delle classi in generale permette la coesistenza di oggetti identici

![[Pasted image 20250226163537.png]]


#### Associazioni

Modellano la possibilità che oggetti di classi diverse abbiano dei legami

![[Pasted image 20250226163624.png]]

Le istanze di associazioni sono chiamate *link*.
Se A è un'associazione tra classi C1 e C2, un'istanza di A è un link tra due oggetti.

![[Pasted image 20250226163819.png]]

I link non hanno identificatori espliciti e quindi non possono esistere link uguali per associazioni *distinte*.

>[!info] Esempio
>Si vuole progettare un’applicazione che permetta ai clienti di prenotare hotel via web
>
>![[Pasted image 20250226164211.png]]
>
>Esiste la classe `Hotel` e la classe `Prenota`, prenota significa che ogni persona può prenotare un hotel.
>
>![[Pasted image 20250226164322.png]]
>
>In questo caso significa che Alice ha prenotato all'hoter "La Pergola"
>
>E se volessimo rappresentare una seconda prenotazione di ‘alice’ presso ‘h1’?
>
>![[Pasted image 20250226164522.png]]
>
>Il diagramma qui sopra impedirebbe ad una stessa persona di prenotare, nella sua vita, lo stesso hotel più volte!
>
>*Come si può fare?*
>
>![[Pasted image 20250226164705.png]]
>
>Diciamo che una prenotazione è legata all'hotel tramite l'associazione `hotel_prenotato` e una prenotazione è legata a Persona tramite l'associazione `cliente_prenotazione`.
>

#### Vincoli di integrità

Un vincolo di integrità impone ulteriori restrizioni (oltre quelle strutturali imposte dal diagramma) sui livelli estensionali ammessi.


![[Pasted image 20250226165947.png]]

Ogni istanza di Impiegato deve essere coinvolta in un numero di link dell’associazione “nascita” che va “da 1 a 1”

Ogni istanza di Città deve essere coinvolta in un numero di link dell’associazione “nascita” che va “da 0 all’infinito”

#### Associazioni con attributi

Supponiamo di voler progettare un sistema per la gestione degli esiti dei voti dei test superati dagli studenti di un corso.
Il corso è diviso in moduli e uno studente può superare il test di ogni modulo al più una volta.

![[Pasted image 20250305084316.png|400]]

Non possiamo aggiungere un attributo “voto” né nella classe Studente né nella classe Modulo. Quindi, come si possono rappresentare i voti conseguiti dagli studenti nei test durante i diversi moduli?

Un voto, non è una proprietà locale di uno studente, né di un modulo, ma è una proprietà del legame tra uno studente e un modulo, è quindi una *prprietà dell'associazione*.



---
### Tipi

Sono dati concettuali, che siano facilmente realizzabili con qualsiasi tecnologia informatica.
I tipi base sono: Intero, Reale, Booleano, Data, Ora, DataOra

**Tipi specializzati**

Serve per rappresentare, per esempio, degli intervalli

![[Pasted image 20250304160143.png|500]]

---

#### Vincoli di identificazione

Mettendo un `id` diciamo che non possono esistere due oggetti con lo stesso attributo.

#### Ereditarietà

Il linguaggio UML permette di implementare l'ereditarietà, quindi il concetto di "sottoclasse".

Per esempio, prendiamo le classi `Studente` e `Persona`. `Studente` può essere considerata una sottoclasse di `Persona`.
`Studente` eredita tutti gli attributi di `Persona` (come in Java).

---

### Operazioni

Un'operazione di una classe ci indica che su quella classe di possono eseguire dei calcoli.
- Si può calcolare un valore a partire da altri dati o operazioni
- Effettuare cambiamenti di stato dell'oggetto, dei link in cui è coinvolto e/o degli oggetti a esso collegati

