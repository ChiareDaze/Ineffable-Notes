### Creazione di un array

```java
int[10] a; //crea un array con 10 valori pari a 0
a = new int[] {5, -2, 3, 0, 1, -6, 75, 32, 122, 4}; //creazione con valori
```

#### Esercizio stampa di un array

```java
public void stampaArray (String[] a)
{
	System.out.print("[");

	for (int k = 0; k < a.lenght; k++)
		System.out.print("\"" + a[k] + "\"") 
}
```

