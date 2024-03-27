### Classe universale Object

- Tutte le classi sono sottoclassi di Object

---
### Sovrascrivere il metodo equals

- Il metodo equals viene invocato per confrontare il contenuto di due oggetti
- Per default, sono "uguali", il metodo restituisce true 

```java
public boolean equals(Object o) {return this == 0;}
```

- Tuttavia, la classe Object non conosce il contenuto della sottoclasse
	- Per mantenere il contenuto del metodo è necessario sovrascriverlo

```java
public class
{
	private int x, y, z;ù


	public boolean equals(Object o)
	{
		if (o == null) return false;
		if (getClass != o.getClass()) return false;
		Punto p = (Punto)o;
		return x == p.x && y == p && z == p.z;
	}
}
```


### Enum e Object

- Una enumerazione ha tante istanze quante sono le costanti enumerative al suo interno
	- Non è possibile costruire altre istanze
- Le classi enumerative estendono la classe `Enum`, da cui ereditano i metodi `toString` e `clone` 
	- `toString` restituisce il nome della costante
	- `clone` restituisce l’oggetto enumerativo stesso senza farne una copia (che non è possibile fare, visto che sono costanti)
- `Enum` a sua volta estende Object, per cui il metodo equals restituisce true solo se le costanti enumerative sono identiche

> [!warning]
> Non possono essere create nuove istanze, ma possono essere costruite le istanze "costanti"
> - Si definisce un costruttore (non pubblico, ma con visibilità di default)
> - Si costruisce ciascuna costante (un oggetto separato per ognuna)
> - Si possono definire altri metodi di accesso o modifica dei campi

---
### Metodi e classi final

- Con la parola abstract obblighiamo i programmatori a implementare certi metodi
- La parola chiave final ci permette di fare il contrario: impedire ad altri programmatori di
	- Creare sottoclassi (se specificato di fronte a class)
	- Reimplementare (=sovrascrivere) certi metodi (di fronte all'intestazione del metodo)