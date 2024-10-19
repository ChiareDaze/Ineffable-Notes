```java
public class HelloWorld
{
	public class static void main(Strings[] args)
	{
		System.out.print("Hello world!");
		System.out.println();
	}
}
```

**public**, **static**, **class** e **void** sono parole chiave.

Il programma (meglio: la classe) Java risiede in un file che ha lo stesso nome della classe creata (`HelloWorld`) più l'esetensione `.java` (`HelloWorld.java`)

La classe contiene un metodo che si chiama **main**.

`(Strings [] args)` definisce gli argomenti del metodo.

Il corpo di una classe di un metodo sono delimitati da {}


### Come convertire un tipo di dati

#### Conversione esplicita

Utilizza un metodo che prende in ingresso un argomento di in tipo e restituisce un valore do un altro tipo

```java
Integer.parseInt();
Double.parseDouble();
Math.round();
```

#### Cast esplicito

Anteponendo il tipo desiderato tra parentesi
```java
(int) 2.718
```

Se il valore di partenza è più preciso, le informazioni aggiuntive vengono eliminate nel modo più ragionevole.

#### Cast implicito

Se il tipo di partenza è meno preciso, Java converte automaticamente il valore al tipo più preciso

```java
double d = 2;
```

>[!warning]
>La somma di due caratteri dà un intero

#### Regole per il cast implicito

Il cast implicito avviene in fase di assegnazione:
- Byte, short e char possono essere promossi a int 
- Int può essere promosso a long
- float può essere promosso a double

Oppure può avvenire in fase di calcolo di un'espressione: se uno dei due operandi è un double, l'intera espressione è promossa a double.
Altrimenti, se uno dei due operandi è float, l'intera espressione è promossa a float.

