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

Consente di costruire