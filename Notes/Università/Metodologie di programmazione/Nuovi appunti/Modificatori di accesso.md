Sono parole riservate che forniscono al compilatore informazioni sulla natura del codice, dei dati e delle classi contenuti nel file sorgente.

Essi regolano la possibilità di accedere a una classe, a un metodo o a un attributo, da parte di una classe o di un metodo, esterno o interno alla classe stessa.

### Public

Il metodo o la variabile è visibile ovunque.

```java
public class Animale
{
	public int count;

	public static void main (String[] args)
	{
		Animale a = new Animale();
		a.count = 20;
	}
}
```

### Private

E' il modificatore più restrittivo. Il metodo o la variabile è visibile solo all'interno della stessa classe, quindi non è visibile/utilizzabile all'esterno della classe stessa.

```java
public class Animale 
{
	private int count;
}

public class Mucca extends Animale 
{
	public void hello()
	{
		count = 30;// errore di compilazione, variabile non visibile
	}
}

public class Prova 
{
	public static void main(String[] args)
	{
		Mucca a = new Mucca();
		a.count = 20;// errore di compilazione, variabile non visi-bile
	}
}
```

### Protected

Il metodo o la variabile è visibile solo dalle classi dello stesso package e da tutte le sottoclassi.

```java
package it;

public class Animale 
{
	protected int count;
}
package it;

public class Mucca extends Animale 
{
	public void hello() 
	{
		count = 30;
	}
}
package it;

public class Prova 
{
	public static void main(String[] args) 
	{
		Mucca a = new Mucca();
		a.count = 20;
	}
}
package com;

import it.Mucca;

public class cane 
{
	public static void main(String[] args) 
	{
		Mucca a = new Mucca();
		a.count = 20;// errore di compilazione, campo non accessabi-le (package diverso, siamo in “com” mentre animale è in “it”)
	}
}
```

### Default

Il metodo o la variabile è visibile dallo stesso package e dalle sottoclassi se sono nello stesso package.

```java
package it;

public class Animale 
{
	int count;
}
package it;

public class Mucca extends Animale 
{
	public void hello() 
	{
	count = 30;
	}
}

package com;
import it.Animale;
import it.Mucca;

public class cane extends Animale
{
	public void hello() 
	{
		count = 30;// errore di compilazione, campo non accessabile (siamo in package diversi, rispetto a animale)
	}

	public static void main(String[] args) 
	{
		Mucca a = new Mucca();
		a.count = 20;// errore di compilazione, campo non accessabi-le (siamo in package diversi, rispetto a animale)
	}
}
```

