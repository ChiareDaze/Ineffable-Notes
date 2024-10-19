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

