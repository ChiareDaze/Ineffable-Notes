### Overloading

Si ha quando abbiamo metodi uguali ma con parametri diversi

```java
public class Test 
{
	public void hello()
	{

	}

	public void hello (int i)
	{

	}

	public void hello (String i)
	{
	
	}
}
```

### Overriding

La classe eredita dai metodi di una classe padre e li sovrascrive

```java
public class TestFiglio extends Test //eredita i metodi di Test
{
	public void hello (int i)
	{
		int temp = i + 10;
		System.out.printlm(temp);
	}

	public static void main (String[] args)
	{
		Testfiglio r = new TestFiglio();
		r.hello(10); //sto chiamando il metodo in TestFiglio e non quello in Test
	}
}

```

