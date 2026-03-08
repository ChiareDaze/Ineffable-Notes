>[!info] Appunti presi solo ai fini dell'esame
>- [[#Concetti fondamentali]]
>- Esempi pratici per l'esame
# Concetti fondamentali

### Analisi concettuale
#### Oggetti
Servono per descrivere elementi singoli particolarmente significativi oppure per descrivere esempi.
In  UML un oggetto modella un elemento del dominio che ha "vita propria" ed è identificato mediante l'*identificatore* di oggetto. Di base, è l'*istanza* di una classe.

![[Pasted image 20260305144205.png|250]]

In questo esempio `div_comm` è l'*identificatore* di un oggetto.
Libro è la *classe* di cui l'oggetto ne è istanza.

#### Classi
Una classe modella un insieme di oggetti omogenei (le istanze della classe) ai quali sono associate proprietà statiche (*attributi*) e dinamiche (*operazioni*).
Ogni classe è descritta da:
- un nome
- un insieme di proprietà

![[Pasted image 20260305145005.png|400]]

>[!info] 
>Il diagramma delle classi impone che tutte le sue istanze abbiano un valore di tipo stringa per l'attributo "titolo"

#### Associazioni e link
Un'associazione modella la possibilità che oggetti di due (o più classi) abbiano dei legami.
Le istanze di associazioni si chiamano *link*: se $A$ è un'associazione tra le classi $C_{1}$ e $C_{2}$, un'istanza di $A$ è un link tra due oggetti, uno della classe $C_{1}$ e l'altro della classe $C_{2}$.

![[Pasted image 20260305151054.png|400]]

![[Pasted image 20260305151127.png|400]]

Come gli oggetti sono istanze delle classi, così **i link sono istanze delle associazioni**.
Al contrario degli oggetti, però, i link *non* hanno identificatori specifici. Il link è implicitamente identificato dalla coppia di oggetti che esso rappresenta.

>[!warning]
>Non sono ammessi link uguali
>
>![[Pasted image 20260305153649.png|450]]

>[!example] Esempio prenotazioni
>Si vuole progettare un'app che permette ai clienti di prenotare hotel via web.
>
>Si potrebbe pensare una cosa del genere:
>
>![[20260305-155518.jpg|500]]
>
>Però questo diagramma è inadeguato.
>Dato che non possono esistere due link uguali che collegano le stesse classi, una stessa persona non potrebbe prenotare lo stesso hotel mai più.
>Per aggirare questo problema si può creare la classe `Prenotazione`.
>
>![[20260305-161027.jpg|800]]

>[!info] Associazioni multiple tra due classi
>Tra le stesse classi possono essere definite più associazioni che modellano legami di natura diversa
>
>![[Pasted image 20260305161345.png|400]]

#### Vincoli di molteplicità
UML permette di definire vincoli in un diagramma delle classi.
Un vincolo  di integrità impone ulteriori restrizioni sui livelli estensionali ammessi.

![[Pasted image 20260305163321.png|500]]

- $1\dots 1$: ogni istanza di `Impiegato` deve essere coinvolta in un numero di link dell'associazione "nascita" che va da $1$ a $1$.
	- Dato che non possiamo avere più link tra la stessa coppia di oggetti, questo è equivalente a: ogni istanza di `Impiegato` deve essere legata a una e una sola istanza `Città` (tramite link dell'associazione `nascita`)
- $0\dots^{*}$: ogni istanza di `Città` deve essere coinvolta in un numero di link dell’associazione `nascita` che va “da $0$ all’infinito. È equivalente a dire: ogni istanza di `Città` può essere legata ad un numero qualunque ($0\dots^{*}$) di istanze di `Impiegato` (tramite link dell’associazione `nascita`)

>[!Example] Esempio sovrano
>Supponiamo di voler modellare i sovrani di un regno ormai scomparso. Di ogni sovrano interessa il nome, il periodo in cui ha regnato e il predecessore
>
>Creo la classe `Sovrano`
>
>![[20260305-164705.jpg|200]]
>
>Come possiamo rappresentare il concetto di `Predecessore`?
>Il predecessore è comunque un sovrano che ha un nome, un periodo in cui ha regnato e a sua volta un predecessore. Perciò possiamo fare un'associazione che *insiste più volte sulla stessa classe*
>
>![[20260305-165421 1.jpg|250]]

#### Associazioni con attributi
Supponiamo di voler progettare un sistema che gestisca gli esiti dei test superati dagli studenti di un corso.
Il corso è diviso in moduli e uno studente può superare il testa di ogni modulo al più di una volta.

![[Pasted image 20260305170054.png|500]]

Il problema nasce perché in questo modo non sappiamo dove mettere l'attributo `voto`, poiché non né attributo di `Studente` né di `Modulo`, ma *è una proprietà del legame* tra `Studente` e `Modulo`. E' quindi una proprietà *dell'associazione*.

![[Pasted image 20260305170434.png|500]]

>[!warning]
>Anche in presenza di attributi, la natura dell'associazione non cambia. Il diagramma permette a una stesa coppia di oggetti di formare *al più* un link dell'associazione.
