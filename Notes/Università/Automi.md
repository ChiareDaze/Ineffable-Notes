>[!info] Argomenti
>- Teoria degli automi
>	- Il primo passo per capire modelli semplici di computazione
>- Computabilità
>	- Modello da calcolo molto più potente (*macchina di Turing*)
>- Complessità
>	- Quantificare le risorse in termini di spazio e tempo

### Linguaggi regolari

>[!Info] Alfabeto
>Definiamo come alfabeto un insieme finito di elementi detto **simboli**

L'insieme $\Sigma = \{ 0,1,x,y,z \}$ è un alfabeto

>[!info] Stringa o Parola
>Data una sequenza di simboli $w_{1},\dots,w_{n} \in \Sigma$, definiamo:
>$$
>w:=w_{1},\dots,w_{n}
>$$
>come **stringa** (o parola) di $\Sigma$

Dato l'alfabeto $\Sigma = \{ 0,1,x,y,z \}$, una stringa di $\Sigma$ è $0x1yyy0$

>[!info] Linguaggio
>Dato un alfabeto $\Sigma$, definiamo come **linguaggio** di $\Sigma$, indicato con $\Sigma^{ * }$, l'insieme delle stringhe di $\Sigma$

>[!info] Lunghezza di una stringa
>Data una stringa $w \in \Sigma^{ x }$, definiamo la **lunghezza di** $w$, indicata come $|w|$, come il numero di simboli presenti in $w$

>[!info] Concatenazione
>Data la stringa $x:=x_{1},\dots,x_{n} \in \Sigma^{ x }$ e la stringa $y_{1},\dots,y_{n} \in \Sigma$, definiamo come **concatenazione di** $x$ **in** $y$ la seguente operazione:
>$$
>xy=x_{1} \dots x_{n}y_{1} \dots y_{n}
>$$

>[!info] Conteggio
>Data una stringa $w \in \Sigma^{ * }$ e un simbolo $a \in \Sigma$ definiamo il **conteggio di** $a$ **in** $w$, indicato come $|w|_{a}$, il numero di simboli uguali ad $a$ presenti in $w$

Data la stringa $w:=010101000 \in \{ 0,1 \}^{ * }$, si ha che $|w|_{0}=6$ e $|w|_{1}=3$

>

**Automi a stati finiti DFA**
Ha una quantità di memoria limitata e processa in modo semplice i dati.
Processa input bit a bit in modo sequenziale.

*Esempio*
...

Astraendo, un *DFA* sarà fatto nel seguente modo:

- $q_{1}, q_{2}, q_{3}$ sono *stati*
- $q_{2}$ è lo stato di *accettazione*
- Gli archi sono le *transizioni*

>[!info] Definizione DFA
>Un DFA è una tupla:
>$$
>( Q, \sum, \delta,q_{0},F )
>$$
>Dove:
>- Q è un numero finito degli stati
>- Sigma è un numero finito dei simboli


>[!info] Teorema dell'unione
>