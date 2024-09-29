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

##### "Dimostrazione"

Per ordinare gli $n$ oggetti scelgo il primo (ho $n$ modi possibili) scelgo il secondo (ho $n-1$ modi possibili), $\dots$ , scelgo l'n-esimo.

**Principio fondamentale**
$$
\#permutazioni=n\times(n-1)\times(n-2)\times\dots 
$$
### Permutazioni senza ripetizioni

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

