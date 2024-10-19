Sono utilizzate per poter dichiarare caratteristiche comuni tra classi di una determinata gerarchia.

Non possono essere istanziate, analogamente a quanto accade per le interfacce.
Quindi non posso essere trasformate in oggetti.

#### Esempio classe Animale

```java
public abstract class Animale
{
	private String verso;

	public void Animale (Stirng verso)
	{
		this.verso = verso;
	}
	
	public String getVerso()
	{
		return verso;
	}
}

public abstract class Mammifero implements Animale
{
	
}

public abstract class Oviparo implements Animale
{
	
}
```

### Differenze tra interfacce e classi astratte

Le interfacce definiscono i metodi da implementare il cui codice verrà definito nella classe che implementa quell'interfaccia.

Le classi astratte vengono ereditate dalle altre classi (come accade per tutti i tipi di classe) e i metodi vengono definiti e scritti nella classe astratta stessa, contrariamente a quanto accade nelle interfacce.

