>[!info] Programma
>- Combinatoria
>- Spazio di probabilità
>- Variabili aleatorie (discrete e continue)
>- Leggi grandi numeri, teorema del limite centrale

---
# Combinatoria

### Principio Fondamentale

Supponiamo di avere due esperimenti. Il primo esperimento ha $n_{1}$ esiti possibili e, qualunque sia l'esito del primo esperimento, il secondo esperimento ha $n2$ esiti possibili.

Allora il numero delle coppie $(a_{1}, a_{2})$ possibili con $a_{i}$ esito dell'esperimento i-esimo è: 

$$n_{1}\times n_{2}$$
#### Esempio lancio di un dado

$\#\{(a,b): a = faccia\space primo\space lancio, b = faccia\space sencondo\space lancio\}$

Per entrambi gli esperimenti le facce che possiamo ottenere (possibili) sono 6.

Per il principio fondamentale abbiamo che il numero possibile di facce che possiamo ottenere nei due lanci è: $$n_{1}\times n_{2}$$
Quindi: $$6\times6=36$$
>[!info] Notazione
>- $\#$ -> il numero
>- Se A è un insieme $|A|=$ cardinalità di $A=\#A$ 


#### Esempio studenti

Supponiamo di avere 140 studenti.
In quanti modi posso scegliere un rappresentante e un vice?

$n=140$
$$140\times139$$

>[!warning]
>$n_{2}$ è 139 perché dopo aver scelto il rappresentante, gli studenti tra cui scegliere non saranno più 140

---

### Principio fondamentale generalizzato

Supponiamo di avere $r$ esperimenti.

Il primo ha $n_{1}$ esiti possibili. 
Qualunque sia la realizzazione del primo esperimento, il secondo ha $n_{2}$ esiti possibili.
Qualunque sia la realizzazione del secondo esperimento, il terzo ha $n_{3}$ esiti possibili e così via.

Allora il numero delle possibili stringhe $(a_{1}, a_{2},\dots, a_{n})$ dove $a_{i}$ è l'esito dell'esperimento i-esimo $\forall i=1,2,\dots,r$ è $n_{1},n_{2},\dots,n_{r}$

#### Esempio ragazzi e ragazze

Supponiamo di avere 120 ragazzi e 20 ragazze.
In quanti modi posso scegliere un rappresentante e un vice di sesso diverso?

$\#\{(a,b): a = è \space rappresentante, b = è\space vice\}$

Risposta: 
$$120\space ragazzi\times20\space ragazze = 140\space modi\space possibili $$
Per scegliere il vice non è possibile applicare il principio fondamentale perché non sappiamo l'esito del primo esperimento.
Infatti, non sappiamo se il il rappresentante scelto è maschio o femmina.

In questo caso posso risolvere distinguendo i casi.

**Primo caso**
$$\#\{(a,b): a = è \space rappresentante\space F, b = è\space vice\space M\}$$

*Cardinalità*:
$$120\times 20$$

**Secondo caso**

$$\#\{(a,b): a = è \space rappresentante\space M, b = è\space vice\space F\}$$
*Cardinalità*:
$$120\times 20$$

Quindi la risposta è:
$$(120\times 20)+(120\times 20) = 4800$$

---
### Permutazioni

#### Esempio libri

Supponiamo di voler sistemare su uno scaffale 4 libri di matematica, 3 di chimica e 2 romanzi.

1. In quanti modi li posso ordinare?
2. In quanti modi li posso ordinare in modo tale che i libri della stessa materia siano vicini?

**Prima domanda**

Dopo aver messo il primo, rimangono 8 libri da scegliere per il secondo spazio. Una volta scelto il secondo libro, te ne restano 7 per il terzo spazio, e così via.

Quindi:

$$
9 \times 8 \times 7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1 = 9!
$$

**Seconda domanda**

Innanzitutto dobbiamo pensare al possibile ordinamenti delle varie materie, quindi immaginiamo i libri della stessa materia come un unico blocco.

Le materie sono 3, quindi dobbiamo disporli in 3 posti.

Quindi: 
$$
3\times 2 \times 1 = 3!
$$

Ora pensiamo anche a sistemare i vari libri.

Libri di matematica: 
$$
4\times 3\times 2\times 1 = 4!
$$
Libri di chimica: 
$$
3\times 2\times 1=3!
$$
Romanzi: 
$$
2\times 1= 2!
$$
Quindi il numero di modi in cui posso ordinare i libri è:  
$$
3!\times 4!\times 3!\times 2! 
$$

### Definizione permutazioni

Dati $n$ oggetti distinti, le permutazioni di questi $n$ oggetti sono tutti i possibili allineamenti degli $n$ oggetti.

Il numero delle permutazioni di $n$ oggetti e $n!$

##### Dimostrazione

Per ordinare gli $n$ oggetti scelgo il primo (ho $n$ modi possibili) scelgo il secondo (ho $n-1$ modi possibili), $\dots$ , scelgo l'n-esimo.

**Principio fondamentale**
$$
\#permutazioni=n\times(n-1)\times(n-2)\times\dots 
$$
#### Permutazioni con e senza ripetizioni

Supponiamo di voler trovare il numero di anagrammi della parola mela.

Le permutazioni saranno: $4!$

Se volessimo trovare gli anagrammi del nome Emma il numero di permutazioni non è più $4!$ poiché ci sono due lettere uguali.

In generale, quando abbiamo parole di lunghezza $n$ con $r$ lettere distinte, sappiamo che la prima appare $n_{1}$ volte, la seconda $n_{2}$ volte ecc.

Il numero di anagrammi sarà:
$$
\frac{n_{1}}{n_{1}!\times n_{2}!\times n_{r}}
$$
Quindi, scomponendo il problema abbiamo che la `e` e la `a` si ripetono 1 volta, mentre la `m` 3 volte.

Quindi avremo che i possibili anagrammi di Emma sono:
$$
\frac{4!}{1!\times 1!\times 2!}=\frac{4!}{2!}
$$

>[!info] Regola generale per permutazioni
>**Senza ripetizioni**
>\#permutazioni {$n!$}
>
>**Con ripetizoni**
>\#permutazioni $\left\{ \frac{n_{1}!}{n_{2}! \times n! \dots \times n_{R}}   \right\}$


#### Esempio targhe alfanumeriche

Calcolare il numero possibile di targhe alfanumeriche di lunghezza 5.
Si hanno a disposizione 26 lettere e 10 cifre, quindi per ogni entrata ci sono 36 possibili input.
Le targhe sono composte da 5 caratteri quindi si ottiene $36^{5}$.

Per il principio fondamentale avremo che:

$$
\{ \text{\#targhe alfanumeriche di lunghezza 5} \} = 36 \times 35 \times 34 \times 33 \times 32
$$

Supponiamo ora, di voler scegliere 3 lettere e 2 cifre per la targa.

Si dovranno prima scegliere come posizionare le 3 lettere nei 5 posti.

$$
\frac{5!}{3! \times 2!}
$$

Le lettere sono 26 quindi in 3 posizioni si avranno $26^{3}$ esiti, mentre per le cifre $10^{2}$ esisti.

Quindi:

$$
\frac{5!}{3! \times 2!} \times 26^{3} \times 10^{2}
$$
---
### Combinazioni

Supponiamo di voler determinare il numero di insiemi che si possono formare con $r$ oggetti in $n$ oggetti.

Per esempio, quanti insiemi da 3 lettere si possono formare con 5 lettere $A, B, C, D \space e \space E \space ?$

Si può ragionare in questo modo:

La prima carta può essere scelta in 5 modi, la seconda in 4 modi e la terza in 3 modi. Quindi si avranno $5 \times 4 \times 3$ modi per scegliere l'insieme delle 3 lettere tenendo conto dell'ordine.

Tuttavia, ogni insieme di 3 lettere viene in tal modo contato 6 volte (quante sono le permutazioni). Quindi il numero totale di insiemi di 3 lettere che si possono ottenere è:

$$
\frac{5 \times 4 \times 3}{3 \times 2 \times 1} = 10
$$
**In generale**

Dato che $n(n-1)\dots(n-r+1)$ rappresenta il numero di scelte $r$ oggetti tra $n$, tenendo conto dell'ordine nel quale questi vengono selezionati ,e dato che ogni insieme di $r$ oggetti viene in questo modo contato $r!$ volte, si ha che il numero di sottoinsiemi di $r$ oggetti che si possono formare da un insieme di $n$ oggetti è:

$$
\frac{n(n-1)\dots (n-r+1)}{r!} = \frac{n!}{(n-r)! \times r!}
$$

#### Coefficiente binomiale

Definiamo $\binom{n}{k}$, per $k\leq n$, come:
$$
\binom{n}{k} = \frac{n!}{(n-k)! \times k!}
$$

Diremo che $\binom{n}{k}$ rappresenta il numero di combinazioni di $r$ oggetti tra $n$.

Pertanto, $\binom{n}{k}$ è il numero di sottoinsiemi di $r$ oggetti che si possono formare con un insieme di $r$ oggetti, senza il conto dell'ordine della selezione.


*Triangolo di Tartaglia per i coefficienti binomiali*

![[Pasted image 20241019175111.png|500]]

#### Coefficiente multinomiale

Supponiamo di avere 5 studenti che vogliono organizzare una festa e si dividono i ruoli:

- C1: Pulire il locale - 2 persone
- C2: Comprare bibite - 2 persone
- C3: Pubblicizzare la festa - 1 persona

Si possono scegliere gli studenti per C1, dai rimanenti per C2 e dai rimanenti per C3:

$$
\binom{ 5 }{ 2 } \times \binom{ 3 }{ 2 } \times \binom{ 1 }{ 1 } 
$$

Quindi:
$$
\frac{5!}{(5-2)! \times 2!} \times \frac{3!}{(3-2)! \times 2!} \times \frac{1!}{(1-1)! \times 1!} = \frac{5!}{2! \times 2! \times 1!}
$$

**E' la stessa formula utilizzata per gli anagrammi**

Infatti, possiamo assegnare a ogni posizione uno studente e a ogni studente un incarico.
In questo modo, si dovrà solamente calcolare gli anagrammi della stringa "13221" (va bene qualsiasi altra combinazione).

>[!info] In generale
>Se si hanno $n$ oggetti distinti da ripartire in $r$ scatole $s_{1}, s_{2},\dots,s_{r}$ in modo che $\forall i$ che va da 1 $r$ nella scatola $s_{i}$ venga inserito l'oggetto $n_{i}$ dove:
>
>
>
>$$
>n_{1}+n_{2}+\dots+n_{r}=n
>$$
>
>**Quante sono le possibili ripartizioni?**
>$$
>\frac{n!}{n_{1}! \times n_{2}! \times \dots \times n_{r}!} = \binom{ n }{ n_{1},n_{2},\dots,n_{r} } 
>$$
>
>Prende il nome di *coefficiente multinomiale*

Quindi, riprendendo l'esempio della festa, rappresentando il gruppo che svolge $c_{i}$ si ottiene $n_{1} = 2, n_{2} = 2, n_{3} = 1, R=3$.

**Dimostro applicando il principio della combinatoria**

1. Scelgo $n_{1}$ oggetti distinti da mettere in $s_{1}$. In questo modo, ho $\binom{ n }{ n_{1} }$ modi.
2. Scelgo $n_{2}$ oggetti da mettere in $s_{2}$ dai rimanenti. Ottengo $\binom{ n-n_{1} }{ n_{2} }$ modi.
3. Per $n_{3}$ e ottengo $\binom{ n-n_{1}-n_{2} }{ n_{3} }$ modi.

Quindi le ripartizioni totali sono:

![[Pasted image 20241019183232.png]]

---
# Probabilità

Supponiamo di avere un esperimento. Chiameremo *spazio campionario* ($S$) l'insieme dei possibili esiti dell'esperimento.

##### Esperimento 1

Lancio un dado $S=\{ 1,2,3,4,5,6 \}$

##### Esperimento 2

Lancio 2 volte una moneta $S = \{ (T,T),(T,C),(C,C),(C,C),(C,T) \}$

Un evento è descritto matematicamente da un sottoinsieme di $S$, più precisamente dall'insieme degli esiti che lo realizzano.

L'evento "esce un numero pari" è descritto dal $\{ 2,4,6 \} \subset S$

La *famiglia degli eventi* = *famiglia dei sottoinsiemi di S*

#### Proprietà

- Due eventi $E,F \subset S$ si dicono incompatibili se $S \space \cap \space F = \emptyset$
- L'evento $S$ è detto *certo* (nell'esempio del dado l'evento "esce un intero" è dato da $S$)
- Dato un evento $E$, l'evento complementare $E^{c}=S \setminus E$ (per esempio se l'evento è "esce un numero minore o uguale a 2", l'evento complementare è dato da $\{ 3,4,5,6 \}$)
- Le *leggi di De Morgan* $(A \space \cup \space B)^{c}=A^{ c }\space \cap \space B^{ c } = A^{ c } \space \cup \space B^{ c }$
- L'evento *impossibile* è descritto da $\emptyset$

#### Spazio di probabilità

>[!info] Definizione
>Uno spazio di probabilità è descritto dalla coppa $(S,P)$ dove $S$ è lo spazio campionario dell'esperimento e $P$ è chiamata funzione di probabilità, è una funzione definita sulla famiglia degli eventi che soddisfa i seguenti assiomi:
>1. $P(E) \in [0,1] \forall E$ evento cioè $\forall E \subset S$
>2. $P(S) = 1$
>3. Data una successione $E_{1},E_{2},\dots$ di eventi 2 a 2 distinguibili vale:
>
>$$
>P\left( \bigcup_{i=1}^{ \infty } E_{i} \right) = \sum_{i=1}^{ \infty }P(E_{i}) 
>$$
>
>Questo quando $\forall i\neq$ e $E_{i}\space \cap \space E_{j} \neq \emptyset$ ovvero $\forall i \neq j$ abbiamo $E_{i}$ e $E_{j}$ incompatibili.
>
>*Terminologia*: dato $E$ evento, $P(E)$ si dice probabilità dell'evento $E$

#### Proposizione 1

$$
P(\emptyset)=0
$$

La probabilità dell'evento impossibile è uguale a 0.

_Dimostrazione - Utilizzando l’assioma 3_

Prendiamo la successione $E1​,E2​,E3​,...$ dove $E1​=∅,E2​=∅,E3​=∅,...,$ quindi abbiamo che $∀i \neq j$ l’intersezione $Ei​∩Ej​=∅$.

Per l’assioma 3 $P\left( \bigcup_{i=1}^{ \infty } E_{i} \right) = \sum_{i=1}^{ \infty }P(E_{i})$, quindi $P(\emptyset)\sum_{i=1}^{ \infty }​P(∅)$, per l’assioma 1 sappiamo che $P(∅)∈[0,1]$.

Supponiamo che $P(∅)∈(0,1]$ allora abbiamo che $\sum_{i_{1}}^{ \infty } ​P(∅)=+∞$ e quindi $P(\emptyset) \neq \sum_{i=1}^{\infty}P(\emptyset)$, per esclusione quindi $P(∅)=0$ altrimenti come appena visto otteniamo un valore infinito.

#### Proposizione 2

Prendiamo un esempio:

- Domani piove con una probabilità $0.3$
- Domani c’è il sole con una probabilità $0.6$
- Domani nevica con una probabilità $0.1$
- Qual è la probabilità che piova o che nevichi? $0.3 + 0.1 = 0.4$

**P soddisfa l’additività finita**: Dati n eventi a 2 a 2 _incompatibili_ $E1​,E2​,...,En​$ vale $P\left( \bigcup_{i=1}^{ n }E_{i} \right)=\sum_{i=1}^{ n } P(E_{i})$

*Dimostrazione*

coming soon


#### Proposizione 3

$$
\forall E \subset S \space vale \space P(E^{ c } ) = 1-P(E)
$$

*Dimostrazione*

Coming soon


#### Proposizione 4 - Monotonia della funzione di probabilità

Dati $E$ e $F$ eventi con $E \subset F$ allora vale $P(E)\leq P(F)$.

$F=E \cup (F\setminus E)$, quindi $E$ e $F \setminus E$ sono *disgiunti*.

Quindi, $P(F)=P(E)+P(F \setminus E )$ dato che per l’assioma 1$P(F \setminus E)≥0 allora P(E)+P(F \setminus E)≥P(E)$.


#### Proposizione 5

$\forall E, F$ eventi, allora $P(E \cup F) = P(E) + P(F)-P(E \cap F)$, questa formula generale non viene usata nel caso in cui $E,F$ sono distinguibili allora $P(E \cup F) = 0$.

---
### Spazi campionari con esiti equiprobabili

In molti esperimenti è naturale assumere che tutti gli esiti dello spazio campionario siano equiprobabili.
Prima di tutto lo spazio campionario $S$ dovrà essere in insieme finito. Poniamo $S=\{ 1,2,\dots,N \}$, allora sarà naturale ipotizzare che

$$
P(\{ 1 \})=P(\{ 2 \})=\dots=P(\{ n \})
$$

Per gli assiomi 1 e 2 possiamo dire che

$$
P(\{ i \})=\frac{1}{N} \ \ \ \ \ \ \ i=1,2,\dots ,N
$$

Per l'assioma 3 avremo perciò che per ogni evento $E$

$$
P(E)=\frac{\text{numero di elementi di }E}{\text{numero di elementi di }S}
$$

>[!info]
>Quindi, se assumiamo che tutti gli esiti di un esperimento siano equiprobabili, allora la probabilità di ogni evento $E$ è uguale alla proposizione degli esiti dello spazio campionario contenuti in $E$ (casi possibili su casi favorevoli)

##### Esempio

Se si lanciano due dadi, qual è la probabilità che la somma dei valori sulla faccia superiore sia uguale a 7?

**Svolgimento**
Assumiamo che tutti i 36 possibili esiti siano equiprobabili. Poiché ci sono 6 possibili esiti che danno come soluzione 7 $E=\{ (1,6),(2,5),(3,4),(4,3),(5,2),(6,1) \}$, la probabilità sarà:

$$
\frac{6}{36}=\frac{1}{6}
$$

##### Esempio

Ho un'urna con 6 palline bianche e 5 nere a caso senza rimpiazzo. Qual è la probabilità che esca una pallina bianca e 5 nere?

Non conviene registrare il colore delle due palline poiché *romperebbe la simmetria*. Conviene, invece, numerarle una per una in modo da distinguerle.

$$Urna = U=\{ B_{1},B_{2},B_{3},B_{4},B_{5},B_{6},N_{1},N_{2},N_{3},N_{4},N_{5} \}$$
Ci sono 11 palline distinguibili.

$$
S = \{ A \subset U:|A|=3 \}
$$

Un esempio è l'esito:

$$
\{ B_{2},B_{4},N_{3} \}
$$

Quindi adesso $S$ ha esiti equiprobabili per simmetria: $P(E)=\frac{|E|}{|S|}$ dove $|S|=\binom{ 11 }{ 3 }$.

$|E|=\{ A \subset U:|A|=3, A \text{ha una pallina bianca e 2 nere} \}$.

$|E|=6 \times \binom{ 5 }{ 2 }$ dove $6$ sono i modi per estrarre una pallina bianca e $\binom{ 5 }{ 2 }$ quelli per scegliere due palline senza considerare l'ordine. Quindi:

$$
P(E) = \frac{6 \times \binom{ 5 }{ 2 }}{\binom{ 11 }{ 3 } } = \frac{4}{11}
$$
---
### Principio di inclusione/esclusione

**Con 2 eventi**

$$
P(A \space \cup B)=P(A)+P(B)-P(A \space \cap \space B)
$$

**Con 3 eventi**

$$
P(A \space \cup \space B \space \cup \space C)=P(A)+P(B)+P(C)-P(A \space \cap \space B)-P(A \space \cap \space C)-
$$
$$
-P(B \space \cap \space C)+ P(A \space \cap \space B \space \cap \space C)
$$
---
### Probabilità condizionata

Dati $E$ e $F$ con $P(F)>0$, la probabilità di $E$ condizionata $F$ è definita come 
$$
$P(E|F)=\frac{P(E \space \cap \space F )}{P(F)}$
$$

Si svolge l’esperimento e so che “si verifica $F$”, questa informazione muta la speranza che si verifichi $E$ e la nuova probabilità di $E$ sapendo che si è verificato $F$ è data da $P(E∣F)$.

##### Esempio

Si lancia un dado.

$E = \text{Esce 1 o 2}, P(E)=\frac{2}{6}=\frac{1}{3}$

Supponiamo di sapere che si è verificato l'evento $F$ ($F=\text{Uscito un numero} \leq 4$), se so che $F$ si realizza allora so che è uscito o 1 o 2 o 3 o 4. Quindi ho 4 esiti possibili e c'è simmentria.

In questo modo se si verifica $F$ allora $P(E)=\frac{2}{4}=\frac{1}{2}$, ci aspettiamo che $P(E|F)=\frac{1}{2}$.

Calcolo usando la definizione:
$$
P(E|F)= \frac{P(E \space \cap \space F)}{P(F)}= \frac{\frac{2}{6}}{\frac{4}{6}}=\frac{1}{2}
$$
$$
S= \{ 1,2,\dots,6 \}
$$
$$
F=\{ 1,2,3,4 \}
$$

---
### ...

---
# Variabili aleatorie

### Variabili reali

Dato uno spazio di probabilità ($S, P$), una variabile aleatoria è una funzione $X:S\to R$ quindi una funzione che mappa elementi dello spazio campionario in numeri reali.

##### Esempio 1

Lancio una moneta due volte e abbiamo $X := \text{\#volte in cui esce testa, X}$  è una variabile aleatoria.

Abbiamo $S=\{ (T,T), (C,C),(T,C),(C,T) \}$ e sono tutti esiti equiparabili.

Quindi: 
$$X((T,T))=2, \space X((T,C))=1, \space, X((C,T))=1, \space, X((C,C))=0$$

##### Esempio 2

Lancio due volte un dado e abbiamo $X:=\text{\#somma dei numeri usciti}$.
Otterremo:
$$
S=\{ (a,b):a,b \in \{ 1,2,3,4,5,6 \} \}
$$

Quindi abbiamo esiti equiprobabili.
$$
X((a,b))=a+b \space
$$
Quindi per esempio
$$
X((1,5))=6
$$

### Variabili discrete

Una variabile aleatoria $X$ è detta *discreta* se i valori che può assumere $\{ X_{i} \}_{i \in I}$, formano un insieme finito o infinito numerabile. Quindi, per esempio, la variabile aleatoria degli esempio descritti precedentemente è discreta.

#### Densità di probabilità aleatoria discreta

Data $X$ variabile aleatoria che assume $\{ X_{i} \}_{i \in I}$, la *densità di probabilità discreta* di $X$ è la funzione:

$$
P_{X}: \{ X_{i} \}_{i \in I} \to [0,1], P_{X}:=(X=X_{i})
$$

E' quindi una funzione che descrive la probabilità associata a ciascun valore possibile di una variabile aleatoria discreta.

##### Esempio

Lancio due volte una moneta e v.a. $X :=\text { \#Teste uscite }$ quindi $X(T,T)=2,X(T,C)=1,X(C,C)=0$.

Quindi $X$ è una variabile aleatoria che assume i valori $0,1,2$.

$$
P_{X}:\{ 0,1,2 \}\to[0,1] \space e \space P_{X}(a)=P(X=a)
$$
Quindi calcoliamo:
$$
P_{X}(0)=P(X=0)=\frac{1}{4}
$$
E' il caso in cui escano due croci $(C,C)$ e ha probabilità $\frac{1}{4}$

Poi:

$$
P_{X}(1)=P(X=1)=\frac{2}{4}
$$

E' il caso in cui almeno una dei due sia testa $(T,C)\space oppure \space (C,T)$ e ha probabilità $\frac{2}{4}$

Infine calcolo:
$$
P_{X}(2)=P(X=2)=\frac{1}{4}
$$

E' il caso in cui entrambi sono testa $(T,T)$ e ha probabilità $\frac{1}{4}$.


Possiamo rappresentare la densità discreta con un istogramma.

![[Pasted image 20241102182238.png|500]]

#### Valore atteso

Data una variabile aleatoria discreta $X$ che assume valore $\{ X_{i} \}_{i\in I}$, definiamo il valore atteso di $X$ come:
$$
E[X] = \sum_{i \in I} X_{i}P(X=X_{i}) = \sum_{i \in I} X_{i}P_{X}(X_{i})
$$
Dove $E$ indica il *valore atteso di X*.

##### Esempio

Lanciamo una moneta 2 volte e come variabile aleatoria si ha $X=\text { \#Teste uscite}$.

$$
E[X]=0 \space\cdot \space \frac{1}{4} + \space 1 \space \cdot \frac{2}{4} + 2 \space \cdot \frac{1}{4} = 1 
$$

##### Esempio

Data un'urna con 3N e 2B. Estraggo due palline senza rimpiazzo, sia $X :=\text { \#Palline nere estratte }$.
Calcolare $E[X]$.

Abbiamo $X=\{ 0,1,2 \}$

- $P(X=0)=\frac{2\cdot 1}{5 \cdot 4} = \frac{2}{20}$
- $P(X=1)=\frac{3\cdot 2}{5 \cdot 4} + \frac{2\cdot 3}{5 \cdot 4} = \frac{2}{20}= \frac{12}{20}$
- $P(X=2)=\frac{3\cdot 2}{5 \cdot 4} = \frac{6}{20}$

$$
E[X]= 0 \cdot \frac{2}{20} + 1 \cdot \frac{12}{20} + 2 \cdot \frac{6}{20} = \frac{6}{5}
$$

#### Funzione di distribuzione (o ripartizione)

Data una variabile aleatoria $X$, la sua funzione di distribuzione è definita come:

$$
F_{X}:\mathbb{R} \to [0,1] \space con \space F_{X}(a)=P(X\leq a) \space\forall a \in \mathbb{R} 
$$
##### Esempio

Sia $X$ la stessa variabile aleatoria di prima (esempio urna) determiniamo $F_{X}$. 

- Se $a<0$ allora $F_{X}(a)=P(X\leq a)=0$
- Se $0 \leq a$ allora $F_{X}(a)=P(X\leq a)=\frac{1}{10}$
- Se $1 \leq a < 2$ allora $F_{X}(a)=P(X\leq a)=F_{X}(\{ X=1 \cup \{ X=0 \}\})=\frac{1}{10}+\frac{6}{10}=\frac{7}{10}$
- Se $a \geq 2$ allora $F_{X}(a)=P(X \leq a)=F_{X}(\{ X=0 \}\cup \{ X=1 \}\cup \{ X= \})=\frac{1}{10}+\frac{6}{10}+\frac{3}{10}=1$

Quindi guardando meglio la funzione abbiamo che:

$$
F_{X}(a)= \begin{cases}
0 \space se \space a \leq 0 \\
\frac{1}{10} \space se \space 0 \leq a \leq 1 \\
\frac{7}{10} \space se \space 1 \leq a \leq 2 \\
1 \space se \space a \geq 2
\end{cases}
$$

In generale se $X$ è una variabile aleatoria che assume $n$ valori dati da $X_{1}\leq X_{2}\leq \dots X_{n}$ allora si ha che:

$$
F_{X}(a)= \begin{cases}
0 \space se \space a \leq 0 \\
P(X_{1}) \space se \space X_{1} \leq a < X_{2} \\
P(X_{1})+P(X_{2}) \space se \space X_{2} \leq a < X_{3} \\
.  \\
P(X_{1})+P(X_{2})+\dots + P(X_{k}) \space se \space X_{k} \leq a < X_{k+1} \\ 
. \\
1 = P(X_{1})+\dots + P(X_{n}) \space se \space a \geq X_{n}\\
\end{cases}
$$

#### Varianza di una variabile aleatoria

Sia $X$ una variabile aleatoria discreta, la varianza di $X$ è definita come $Var(X):= E[(X-EX)^{ 2 }]$.
Dove $EX$ è il valore atteso.

La varianza è utile perché indica la dispersione della variabile aleatoria $X$ dal suo valore atteso (il risultato è in unità al quadrato).

>[!info]
>Con il termine *dispersione* si indica quanto i dati si allontanano dal valore centrale (valore atteso) e tra di loro.

##### Esempio

Sia $X$ una variabile aleatoria con $X(1)=\frac{1}{2}$ e $X(-1)=\frac{1}{2}$, abbiamo che:

$$
E[X]=EX=1 \cdot \frac{1}{2} + 1 \cdot \frac{1}{2}=0
$$

Quindi:

$$
Var(X)=E[(X-EX)^{ 2 } ] = E[(X-0)^{ 2 } ]= E[X^{ 2 }]=1
$$

#### Deviazione quadratica

Sia $X$ una variabile aleatoria, la deviazione quadratica standard in $X$ è data da $\sigma_{X}:=\sqrt{ Var(X) }$.

In altre parole, è una misura che indica quanto i dati sono  "sparpagliati" rispetto al valore atteso.

>[!warning] Qual è la differenza tra deviazione quadratica e varianza?
>Entrambe calcolano la stessa cosa. L'unico elemento che le distingue è l'unità di misura.
>Infatti, la varianza non è altro che la deviazione quadratica elevata al quadrato.

##### Esempio

Supponiamo di avere i seguenti voti di un gruppo di studenti in un test  $X=\{ 6,7,8,9,10 \}$.

Calcoliamo ill valore atteso:

$$
E[X]= \frac{6+7+8+9+10}{5}=8
$$

Ora calcoliamo la varianza:

1) Calcolo la distanza di ogni voto dalla media:
	- $6$ è a distanza $2$ dalla media $(8-6=2)$
	- $7$ è a distanza $1$ dalla media $(8-7=1)$
	- $8$ è a distanza $0$ dalla media $(8-8=0)$
	- $9$ è a distanza $1$ dalla media $(9-8=1)$
	- $10$ è a distanza $2$ dalla media $(10-8=2)$

2) Eleviamo al quadro:
$$
2^{ 2 }=4,\space 1^{ 2 }=1, \space 0^{ 2 }=0, \space 1^{ 2 }=1,\space 2^{ 2 }=4     
$$
3) Calcoliamo la media dei valori elevati al quadrato:
$$
Var(X) = \frac{4+1+0+1+4}{5}=2
$$
Ora calcoliamo la derivazione standard svolgendo la radice quadrata della varianza:
$$
\sigma_{X}=\sqrt{ 2 } \approx 1,41
$$
---
### Funzione aleatoria

Dati $(S,P)$ e $X: S\to \mathbb{R}$ , denoto con $f(X)$ la variabile aleatoria $f$ o $X$, avremo quindi che:
$$
 \underbrace{S \overset{X}{\to} \mathbb{R} \overset{f}{\to}\mathbb{R}}_{f \space o \space X =f(X)}
$$

- $f(X): S \to \mathbb{R}$ è una variabile aleatoria

Infatti:

- $X : S\to \mathbb{R}$ assume valori $\{ X_{i} : i \in I \}$
- $f(X) = f \space o X:S \to \mathbb{R}$ assume valori $\{ f(X_{i}) : i \in I \}$

##### Esempio

Lancio 10 volte una moneta $X = \text { \#Teste uscite }$. Si vince $€2$ per ogni testa e si perde €1 per ogni croce.

$Y= \text { \#Guadagno algebrico }$ 

Posso esprimere $Y$ come $f(X)$.

$$
Y = 2 \cdot X - 1 \cdot (10-X)=3X-10\space\space\space \space \space \space \space \space \space Y= f(X) \text { dove } f: \mathbb{R} \to \mathbb{R} 
$$
Ho $(S,P) \space e \space X:S\to R \text { variabile aleatoria }$

Ho $f:\mathbb{R}\to \mathbb{R}$, se $X$ è una variabile aleatoria discreta, allora $f \space o \space X=f(X)$ è variabile discreta aleatoria.

Calcolo $E[f(X)]$

**Primo metodo**

Determino i possibili valori di $f(X)$ che chiamo $\{ y_{j}:j \in J \}$ e calcolo $P(f(X)=y_{j}) \forall j \in J$.
Quindi per definizione:
$$
\sum_{j} y_{j}\space\cdot \space P(f(X)) = y_{j}
$$
**Secondo metodo**

*Teorema*

Sia $X$ una variabile aleatoria discreta che assume valori $\{ X_{i} \}_{i \in I}$ e sia $f:\mathbb{R}\to \mathbb{R}$.
Allora:
$$
E[f(X)]=\sum_{i \in I} f(X_{i}) \space \cdot \space P(X=X_{i}) = \sum_{i \in I} f(X_{i}) \space \cdot \space P_{X}(X_{i})
$$

##### Esempio

Data $X$ che assume valori $-1, 0, 3$ con probabilità $0.2, 0.5, 0.3$ rispettivamente. Calcolare $E((X-1)^{ 2 })$.

**Primo metodo**

$$
Y = (X-1)^{ 2 } \text { assume valori } \space 
\begin{cases}
4 \space se \space X = -1 \space o \space X = 3 \\
1 \space se \space X=0
\end{cases} 
$$

- $P(Y=4) =P(X=-1)+P(X=3)=0.2+0.3=0.5$
- $P(Y=1)=P(X=0)=0.5$
- $E[Y]=4 \cdot 0.5+1 \cdot 0.5=2.5$

**Secondo metodo**

$$
\begin{align}
E[Y] & = f(-1) \cdot P(X = -1)+f(0)+f(3)\cdot P(X=3)\\
& = (-1 -1)^{ 2 } \cdot 0.2 + (0-1)^{ 2 } + (3-1)^{ 2 } \cdot 0.3 \\
& = 0.8+0.5+1.2=2.5   
\end{align}
$$
---
### Valore atteso con funzione

Se $X$ è variabile discreta che assume i valori $\{ x_{i} \}_{i\in I}$ e $f:\mathbb{R}\to \mathbb{R}$ allora:
$$
E[f(X)]=\sum_{i\in I}f(x_{i})\cdot P(X=x_{i})
$$
$$\text { La chiamiamo * }$$
##### Esempio

$X$ assume valori $\{ -1,0,2,3 \}$ e abbiamo che:
- $P(-1)=0.1$
- $P(0)=0.2$
- $P(2)=0.2$
- $P(3)=0.5$

Allora:
$$
E[(X-1)^{ 4 } ]=E[f(X)] \space dove \space f(u)=(u-1)^{ 4 } 
$$

Calcoliamo:
$$
\begin{align} \\
E[(X-1)^{ 4 } ]&=E[f(X)]=f(-1) \cdot P(-1) + f(0) \cdot P(0)=+f(2)\cdot P(2)+f(3)\cdot P(3) \\
&=(-1-1)^{ 4 } \cdot 0.1 + (-1)^{ 4 } \cdot 0.2 + (2-1)^{ 4 }\cdot 0.2 + (3-1)^{ 4 }+(3-1)^{ 4 } \cdot 0.5  \\
&=2   
\end{align}
$$

**Linearità del valore atteso**

Sia $X$ una variabile aleatoria discreta e siano $a, b \in \mathbb{R}$ allora $E[aX+b]=aE[X]+b$

*Dimostrazione*

Sia $\{ x_{i} \}_{i\in I}$ l'insieme dei valori assunti da $X$, inoltre abbiamo $aX+b=f(X)$ dove $f(u)=au+b$. 
La scriviamo quindi come funzione di $X$.

$$
E[aX+b]=E[f(X)] = \sum_{i \in I}f(x_{i})P(X=x_{i})=\sum_{i \in I}(ax_{i}+b)P(X=x_{i})
$$
$$
\text { Proprietà distributiva }= \sum_{i}ax_{i}P(X_{i})+bP(X_{i})
$$
$$
\text { Portiamo fuori a,b e spezziamo }= a \underbrace{\sum_{i}P(x_{i})}_{E[X]} + b \underbrace{\sum P(x_{i})}_{1}= aE[X]+b 
$$

##### Esempio

$E[X]=1000$ come calcoliamo $E[3X-500]$?

Applichiamo la formula:

$$
E[3X-500]=3E[X]-500=3000 - 500 = 2500
$$

**Proposizione**

Ricordiamo che la varianza si calcola $Var(X):=E[(X-EX)^{ 2 }]$, possiamo anche calcolarla come:
$$
Var(X)=E[X^{ 2 } ]-(EX)^{ 2 } 
$$
---
>[!warning] Reminder
>La deviazione quadratica standard è:
>$$
>\sqrt{ Var(x) }
>$$

Osserviamo che $Var(X)$ deve essere sempre $\geq 0$ infatti $Var(X)=E[(X-EX)^{ 2 }]$ è $\geq 0$, dato che è elevato al quadrato.

$$
Var(X)=0 \iff P(X=EX)=1
$$

Se la varianza è uguale a 0 allora significa che la variabile è costante, infatti $Var(X)$ misura quanto $X$ si sposta dal suo valore atteso $E[X]$.

>[!info] Osservazione 
>![[Pasted image 20241110184736.png|70]] 
>Né la varianza né la deviazione quadratica sono lineari

**Proprietà**

Data $X$ variabile discreta e dati $a,b \in \mathbb{R}$ vale:
$$
Var(aX+b)=a^{ 2 }Var(X) 
$$
E quindi si può notare che amplifica le costanti moltiplicative e annulla quelle additive.

---

### Variabile di Bernoulli

Una variabile aleatoria è  detta di Bernoulli se di parametro $p \in [0,1]$ se $P(X=1)=p$ e $P(X=0)=1-p$, quindi questa può assumere soltanto due valori.

Quindi in questo caso notiamo che:
$$
E[X]=1 \cdot P(X=1)+0 \cdot P(X=0)=1 \cdot p + 0 \cdot(1-p)=p
$$
Mentre
$$
Var(X)=E[X^{ 2 } ]-(EX)^{ 2 }=p-p^{ 2 }=p \cdot (1-p)  
$$
Dove
$E[X^{ 2 }]=1^{ 2 } \cdot P(X=1)+0^{ 2 }\cdot P(X=0)=p$

---

### Variabile aleatoria binomiale

Dato un esperimento con $n$ prove indipendenti, tutte svolte nello stesso modo.
Supponiamo che ogni prova abbia due possibili esiti: *successo* e *insuccesso*.

*Esempio 1*

Lancio una moneta 10 volte, i 10 lanci solo le prove e come successo stabilisco che deve uscire testa.

*Esempio 2*

Lancio un 8 volte, gli 8 lanci sono le prove e come successo stabilisco quando esce un numero multiplo di 3.

Definiamo $X=\text{\#Successi ottenuti}$ nelle prove, notiamo quindi che può assumere come valore, tutti i valori interi da 0 a n, ma con che probabilità?

Chiamiamo p la probabilità che una singola prova ci dia successo come esito.

**Proposizione**

$$
\forall k=0.1,2,\dots,n \space vale \space P(X=k) = \binom{ n }{k  }\cdot p^{ k } \cdot (1-p)^{ n-k }   
$$

Prendiamo l'esempio 2, quindi abbiamo $n=8$, $p=\frac{1}{3}$ e calcoliamo la probabilità di due successi:
$$
P(X=2)=\binom{ 8 }{ 2 }\cdot \left( \frac{1}{2} \right)^{ 2 } \cdot \left( \frac{2}{3} \right)^{ 6 }   
$$

*Perché vale questa proposizione?*

Supponiamo di avere 4 prove e ci chiediamo $P(X=2)$, questo evento $\{ X=2 \}$ possiamo vederlo come unione di varie prove:

$$
E_{SSII}\space \cup \space E_{SISI} \space \cup \space E_{ISSI} \space \cup \space E_{IISS} \space \cup \space E_{ISIS}
$$

Dove i pedici sono successi e insuccessi.

Abbiamo $\binom{ 4 }{ 2 }$ eventi, in generale $\binom{ n }{ k }$.

Adesso se calcoliamo la probabilità di tutti questi eventi:
$$
\begin{align}
P(X=2)&=P(E_{SSII})+\dots+P(E_{ISIS}) \\
& = p \cdot p \cdot (1-p) \cdot (1-p))+\dots+((1-p)\cdot p\cdot p\cdot(1-p))
\end{align}
$$

Hanno tutti la stessa probabilità che è data da $p^{ 2 }\cdot(1-p)^{ 2 }$ quindi è uguale a:

$$
\binom{ 4 }{ 2 } \cdot p^{ 2 } \cdot (1-p)^{ 2 }   
$$

Ovviamente abbiamo $p=2$ e quindi $n-k=2$ ma dipende da quanti esiti con successo abbiamo. *Quindi vale la proposizione*.

**Definizione**

Una variabile aleatoria binomiale di parametri $n \in \{ 1,2,3,\dots \}$ e $p \in [0,1]$ è una variabile aleatoria che assume valori $0,1,2,\dots,n$ con la stessa probabilità:
$$
P(X=k)=\binom{ n }{ k } \cdot p^{ k }\cdot (1-p)^{ k } \space \forall k \in \{ 0,1,2,\dots,n \}   
$$
**Teorema**

Indichiamo con $X=Bin(n,p)$ una variabile binomiale di parametri $n,p$.

Sia $X=Bin(n,p)$ allora:
$$
E[X]=n \cdot p \space e \space Var(X)=n \cdot p \cdot (1-p)
$$
Se $n=1$ e $X=Bin(n,p)$ ho che $X$ assume i valori $0,1$ e:
$$
P(X=1)=\binom{ n }{ 1 } \cdot p ^{ 1 }\cdot (1-p)^{ n-1 }=\binom{ 1 }{ 1 }\cdot p^{ 1 }\cdot(1-p)^{ 0 }=p      
$$
Mentre
$$
P(X=0)=1-p
$$
Quindi si può notare che $Bin(1,0)=Bernoulli(p)$, cioè una variabile aleatoria di Bernoulli di parametro $p$.

##### Esempio

Lancio 5 volte una moneta onesta. Sia $X=\text { \#Teste uscite }$ determinare la probabilità discreta $X, EX, Var(X), \sigma(X_{0})$

$X=Bin(\frac{5}{1})$ ovvero 5 prove e il successo è che esce testa.

Calcoliamo $P_{X}$, sappiamo che $X$ assume $0,1,2,3,4,5$ ovvero le possibili teste quindi per questi valori $k$ calcoliamo:

![[WhatsApp Image 2024-11-11 at 12.51.20_6224f911.jpg|500]]

Poi abbiamo che:

![[WhatsApp Image 2024-11-11 at 12.51.20_ca374040.jpg|500]]

---

*Perché le costanti additive non importano nella varianza?*

Prendiamo come esempio due grafici di due probabilità:

![[WhatsApp Image 2024-11-11 at 12.51.21_a3e43a1f.jpg|400]]

Notiamo che se trasliamo la probabilità di una costante, i grafici rimangono uguali ma vengono traslati, la varianza quindi rimane la stessa, dato che misura la dispersione dal valore atteso.

Quindi $Var(X)\text{ e }Var(X+b)$ coincidono.

---

### Variabile aleatoria di Poisson (distribuzione degli eventi rari)

Una variabile aleatoria $X$ è detta di Poisson di parametro $\lambda >0$ se assume valori $0,1,2,\dots$ (valori interi) e:
$$
P_{X}(k)=P(X=k)=e^{ -\lambda } \cdot \frac{\lambda^{ k } }{k!} \space \forall k = 0,1,2,\dots
$$

Per verificare l’esistenza della variabile aleatoria di Poisson di parametro $k$ devo verificare:
$$
\begin{cases}
P_{X}(k)\geq 0 \space \forall k =0,1,2,\dots \\
\\
\sum \limits_{k=0}^{ \infty } P_{X}(k)=1
\end{cases}
$$
Infatti:
$$
\sum_{k=0}^{ \infty } P_{X}(k)=\sum_{k=0}^{ \infty }e^{ -\lambda } \cdot \frac{\lambda^{ k } }{k!}=e^{ -\lambda } \cdot \underbrace{\sum_{k=0}^{ \infty } \frac{\lambda^{ k } }{k!}U}_{Serie \space Esponenziale} = e^{ -\lambda }\cdot e^{ \lambda }=1  
$$

La variabile aleatoria di Poisson è un'approssimazione della variabile aleatoria binomiale $Bin(n,p)$ quando $n$ è molto grande e $p$ molto piccola.

**Teorema: legge dei piccoli numeri**

Dato $n \in \{ 1,2,\dots \}$ sia $P_{n}\in[0,1]$ tale che:

$$
\exists \lim_{ n \to \infty }P(X_{n}=k)=P(Z=k) \space \forall k \in \{ 0,1,2,\dots \}
$$
Quindi per $n$ grande possiamo approssimare $P(X_{n}=k) \approx P(Z=K)$, quindi in alcune situazioni abbiamo che:

$$
Bin(n,p) \approx Poisson(\lambda)
$$

Dove presi $n,p,\lambda$ abbiamo che:
$$
n\gg 1 (molto \space grande)
$$
$$
np \approx \lambda \space \text { quindi anche } p \approx \frac{\lambda}{n}
$$

Cosa intendiamo per $Bin(n,p) \approx Poisson(\lambda)?$

Intendiamo che:
$$
P(X=k) \approx P(Z=k) \space \forall k=0,1,2,\dots
$$

Dove $X=Bin(n,p)$ e $Z=Poisson(\lambda)$


*Esempio di grandezza ben modellizzata da una variabile aleatoria di Poisson*

Supponiamo di avere la pagina di un libro e consideriamo la probabilità che un carattere venga stampato in modo errato. 
Si ha una variabile aleatoria binomiale infatti un numero di prove n e due esiti, successo se stampato male e insuccesso altrimenti.

Notiamo che n è il numero di caratteri ed è molto alto all’interno di una pagina, e p possiamo assumerla piccola.

Possiamo quindi assumere $Bin(n,p) \approx Poisson(\lambda)$ dove $\space \lambda=n⋅p$.


*Esempio più concreto*

Supponiamo che il numero di errori tipografici per pagina sia approssimato da $Poiss\left( \frac{2}{1} \right)$:

- Qual è la probabilità che ci sia almeno un errore a pagina 20?

Consideriamo quindi $z := \text { \#Errori a pagina 20 }$ e quindi abbiamo che:
$$
z=Poiss(\lambda) \space \space \space \space \space \space \lambda=\frac{1}{2}
$$

$$
P(z=k)=e^{ -\frac{1}{2} } \cdot \left( \frac{1}{2} \right)^{ k } \cdot \frac{1}{k!} 
$$

Possiamo considerare il fatto che ci sia almeno un errore come l’evento complementare di non ci sono errori, quindi possiamo calcolare:

$$
P(z \geq 1)= 1 - P(z = 0)= 1 - e^{ - \frac{1}{2} } ​\cdot \left( \frac{1}{2} \right)^{ 0 } \cdot \frac{1}{0!}=1−e^{ -\frac{1}{2} } \approx 0.393
$$

- Qual è la probabilità che ci siano esattamente 4 errori?

$$
P(z =4)= 1 - e^{ - \frac{1}{2} } ​\cdot \left( \frac{1}{2} \right)^{ 4 } \cdot \frac{1}{4!}=1−e^{ -\frac{1}{2} } \approx 0.00158
$$

>[!info] Osservazione
>![[Pasted image 20241111143543.png|95]]
>La Poisson approssima una binomiale $Poiss(\lambda) \approx Bin(n,n\lambda​)$ per un n abbastanza grande.


**Teorema: valore atteso e varianza di Poisson**

Se $X=Poiss(\lambda)$ allora $E[X]=\lambda$ e anche $Var(X)=\lambda$

---

### Variabile aleatoria geometrica

Immaginiamo di ripetere in maniera indipendente una prova (lancio un dado$\space \infty \space$volte). Ogni prova ha successo con probabilità $p$ e insuccesso con $1-p$.

Sia $X$ il numero di prove necessarie per ottenere il primo successo.

Quindi:

$$
P(X=k)=\underbrace{(1-p)}_{\text { Prova 1, ins }} \cdot \underbrace{(1-p)}_{\text { Prova 2 ins. }} \to \text{Ultima prova, successo}
$$

Quindi abbiamo:
$$
P(X=k)=(1-p)^{ k-1 } \cdot p \space \space \space \space \space \space \forall k = 1,2,\dots
$$

Teoricamente si potrebbe sempre ottenere un insuccesso e quindi avere che $X=+ \infty$ e quindi si avrebbe che:

$$
P(X=+ \infty)=(1-p)^{ \infty }=0 \space \space \space \space \space \text { con } 0<p<1 
$$

Questo significa che l’evento è possibile ma ha una probabilità nulla.
Questa situazione strana è data dal fatto che l’insieme degli esiti è un insieme non numerabile.

Oppure possiamo dimostrare che questo risultato è 0 svolgendo:
$$
P(X=\infty) = 1 - P(Z< \infty) = 1 - 1 =0
$$
Dove
$$
P(X<\infty) = \sum_{k=0}^{ \infty } P(X=k)=\sum_{k=0}^{ \infty } (1-p)^{ k } \cdot p = p \underbrace{\sum_{k=0}^{ \infty } (1-p)^{ k } }_{\text { Serie Geometrica }}= p \cdot \frac{1}{1-(1-p)}=1   
$$
Infine, possiamo dire che in una variabile aleatoria geometrica:

$$
EX=\frac{1}{p} \space  \space \space \space \space \space \space \space \space Var(X=\frac{1-p}{p^{ 2 } })
$$

##### Esercizio

Si lancia un dado finché non esce 6.
	a) Calcolare il valore atteso del numero di lanci effettuati
	b) Calcolare la probabilità di aver effettuato almeno 7 lanci


a) 
$$ 
\begin{align}
&P(\text { Esce 6 })= \frac{1}{6} = p \\
&X=\text { Lanci effettuati fino al primo 6 }= Geom\left( \frac{1}{6} \right) \\
&E[X]= \frac{ 1 }{ \frac{1}{6} }=\frac{ 1 }{ \frac{1}{6} }=6   \\
\end{align}
$$


b) Abbiamo $p=\frac{1}{6}$ come prima e anche la variabile aleatoria $X$. Adesso però dobbiamo calcolare $P(X=7)$

$$
P(X= 7)=p^{ k-1 }=\left( \frac{5}{6} \right)^{ 6 } 
$$
---
### Variabile aleatoria binomiale negativa

Dipende da due parametri, $p \in (0,1)$ che è la probabilità di successo in una prova e $r \in \{ 1,2,3,\dots \}$ intero che indica il numero di successi che voglio ottenere.

##### Esempio chiave

Considero una successione di prove indipendenti di tipo successo/insuccesso.

$$
X := \text { \# Prove effettuate fino ad avere r successi per la prima volta }
$$
Allora $X= Bin\_Neg(p,r),X$ assume valori $r,r+1,r+2,\dots$ quando dato $k \in \{ r,r+1,r+2,\dots \}$ come calcoliamo $P(X=k)$?

Sappiamo che sicuramente la $k$-esima prova deve avere come esito successo, mentre nella $k-1$ prove dobbiamo avere sicuramente $r-1$ successi.

Non tenendo conto dell'ordine, possiamo dire che:

$$
P(X=K)=P(\text { Ho } r-1 \text { successi nelle prime }k-1 \text { prove}) \cdot p
$$

A questo punto, possiamo utilizzare la binomiale per calcolare la probabilità degli $r-1$ successi:

$$
\binom{ k-1 }{ r-1 } \cdot p^{ r-1 } \cdot (1-p)^{ (k-1)-(r-1) }=\binom{ k-1 }{ r-1 } \cdot p^{ r } \cdot (1-p)^{ k-r }  
$$
---

### Variabile aleatoria ipergeometrica

**Prototipo**

Abbiamo un'urna con $N$ palline di cui $m$ bianche e $N-m$ nere, estraggo senza rimpiazzo $n$ palline con $n \leq N$.

Definiamo $X := \text { \#Numero palline bianche estratte }$

$X$ è detta *variabile aleatoria di parametri* $N,m,n$.

Come si calcola $P(X=k)$? Numeriamo tutte le palline per distinguerle, nello spazio campionario abbiamo: $\binom{ N }{ m }$ modi per scegliere $n$ palline. Usiamo il principio fondamentale della combinatoria:
$$
P(X=k)= \frac{\binom{ n }{ k } \cdot \binom{ N-m }{ n-k } }{\binom{ N }{ n } }
$$
Quindi al numeratore abbiamo i modi per scegliere le bianche per i modi per scegliere le nere.

Per quali $k$ abbiamo che $P(X=k)>0$?

$$
P(X=k)\iff \binom{ m }{ k } > 0 \iff 0 \leq n-k \leq N-m 
$$

Ricordiamo che per i binomiali $\binom{ b }{ a }$ deve valere $0\leq a\leq b$ altrimenti è $0$.

Quindi abbiamo:
$$
\begin{cases}
0 \leq k \leq m \\
0\leq n-k \leq N-m
\end{cases}
$$
Ovvero 4 disuguaglianze:
$$
\begin{cases}
0\leq k \\
k \leq m \\
k\leq n \\
n+m-N\leq k
\end{cases}
$$
Scritto in un'unica disuguaglianza:
$$
max(0,n+m-N)\leq k \leq min(m,n)
$$

>[!info] Definizione
>Una variabile aleatoria ipergeometrica di parametri $N,m,n$ è una variabile aleatoria discreta con densità di probabilità come il prototipo visto per l’esercizio sopra, cioè:
>$$
>P(X=k)= \frac{\binom{ n }{ k } \cdot \binom{ N-m }{ n-k } }{\binom{ N }{ n } }
>$$

Inoltre abbiamo che:
$$
E[X]=\frac{n\cdot m}{N} \space \space \space \space \space \space \space Var(X)=np(1-p)\left( 1- \frac{ n-1 }{ N-1 }  \right) \space \space \space \space \space \space \space \space \text { dove } p =\frac{m}{n}
$$
---

