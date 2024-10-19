# Prima lezione

### Tipi di dato di base (o primitivi)

###### I tipi di dati sono built-in
- Sono predefiniti nel linguaggio

###### Un tipo di dati è un insieme di valori e di operazioni definite su tali valori
- Intero
- Reali
- Booleani
- Caratteri
- Stringa (anche se non è propriamente primitivo)

>[!info] Notazione operazioni booleane
>- and ->&&
>- or -> ||
>- not ->!

```java
// Esempio operatori booleani

A && B
A || B
A ! B
```

### Tipi di built-in

- Int (dim 4 byte)
- Double (dim 8 byte)
- Long (dim 8 byte)
- Float (dim 4 byte)
- Boolean (dim 1 byte)
- Char (dim 2 byte)
- Short (dim 2 byte)
- Byte (dim 1 byte)

### Variabili, dichiarazioni e assegnazioni

###### Una variabile è un nome usato per riferirsi a un valore di un tipo di dati
- Una variabile è creata mediante dichiarazione
```java
int contatore;
```
- Il valore viene assegnato a una variabile mediante un'assegnazione
```java
contatore=0
```
- Un'istruzione può includere una dichiarazione e un'assegnazione allo stesso tempo
```java
int contatore=0
```

>[!warning] Rispetto a python
>- In java siamo costretti a specificare il tipo della variabile
>- Questo tipo non può più cambiare (è statico)
>	- Tuttavia esistono alcuni elementi di dinamicità

>[!warning] 
>- Non posso utilizzare una variabile senza prima dichiararla
>		NO: `a = "stringa"`;,SI: `String a = "stringa";` 
>- Non posso assegnare a una variabile tipi incompatibili tra loro
>		NO: `int a = "stringa";`
>		NO: `String a = 50;`
>		SI: `String a = "stringa";`

### Variabili e identificatori

###### Il nome assegnato a una variabile è detto identificatore, ovvero una sequenza di lettere, cifre, _ e $ la prima delle quali non è una cifra

- Gli identificatori sono case-sensitive non possono essere utilizzate alcune parole riservate (es. public, static, int, double, ecc.) si utilizza la notazione a cammello (Camel case)
	- Camel case: una variabile ha la prima parola con la prima lettera minuscola e la seconda parola ha la lettera maiuscola (ex. `unaVariabile`, `myInteger`)
- Le variabili devono avere un nome sensato

### Assegnazione e inizializzazione

###### Ci troviamo all'interno di un metodo per esempio:

```java
// esempio

int a, b;
a = 5;
b = a+10;
int c = a+b;
a = a-b;
```

### Letterali

###### E' una rappresentazione a livello do codice sorgente del valore di un tipi di dati
- 27 o -32 sono letterali per gli interi
-  3.14 è un letterale per i double
- true o false sono gli unici due letterali per il tipo booleano
- “Ciao, mondo” è un letterale per il tipo String

### Distinguere tra costanti intere e in virgola mobile

###### Interi
- Le costanti di tipo int sono semplicemente numeri interi nell'intervallo
- [-2, +2] miliardi circa
- Le costanti di tipo long vengono specificate con il suffisso l o L (ex. 10000000000000000L)

###### Numeri in virgola mobile
- Le costanti di tipo double sono semplicemente numeri con la virgola (punto)
- Le costanti di tipo float hanno il suffisso f o F (ex. 10.5F)

>[!info]
>- In tutti i casi si può utilizzare il trattino basso _ per separare le cifre (ex. 100_000 per indicare 1000000, 1_234 per indicare 1234)
>- Si può ottenere un intero da una rappresentazione binaria anteponento 0b alla stringa binaria (ex. 0b101 vale 5))

### Espressioni
###### Un'espressione è un letterale, una variabile o una sequenza di operazioni du letterali e/o variabili che producono un valore

![[Screenshot 2024-02-28 093749.png| 300]]

### Assegnazione di un'espressione alla variabile

###### Supponiamo di voler effettuare l’assegnazione:
```java
c = a*2+b
```

1. Calcola il valore dell’espressione destra (5\*2+15)
2. Assegna il valore (25) alla variabile di destinazione (c)

### Precedenza operatori 

1. Moltiplicazione, divisione, resto
2. Addizione, sottrazione

### Caratteri e stringhe
###### Char
- E' un carattere alfanumerico o un simbolo
- Ci sono 216 possibili valori di caratteri (più eventuali “caratteri supplementari”, per esempio per il cinese)
- Codifica Unicode basata su interi a 16 bit
- Racchiusi da apici (es. ‘a’, ‘b’, ‘0’, ‘1’, ecc.)
- Caratteri di escape
	- Tab -> `\t`
	- A capo: `\n`
	- Backslash: `\\`
	- Apice: `\'
	- Virgolette: `\"`
###### Stringhe
- E' una sequenza di caratteri

### Operatori booleani
- Ha solo due valori possibili: `true` (vero) e `false` (falso)
- Gli operatori disponibili sono ``&&`` (and), `||` (or) e `!` (not)

### Operatori di confronto 
###### Definiti sui tipi numerici primitivi
- Producono un valore booleano

> [!info] Operatori di confronto
> - Uguaglianza -> ==
> - Diversità -> !=
> - Minore -> <
> - Maggiore -> >
> - Minore uguale -> <=
> - Maggiore uguale -> >=

### Operatori

![[Pasted image 20240228095400.png|500]]

###### Post-incremento e post-decremento
```java
int a;
a = 3;
int c = a++;
//a vale 4 e c vale 3
```

###### Pre-incremento e pre-decremento
```java
int a;
a = 3;
int c = ++a;
//a vale 4 e c vale 4
```


### Print() in Java

###### HelloWorld.java
```java
public class HelloWorld //dichirazione di una classe
{
	public static void main (String [] args) 
	//main è il nome del metodo, String [] args sono gli argomenti
	{
		System.out.print("Hello, World!");
		System.out.println();
	}
}
```

- Public, class, static, void sono parole chiave
- Il metodo Java risiede in un file che ha lo stesso nome della classe creata (HelloWorld) più l'estensione .java (HelloWorld.java)

### Ricevere un input in fase di esecuzione e generare un output

```Java
public class BotSempliceSemplice 
{
	public static void main (String[] args)
	{
		System.out.print("Ciao");
		System.out.print(args[0]); // args[0] è la prima parola in input
		System.out.print(". Come va?");
	}
}
```

- Compila: javac BotSempliceSemplice.java
-  Esegui: java BotSempliceSemplice Pippo
- Output: Ciao, Pippo. Come va?

##### Abbiamo implementato un programma che prende in input una stringa e ne restituisce in output un'altra

![[Screenshot 2024-02-28 114712.png|500]]

### Regole di stile nella scrittura del codice

###### Posso scrivere così?
```Java
public                       class
				HelloWorldAnarchico{
			public static void main (String [] args) 
	{
						System.out.print("Hello, World!");
			System.out.println();
	}
}
```

###### No: il codice è scritto per essere riletto e riusato da altri (e da noi stessi) dopo qualche settimana, mese, anno...

