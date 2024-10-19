>[!info] Programma
>- Algebra relazionale
>- Progettazione di una base di dati
>- Organizzazione fisica dei dati
>- Controllo della concorrenza

### Sistema informativo

E' la componente di una organizzazione che viene utilizzata per gestire (acquisire, processare, memorizzare, comunicare) le informazioni di interesse.

Opera a supporto delle altre componenti dell’organizzazione

#### Cosa succedeva prima?

Prima dell'introduzione dei moderni sistemi di gestione dei database, ogni applicazione gestiva i propri dati tramite file privati. 
Questi file erano organizzati in modo sequenziale, il che significava che i dati venivano memorizzati e letti in un ordine predefinito.

Le applicazioni erano scritte in linguaggi di programmazione orientati alla gestione dei file, come `Cobol` o `PL/1`, che facilitavano la manipolazione dei dati direttamente attraverso il file system. 

La gestione dei dati avveniva, dunque, tramite il file system, con tutte le limitazioni che questo comportava, come la difficoltà di accedere a dati non sequenziali o di condividere informazioni tra applicazioni diverse.

##### Svantaggi

- Ridondanza: se due applicazioni usavano gli stessi dati, questi venivano replicati
- Inconsistenza: l’aggiornamento di un dato poteva riguardare una sola copia del dato
- Dipendenza dei dati: ogni applicazione organizzava i dati tenendo conto dell’uso che doveva farne

Ridondanza e inconsistenza sono due difetti strettamente legati perché la prima aumenta il rischio che le copie dei dati non siano aggiornate in modo uniforme, causando incoerenze.

---
### Database

E' un insieme di file mutuamente connessi.
Gli insiemi di dati sono organizzati in diverse strutture dati che ne facilitano la creazione l'accesso e l'aggiornamento e ottimizzano la gestione delle risorse fisiche.

I **Sistemi di Gestione di Base Dati** (Database Management System - DMS) sono strumenti software per la gestione di grandi masse di dati residenti su  memoria secondaria.

I **dati** servono per registrare l'informazione in formato elettronico.
Si dividono i dati strutturati e non strutturati.

- Dati strutturati: gli oggetti rappresentati da brevi stringhe di simboli e da numeri
- Dati non strutturati: testi scritti di un linguaggio naturale

La struttura dell'informazione dipende da come viene utilizzata e può essere modificata nel tempo.


Qual è l'obiettivo di una bd?

Facilita il recupero di informazioni che abbiamo registrato nella tabella.

Quando noi inseriamo dei dati, non hanno significato. i dati devono essere interpretati.
Quando progettiamo un data base i dati devono avere un nome che ci fa capire cosa sono.

Modelli
modello logico: indipendenti dalle strutture fisiche

modelli concettuali: progettiamo cosa vogliamo progettare e come.

Modello relazionale: abbiamo oggetti che sono record (relazioni), campi (informazioni di un certo oggetto) e informazioni d'interesse

L'insieme degli attributi che definiscono le informazioni si chiama schema delle relazioni

Nello schema c'è il tipo dell'attributo.

Le tuple costituiscono le istanze (tabelle)

La cardinalità è il numero di tuple.

Il modello relazionale è stato ideato negli 70', negli 80' sono usciti i primi modelli a oggetti.

![[Pasted image 20240925163920.png]]

schemi...


Nello schema logico separo le cose in modo tale da inserirle una volta sola
Quando creo la lista esterna, combino le due tabelle in modo tale da vedere tutte le informazioni.

Le viste possono esser usate per dare l'accesso solo ad alcuni campi.

Lo schema è invariato nel tempo (aspetto intensionale)
i valori attuali sono quelli estensionali e cambiano nel tempo.

I dati devono soddisfare dei vincoli che esistono nella realtà di interesse.
(vedi vincoli nelle slides).

Le bd consentono un uso concorrente delle informazioni e dobbiamo utilizzare dei sistemi.

---
### Modello relazionale

Proposto negli anni 70 per favorire l'indipendenza dei dati, disponibile nel 1981.

Basato sul concetto matematico di relazioni (volgarmente chiamate tabelle).
Dati e relazioni tra dati e insiemi diversi sono rappresentati come valore

L'attributo master deve avere un valore unico

Significato di relazioni:
relazione matematica: combinazioni di elementi

relazione secondo il modello relazionale dei dati

relazione che rappresenta una classe di fatti, nel modello entity-relationship viene rappresentata come associazione

**Su cosa si basa modello relazionale?**
Dominio: un insieme infinito di valori (l'insieme dei numeri interi)

Come si costruisce una tupla di una relazione?

Lo faccio rispettando i vincoli ma soprattutto le dipendenze relazionali (vengono fuori dall'analisi dei dati).

Un insieme di tuple è un'istanza di relazione.

Se abbiamo k domini abbiamo una relazione data da una lista ordinata di valore tale che v1 appartiene a D1 ecc.

Una relazione matematica è un qualsiasi sottoinsieme del prodotto cartesiano di uno o più domini.
una relazione che è sottoinsieme del prodotto cartesiano di kk domini si dice k.

Gli elementi di una relazione sono detti tuple. Il numero di tuple in una relazione è detto cardinalità.

Le tuple di una relazione sono tutte distinte dai vincoli sugli insiemi.

Il grado è il numero di domini che partecipano al prodotto cartesiano.

Quasi sempre si usano domini predefiniti, comuni ai linguaggi di programmazione.

##### Come si interpretano i dati in una tabella?

Assegniamo dei nomi agli attributi e alla tabella

![[Pasted image 20240926133117.png|500]]

Se cambia lo schema, cambia il significato dei dati
A parità di domini, il significato ce lo da lo schema.

Un attributo è definito dal nome e dal dominio.

Se R è un insieme di attributi , un'ennupla su R è una funzione definita si R che associa ogni attributo A in R un elemento dom(A).

Se t è un'ennupla su R e A è un attributo in R, allora con t(A) indicheremo il valore assunto dalla funzione t in corrispondenza dell'attributo A.

Lo schema di una base di dati è un insieme di schemi di relazione con nomi differenti.

Basi di dati relazionale: insieme di istanze.

I valori Null rappresentano mancanza di informazione o il fatto che l'informazione non è applicabile.

Vincoli di integrità che descrivono proprietà specifiche del campo di applicazione e quindi delle informazioni ad esso relative modellate attraverso la base di dati.

Una chiave di una relazione è un attributo o insieme di attributi che identifica univocamente una tupla. Le chiavi di uno schema si definiscono con le dipendenze funzionali.

Una chiave è un attributo o un insieme di attributi.
Deve soddisfare due condizione:
1. Per ogni istanza di R, non esistono due tuple distinte che hanno gli stessi valori per tutti gli attributi in X.
2. Nessun sottoinsieme proprio di X soddisfa la condizione 1.


Una chiave è anche superchiave, ma una superchiave potrebbe non essere chiave.

Una relazione potrebbe avere più chiavi alternative, si sceglie quella più usata o quella composta da un numero minore di attributi (chiave primaria).

Se metto due foreign keys separate è un errore perché la chiave non è data dai singoli ma per esempio dalla coppia.

Come sono fatte le dipendenze funzionali?
Una dipendenza funz. stabilisce una un particolare legame semantico tra due insiemi non-vuoti di attributi X e T appartenenti a uno schema R

Questo vincolo si scrive X -> Y e si legge X determina Y.

Quando usiamo le prime lettere dell'alfabeto intendiamo i singoli attributi, quando usiamo le ultime intendiamo gli insiemi di attributi.

Ciò che si applica agli insiemi, vale per i singoli ma non viceversa.

Supponiamo di avere uno schema di relazione VOLI (CodiceVolo, Giorno, Pilota, Ora)

Che vincoli possiamo estrarre?
Un volo con lo stesso codice parte alla stessa ora (codiceVolo determina ora)
Esiste un solo volo con un dato pilota, in un dato giorno a una data ora.

---
### Algebra relazionale

E' un operatore formale, nel senso che non esiste un linguaggio eseguibile.
E' procedurale: l'interrogazione consiste in un'esperessione in cui compaiono operatori dell'algebra e istanze di relazioni della base di dati, in una sequenza che prescrive in maniera puntuale l'ordine delle operazioni e i loro operandi.

#### Proiezione

Si denota con il simbolo $\pi_{A_1, A_{2},\dots,A_{k}}(r)$

Il pedice corrisponde agli attributi

Permette di selezionare solo alcune colonne (attributi).

![[Pasted image 20240926153638.png|500]]

Non ci sono duplicati, l'algebra relazionale è su base insiemistica quindi tutti i duplicati vengono eliminati.

La cardinalità può essere minore della cardinalità originale.

Per avere la stessa cardinalità basta aggiungere la chiave 

#### Selezione

Si denota con il simbolo $\sigma_{C}(r)$

Seleziona le tuple di r che soddisfano la condizione C
Seleziona solo le righe che soddisfano una data condizione

La condizione di selezione è un'espressione booleana in cui termini semplici sono del tipo

$A\Theta B$
$A\Theta'a'$

$\Theta$ è un operatore di confronto
A e B sono due attributi con lo stesso dominio
a è un elemento di dom(A)

![[Pasted image 20240926154616.png|500]]

Con la selezione non c'è il problema del collasso delle tuple.

#### Unione

Consente di costruire una relazione che contiene tutte le ennuple che appartengono ad almeno uno dei due operandi.

Nel risultato avremo un

Si denota con il simbolo $\cup$

Può essere applicata a due istanze solo in determinate situazioni:
Quello che noi andiamo a unire sono il risultato di operazioni precedenti.
Devo essere sicuro che abbiamo schemi union compatibili

1. Hanno lo stesso numero di attributi
2. Gli attributi corrispondenti devono essere definiti sullo stesso dominio

Non è necessario che gli attributi abbiano lo stesso nome

Esempio
Se ho due istanze e die schemi di relazione in cui all'ultimo posto compare in uno l'età e nell'altro il numero di esami.
Potrebbero essere definiti sullo stesso dominio, non avrebbe senso unire due relazioni che hanno questi attributi in colonne corrispondenti

Possiamo filtrare gli elementi che ci impediscono di fare un'unione

![[Pasted image 20241002153701.png|500]]

Possiamo effettuare l'unione perché tutti i campi vengono da un dominio che ha una stringa e occupano lo stesso posto.


![[Pasted image 20241002153829.png|500]]

L'unico problema che esce fuori è che non sappiamo più distinguere i docenti dagli amministrativi.

La tupla "Verdi" è stata riportata una sola volta.

In SQL il risultato di una query non segue la regola insiemistica ma se ci sono due query coordinate unite da un operatore insiemistico UNION, la regola vale di nuovo.

Altro esempio

![[Pasted image 20241002154326.png|500]]

Queste due istanze non possono più essere unite perché c'è un attributo inn più nello schema degli amministrativi.

Come si risolve?

Si effettua una proiezione sugli attributi comuni e poi si effettua l'unione.

![[Pasted image 20241002154657.png|500]]

Non sono union compatibili.
Nome e codice hanno lo stesso ordine, da una parte ho anni di servizio dall'altra ho dipartimento.

Ne devo togliere una per parte.
•Soluzione: proiettare su un sottoinsieme di attributi che abbiano lo stesso tipo (e che abbiano un significato compatibile)

![[Pasted image 20241002155246.png|500]]

Il dominio di dipartimento e mansioni sono dello stesso dominio (sono entrambe stringhe) ma non ha senso fare l'unione perché non hanno lo stesso significato.

Proiettare sugli attributi comuni e poi fare l'unione.

#### Differenza

Si applica a operandi union compatibili.

Dobbiamo avere attributi che appartengono al primo operando e non appartengono al secondo operando
L'ordine degli operandi è significativo

Si denota con il simbolo $r_{1}-r_{2}$
![[Pasted image 20241002155710.png]]

Tutto ciò che sta in $r_{2}$ non ci interessa
Ci interessa togliere le tuple che stanno in $r_{2}$ e $r_{1}$.

![[Pasted image 20241002155819.png|500]]

$\text{Studenti - Amministrativi = studenti che non sono anche amministrativi}$

![[Pasted image 20241002160045.png]]

$\text{Amministrativi - Studenti = amministrativi che non sono anche amministrativi}$

![[Pasted image 20241002160055.png]]

Stiamo assumendo in maniera arbitraria che un amministrativo studia nello stesso dipartimento in cui lavora (il che non è sempre vero).

Proiettiamo su nome e codice fiscale

#### Intersezione

Si applica su operandi union compatibili

Consente di costruire una relazione contenente tutte le tuple che appartengono a entrambi gli operandi

Si denota con il simbolo $\cap$

![[Pasted image 20241002160922.png|500]]

E' commutativa

![[Pasted image 20241002160951.png|500]]

---

### Informazioni in più relazioni

Capita molto spesso che le informazioni che interessano per rispondere a un interrogazione sono distribuite in più relazioni, in quanto coinvolgono più oggetti in qualche modo associati

Serve individuare le relazioni in cui si trovano le informazioni che ci interessano e combinare queste informazioni in maniera opportuna.

#### Prodotto cartesiano

Consente di costruire una relazione contenente tutte le ennuple che si ottengono concatenando una ennupla del primo operando con una ennupla del secondo operando.

Si denota con il simbolo $\times$
$$r_{1}\times r_{2}$$

Si usa quando le informazioni che servono a rispondere a una query si trovano in relazioni diverse.

![[Pasted image 20241002163720.png]]

**Query**: Dati clienti e degli ordini ($\text{Ordine} \times \text{Cliente}$)

![[Pasted image 20241002163919.png]]

Operazione di ridenominazione: l'unica che agisce sullo schema.

![[Pasted image 20241002164213.png]]

Vengono unite molte più tuple del dovuto
E molte tuple non hanno senso.

![[Pasted image 20241002164259.png]]

Come tiriamo via le tuple che non hanno senso?
Utilizziamo la selezione

![[Pasted image 20241002164400.png]]


![[Pasted image 20241002164458.png]]

#### Join naturale

Consente di selezionare le tuple del prodotto cartesiano dei due operandi che soddisfano la condizione.

![[Pasted image 20241002165628.png]]

(dove R1 ed R2 sono i nomi delle relazioni operando e A1,A2,..., Ak sono
gli attributi comuni, cioè con lo stesso nome, delle relazioni operando) eliminando le ripetizioni degli attributi.

![[Pasted image 20241003131121.png]]

Nel join naturale gli attributi della condizione che consente di unire solo le ennuple giuste hanno lo stesso nome

Vengono unite le ennuple in cui gli attributi hanno lo stesso valore.

![[Pasted image 20241003131557.png]]

Le colonne duplicate vengono eliminate 

Risultato corretto:

![[Pasted image 20241003133208.png]]

Due casi limite del join naturale

Due attributi con lo stesso nome ma nessuna tupla in corrispondenza di quell'attributo ha lo stesso valore, restituisce un'istanza vuota.

Se non c'è alcun nome degli attributi in comune, il join diventa un prodotto cartesiano.
E' fondamentale di ridenominare alla rovescia gli attributi in modo tale che abbiano lo stesso nome.

Il join ha senso quando gli attributi con lo stesso nome devono avere anche lo stesso significato.

![[Pasted image 20241003135408.png]]

Il join va effettuato tra `Artista.C#` e `Quadtro.Artista`, quindi si usa un $\theta - join$ oppure una ridenominazioine.

#### $\theta \text {-join}$

Consente di selezionare le tuple del prodotto cartesiano dei due operandi che soddisfano una condizione del tipo
$$
A \theta B
$$
dove

- $\theta$ è un operatore di confronto $\theta \in \{ <, =,>, \leq, \geq \}$
---

### Condizioni che implicano il quantificatore universale

Fino ad ora abbiamo visto query che implicavano condizioni equivalenti al quantificatore esistenziale.

Il meccanismo di valutazione consente di rispondere facilmente a questo tipo di query.

Infatti, in qualunque posizione appaiono nell’espressione di algebra relazionale, la valutazione delle condizioni avviene in sequenza, tupla per tupla, e quando si incontra una tuple che soddisfa le condizioni, questa viene inserita nel risultato (eventualmente parziale).

Query: Codici dei clienti che hanno effettuato un ordine (sottinteso: almeno) per più di 100 pezzi

![[Pasted image 20241009155755.png|500]]

Si proiettano sui codici dei clienti (in questo caso potrebbe non interessarci mantenere i duplicati).

![[Pasted image 20241009155923.png|500]]

- La condizione potrebbe richiedere la valutazione di interi gruppi di tuple prima di decidere se inserirle tutte, qualcuna o nessuna nella risposta
- Le tuple non sono rodiante
- La valutazione delle condizioni avviene in sequenza, tupla per tupla, e una volta inserita una tupla nel risultato non possiamo più eliminarla
- In questo caso la condizione equivale a valutare il quantificatore universale


![[Pasted image 20241009160201.png|500]]

(vedi slide)

>[!warning]
>Fare attenzione sempre alla union compatibilità perché non si può fare la sottrazione tra elementi non union compatibili

---

#### Altro esempio

Vogliamo risolvere delle query che richiedono di confrontare campi di tuple che stanno nella stessa relazione.

Non possiamo accederci direttamente.

Query: Nomi e codici degli impiegati che guadagnano quanto o più del loro capo

![[Pasted image 20241009161432.png|500]]

Posso solo sapere chi è capo e chi no, non posso sapere chi guadagna più del capo.

L'unico modo è mettere in fila le tuple.
Il join naturale non ci serve perché otterrei l'istanza stessa.

1. Creo una variabile relazionale con la copia dell'istanza stessa
2. Faccio un $\theta$-join bypassando il join naturale
3. Faccio il prodotto cartesiano
4. Confronto lo stipendio del capo con quello dell'impiegato

Se volessi controllare l'impiegato che guadagna più di tutti?

Dovrei confrontare a coppie.
Faccio il $\theta$-join tra le istanze e poi il prodotto cartesiano.
Dopo aver controllato le coppie come faccio a capire quello che ha guadagnato di più?

Nelle coppie, vedo qual è quello che vale di più.

---

### Progettazione di una base di dati relazionale

Supponiamo di voler creare una base di dati che contiene i dati di studenti universitari.

**Dati anagrafici e identificativi**

- Nome e Cognome
- Data, comune e provincia di nascita, matricola
- codice fiscale

**Dati curriculari**

Per ogni esame sostenuto:
- Voto
- Data
- Codice, titolo e docente del corso

La base di dati consiste in una sola relazione con schema:
Curriculum (Matr, CF, Cogn, Nome, DataN, Com, Prov, C#, Tit, Doc, DataE, Voto)

![[Pasted image 20241010142734.png|500]]

**Ridondanza**

1. I dati anagrafici di uno studente sono memorizzati per ogni esame sostenuto dallo studente

2. I dati di un corso sono memorizzati per ogni esame sostenuto per quel corso.

La *ridondanza* da luogo a spreco di spazio di memoria e anomalie di aggiornamento, inserimento e cancellazione.

**Anomalia di aggiornamento**

Se cambia il docente del corso il dato deve essere modificato per ogni esame sostenuto per quel corso.

![[Pasted image 20241010143617.png|500]]

**Anomalia di inserimento**

Non posso inserire i dati anagrafici si uno studente finché non ha sostenuto almeno un esame a meno di non usare valori nulli (spreco di spazio), idem per i corsi

![[Pasted image 20241010143629.png|500]]


**Anomalia di cancellazione**

Eliminando i dati anagrafici in uno studente potrebbero essere eliminati i dati di un corso(se lo studente è l'unico ad avere sostenuto l'esame di quel corso).

![[Pasted image 20241010143641.png|500]]


La base di dati consiste in tre schemi di relazione:
- Studente (Matr, CF, Cogn, Nome, Data, Com, Prov)
- Corso (C#, Tit, Doc)
- Esame (Matr, C#, Data, Voto)

In realtà è rimasta un'anomalia, perché comune determina provincia.
Se ho lo stesso comune devo avere la stessa provincia.

![[Pasted image 20241010144021.png|500]]

**Ridondanza**

Il fatto che un comune si trova in una certa provincia è ripetuto per ogni
studente nato in quel comune

**Anomalia di aggiornamento**

Se un comune cambia provincia (in seguito alla creazione di una nuova
Provincia) devono essere modificate più tuple

**Anomalia di inserimento**

Non è possibile memorizzare il fatto che un certo comune si trova in una certa
provincia se non c’è almeno uno studente nato in quel comune

**Anomalia di cancellazione**

Se vengono eliminati i dati anagrafici di uno studente potrebbe perdersi l’informazione che un certo comune si trova in una certa provincia (se è l’unico studente nato in quel comune.

La soluzione è dividere ulteriormente

La base dati consiste di quattro schemi di relazione:

- Studente (Matr, CF, Cogn, Nome, Data, Com)
- Corso (C#, Tit, Doc)
- Esame (Matr, C#, Data, Voto)
- Comune (Com, Prov)

![[Pasted image 20241010144402.png|500]]

Uno schema di base dati è detto "buono" se non presenta:
- Ridondanze
- Anomalie di aggiornamenti, inserimento e cancellazione

#### Come si progetta uno schema "buono"?

 I problemi esaminati precedentemente derivano dal fatto che sono rappresentati in un'unica relazione e vengono superati quando i concetti vengono rappresentati nelle tre relazioni distinte.

Spesso la cattiva progettazione, cioè l'errore di rappresentare più concetti nella stessa relazione, deriva dalla necessità di recuperare informazioni relative non agli oggetti ma anche alle loro associazioni.

---
Per progettare uno schema “buono” occorre rappresentare separatamente ogni concetto in una relazione distinta.

![[Pasted image 20241010145023.png|500]]

I concetti sono mischiati (ordine, articolo e cliente).

- Se devo aggiornare la città di un cliente, devo aggiornare tutte le tuple, e in caso in inconsistenze non sono più in grado di sapere qual è quella giusta
- Se cancello un articolo che va fuori produzione, rischio di perdere i dati di un cliente che ha ordinato solo quell'articolo
- Per inserire un articolo deve esserci per forza un cliente che lo ordina

**Soluzione**

![[Pasted image 20241010145654.png|500]]

#### Come possono essere individuati i concetti rappresentati in una relazione (ben progettata)?

Possiamo individuare i concetti rappresentati in una relaziona tramite una *chiave* che è un attributo o un gruppo di attributi che determinano una particolare *dipendenza funzionale* che è un particolare tipo di *vincolo*.

### Vincoli

Quando si rappresenta una realtà di interesse in una base di dati deve essere possibile rappresentare anche tali condizioni.

Un *vincolo* è la rappresentazione nello schema di una bae di dati di una condizione valida nella realtà di interesse

Un'istanza della base di dati è *legale* se soddisfa tutti i vincoli (cioè se è una rappresentazione fedele della realtà).

### Definizione e verifica dei vincoli nei DBMS

Un DBMS permette di:

- definire insieme allo schema della base di dati i vincoli
- verificare che un’istanza della base di dati sia legale
- in base a speciali vincoli predefiniti, impedire l’inserimento di tuple che violerebbero tali vincoli

Ed è dotato di procedure per la verifica dei vincoli che ricorrono più frequentemente:

- Vincoli di dominio
- Chiavi
- Contenimento di domini

Per la verifica di altri tipi di vincoli può essere necessario definire opportune procedure

---
### Dipendenze funzionali

Uno schema di relazione R è un insieme di attributi {$A_{1}, A_{2}, \dots,A_{n}$}

**Notazione**

- $R=A_{1},A_{2},\dots,A_{n}$
- le prime lettere dell'alfabeto ($A,B,C,\dots$) denotano singoli attributi
- le ultime lettere dell'alfabeto ($X,Y,\dots$) denotano insiemi di attributi
- Se X e Y sono insiemi di attributi XY e X u Y

#### Tupla

Uno schema di relazione R = {$A_{1}, A_{2}, \dots,A_{n}$}

Una tupla $t$ su R è una funzione che associa a ogni attributo $A_{i}$ in R un valore $t[A_{i}]$ nel corrispondente $dom(A_{i})$

![[Pasted image 20241010153511.png|500]]

Se X è un sottoinsieme di R e t1 e t2 sono due tuple su R 

![[Pasted image 20241010153555.png|500]]

#### Istanza di relazione

Dato uno schema di relazione R

Un'istanza di R è un insieme di tuple su R

TUTTE le “tabelle” che abbiamo visto finora negli esempi sono istanze di qualche schema di relazione

#### Dipendenze funzionali

Dato uno schema di relazione R

una dipendenza funzionale su R è una coppia ordinata di sottoinsiemi non vuoti X e Y di R.

**Notazione e terminologia**

- $X \to Y$
- X determina funzionalmente Y oppure Y dipende funzionalmente da X
- X = parte sinistra della dipendenza o determinante
- Y = parte destra della dipendenza o dipendente

Dato uno schema su R e una dipendenza funzionale $X \to Y$ su R,

un'istanza funzionale $r$ *soddisfa* la dipendenza funzionale $X \to Y$ se:

$$
\forall t_{1}, t_{2} \in r (t_{1}[X]= t_{2}[X] \implies t_{1}[Y]=t_{2}[Y])
$$
>[!info] Nota
>Ovviamente se $t_{1}\neq t_{2}$ la dipendenza è soddisfatta comunque siano i valori di $t_{1}[Y]$ e $t_{2}[Y]$

---

![[Pasted image 20241016153105.png|500]]

Possiamo osservare che se l'istanza è legale deve soddisfare entrambe le dipendenze.

Se `A -> B` e `B -> C` allora `A -> C`

Dato uno schema di relazione R e un insieme F di dipendenze funzionali su R ci  sono delle dipendenze funzionali che non sono in F, ma che sono soddisfatte da ogni istanza legale di R.

#### Esempio 1

`Matricola -> CodiceFiscale` e `CodiceFiscale -> DataNascita`

devono essere sempre soddisfatte da ogni istanza legale, ma allora sarà sempre soddisfatta anche `Matricola -> DataNascita`

#### Esempio 2

`CodiceFiscale -> Nome, Cognome`

deve essere soddisfatta da ogni istanza legale, ma allora saranno sempre soddisfatte anche 

`CodiceFiscale -> Nome` e `CodiceFiscale -> Cognome`

### Chiusura di un insieme di dipendenze funzionali

Dato uno schema di relazione R e un insieme F di dipendenze funzionali su Rm la *chiusura di F* è l'insieme delle dipendenze funzionali che sono soddisfatte da ogni istanza legale su R

**Notazione**: $F^{+}$

#### $F^{+}$ e $F$

Se F è un insieme di dipendenze funzionali su R e r è un'istanza di R che soddisfa tutte le dipendenze in F, diciamo che r è un'istanza legale di R

La chiusura di F, denotata con F+ è l’insieme di dipendenze funzionali che sono soddisfatte da ogni istanza legale di R

### Chiave

Dati uno schema di relazione R e un insieme F di dipendenze funzionali, un sottoinsieme K di uno schema di relazione R è una chiave di R se:

$$
K \to R \in F^{+}
$$

- Non esiste un sottoinsieme proprio $K'$ di $K$ tale che $K' \to R \in F^{+}$

La chiave determina R

### Chiave primaria

Dati uno schema di relazione R e un insieme F di dipendenze funzionali, possono esistere più chiavi di R

In SQL una di esse verrà scelta come chiave primaria (non può assumere valore nullo)

#### Esempio

`Studente = Matr CD Cognome Nome Data`

Questo vale nel caso in cui uno studente con lo stesso codice fiscale non possa iscriversi a più corsi di laurea.

### Dipendenze banali

Dati uno schema di relazione R e due sottoinsiemi non vuoti X, Y di R tali che $Y \subseteq X$ si ha che ogni istanza r di R soddisfa la dipendenza funzionale $X \to Y$

![[Pasted image 20241016160643.png|500]]


![[Pasted image 20241016160700.png]]

### Proprietà dipendenze funzionali

Dati uno schema di relazione R e un insieme di dipendenze funzionali F, si ha:

$$
X \to Y \in F^{+} \iff \forall A \in Y (X \to A \in F^{+})
$$

![[Pasted image 20241016161011.png]]

---

### Assiomi di Armstrong

![[Pasted image 20241016164938.png|150]]

Denotiamo con $F^{A}$ l'insieme di dipendenze funzionali definito nel modo seguente

- Se $f \in F$ allora $f \in F^{A}$
- Se $Y \subseteq X \subseteq R$  allora $X \to Y \in F^{A}$ (assioma della riflessività)
- Se $X \to Y \in F^{A}$ allora $XZ \to YZ \in F^{A}$, per ogni $Z \subseteq R$ (assioma dell'aumento)
- Se $X \to Z \in F^{A}$ e $Y \to Z \in F^{A}$ allora $X \to Z \in F^{A}$ (assioma della transitività)

#### Osservazioni

- Nome è contenuto in (Nome, Cognome) quindi se due tuple hanno uguale la coppia (Nome, Cognome) allora avranno sicuramente uguale l'attributo Nome e Cognome

- Codice Fiscale -> Cognome è soddisfatta quando due tuple hanno codice fiscale uguale, allora hanno anche cognome uguale.

	Se la dipendenza è soddisfatta e aggiungo l'attributo indirizzo, avrò che se due tuple sono uguali, lo devono essere su (Cognome, Indirizzo), quindi se soddisfatta


---
### Conseguenze degli assiomi

- Se $X \to T \in F^{A}$ allora $X \to YZ \in F^{A}$ (regola dell'unione)
- Se $X \to Y \in F^{A}$ e $Z \subseteq Y$ allora $Z \to Z \in F^{A}$ (regola della decomposizione)
- Se $X \to T \in F^{A}$ e $WT \to Z \in F^{A}$ allora $WX \to Z \in F^{A}$ (regola della pseudotransitività)

### Chiusura di un insieme di attributi

Siano R uno schema di relazione, F un insieme di dipendenze funzionali su R e X un sottoinsieme di R.

La chiusura di X rispetto a F, denotata con $X^{+}_{F}$ è definito come:
$$
X^{+}_{F} = \{A|X \to A \in F^{A}  \}
$$
In pratica, fanno parte della chiusura di un insieme di attributi X tutti quelli che sono determinati funzionalmente da X eventualmente applicando gli assiomi di Armstrong

$$
X \subseteq X^{+}_{F} \space (riflessività)
$$


#### Lemma

Siano R uno schema di relazione e F un insieme di dipendenze funzionali su R.
Si ha che:
$$
X \to Y \in F^{A} \text{ se e solo se } Y \subseteq X^{+}
$$
,