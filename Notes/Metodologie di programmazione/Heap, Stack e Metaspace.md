### Anatomia della memoria

Esistono due tipi di memoria:
- **heap**
- **stack**

Gli oggetti vengono gestiti dinamicamente e la gestione dinamica consiste nell'allocare gli oggetti nella heap.

Il compilatore mette nello stack delle strutture dati dove le variabile locali dei metodi saranno scritte nei frame.

Quindi la gestione dello stack viene prestabilita compilando il codice, la 
gestione della heap è una questione dinamica.

### La parola chiave static

Un campo static esiste in una sola locazione di memoria, allocata prima di qualsiasi oggetto della classe in una zione speciale di memoria nativa chiamata **MetaSpace**.

E' condiviso da tutte le sue istanze e quindi è relativo all'intera classe.

Per ogni campo non statico esiste una locazione di memoria per ogni oggetto, allocata a seguito dell'istruzione `new`

#### Esempio classe Tornello

```java
public class Tornello
{
	static private int passaggi;

	public void passa() {passaggi++;}

	public static int getPassaggi() {return passaggi;}

	public static void main (String[] args)
	{
		Tornello t1 = new Tornello();
		t1.passa();
		Tornello t2 = new Tornello();
		for (int k = 0; k < 10; k++) t2.passa();
		int g; 
		String s = null;
	}
}
```

### Heap, stack e metaspace

- Nello **stack** si rappresentano i frame di attivazione (chiamate ai metodi) e le variabili locali
- Nella **heap** si rappresenta l'allocazione degli oggetti
- Nel **metaspace** si rappresenta l'allocazione dei campi

[[Drawing 2024-08-09 17.53.18.excalidraw]]

![[Pasted image 20240811171052.png|500]]

Quando compilo il codice la `JVM` usa un modulo chiamato **class loader** che controlla innanzitutto la presenza del metodo `main`.

Quindi controlla se ci sono campi statici. Nell'esempio tornello c'è un campo statico (`static private int passaggi;`).

Quindi passaggi verrà allocato nel **metaspace**

![[Pasted image 20240811171108.png|500]]

Dopo aver controllato tutti i campi statici, la `JVM` passa al metodo `main`.

Il main è un metodo che ha sempre un vettore di stringhe.

Se ci sono degli argomenti, viene costruito un vettore i cui elementi sono le stringhe che sono passate come argomento di programma.

Se non ci sono stringhe, il vettore sarà vuoto. 

La `JVM` crea il frame di attivazione del metodo `main`.

![[Pasted image 20240811171203.png|500]]

Ogni volta che viene chiamato un metodo, tutte le variabili locali che corrispondono ai parametri attuali, vengono copiati.

Tutto ciò che viene passato come metodo viene copiato e allocato nello stack, quindi `args` diventa una variabile

![[Pasted image 20240811171251.png|500]]

Ora siamo nella riga 

```java
Tornello t1 = new Tornello();
```

Viene chiamato il costruttore di default e viene allocato nello stack

![[Pasted image 20240811171830.png|500]]

E' una dichiarazione di `t1` di tipo Tornello.

Costruisce l'oggetto e lo alloca nella heap.

![[Pasted image 20240811171510.png|500]]

Ora ho la chiamata del metodo `passa()` a partire dal riferimento `t1`.

```java
t1.passa();
```

Avremo quindi un nuovo frame che si posizionerà sopra il `main`.

![[Pasted image 20240811171606.png|500]]

La `JVM` crea un'altra area di memoria per rappresentare ciò che deve fare nell'eseguire il metodo `passa()`.

Nel passaggio successivo `t1.passa()` viene distrutto e al suo posso viene scritto il frame `Tornello()`

```java
Tornello t2 = new t2 = new Tornello();
```

![[Pasted image 20240811171635.png|500]]

Stiamo chiamando un metodo, quello di costruzione del tornello, il costruttore di default.

Quando chiamo il costruttore la `JVM` inizia ad allocare il progetto, controlla se ci sono campi e istruzioni e alloca il progetto nella heap.

![[Pasted image 20240811171858.png|500]]

```java
Tornello t2 = new Tornello();
```

Viene allocato `t2` che è una variabile locale.

![[Pasted image 20240811172240.png|500]]

```java
for (int k = 0; k < 10; k++) t2.passa();
```

Con quest'istruzione intendiamo chiamare passa a partire dall'oggetto `t2`.

`k = 0` diventa **temporaneamente** una variabile locale di tipo intero.

Viene allocata nel frame `main`

![[Pasted image 20240811172846.png|500]]

Viene richiamato il metodo `passa()`.

![[Pasted image 20240811173128.png|500]]

Il frame `t2.passa()` viene distrutto

![[Pasted image 20240811173246.png|500]]

K diventa 1 e richiamo di nuovo `passa()`

![[Pasted image 20240811173427.png|500]]

Continuo a chiamare `passa()` finché `k>=10` 

![[Pasted image 20240811173533.png|500]]

K sparisce dal frame alla fine del ciclo for

![[Pasted image 20240811173749.png|500]]

```java
int g;
```

viene creata una variabile primitiva `g` che avrà come valore `undef`.

![[Pasted image 20240811174055.png|500]]

```java
String s = null;
```

Viene creata una variabile locale `s` di tipo `String` che ha come valore `null`.

![[Pasted image 20240811174420.png|500]]+

