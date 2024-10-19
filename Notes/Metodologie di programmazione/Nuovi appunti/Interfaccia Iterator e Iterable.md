### Iterabile

Ci sono molte classi di natura diversa che rappresentano sequenze di elementi. Tuttavia, le sequenze hanno qualcosa in comune:
- E' possibile **iterare sui loro elementi**

```java
public interface Iterabile:
{
	boolean hasNext();
	Object next ();
	void reset();
}
```

Ciascuna classe implementerà i metodi a suo modo:

```java
public class MyIntegerArray implements Iterable
{
	private Integer[] array;
	private int k = 0;

	public MyIntegerArray(Integer[] array)
	{
		this.array = array;
	}

	@Override
	public boolean hasNext()
	{
		return k < array.lenght;
	}

	@Override
	public Object next()
	{
		return array[k++]; //Possono essere specializzati a Integer e Character
	}

	@Override
	public void reset() { k = 0;}
}
```

```java
public class MyString implements Iterabile
//questa soluzione NON va bene
{
	private String s;
	private int k = 0;

	public MyString (String s)
	{
		this.s = s;
	}

	@Override
	public boolean hasNext()
	{
		return k < s.lenght;
	}

	@Override
	public Object next()
	{
		return s.charAt[k++];  //Possono essere specializzati a Integer e Character
	}

	@Override
	public void reset() { k = 0;}
}
```

```java
//testiamo le classi
public class InterfacceChePassione
{
	static public void main (Stirng[] args)
	{
		Iterabile i1 = new MyIntegerArray(new Integer[] {10, 20, 30, 40});
		Iterabile i2 = new MyString ("abcdefghijk");

		for (Iterabile i : new Interabile[] {i1, i2})
		{
			while (i.hasNext())
				System.out.println(i.next());
		}
	}
}
```

>[!warning] L'esempio "Iterabile" non è la soluzione ideale per iterare su una collezione
>- Non permette di mantenere contatori multipli sullo stesso oggetto
>```java
>MyString s = new MyString("ciao");
>while (s.hasNext())
>{
>	char c1 = s.next();
>	while (s.hasNext())
>	{
>		char c2 = s.next();
>		System.out.println(c1 + "" + c2);
>	}
>}
>```
>Questo esempio **NON FUNZIONA**

### La soluzione è usare Iterable e Iterator

Sono interfacce standard di Java che disaccoppiano l'oggetto su cui iterare dall'oggetto che tiene la posizione d'iterazione.

#### `java.lang.Iterable`

![[Pasted image 20240902182507.png||500]]

#### `java.util.Iterator`

![[Pasted image 20240902182614.png|500]]

E' un'interfaccia fondamentale che permette di iterare su collezioni ed è in relazione con l'interfaccia `Iterable` nel senso che chi implementa `Iterable` restituisce un `Iterator` sull'oggetto-collezione.

