### Classe `IDuck`

Strutturata in questo modo

![[Pasted image 20240903121502.png|400]]

Ora vogliamo aggiungere il metodo `vola()`

![[Pasted image 20240903121612.png|400]]

Tutte le classi ereditano il metodo `vola()`.

Però, se volessimo aggiungere il la classe `AnatraDiPlastica` non sarebbe corretto, perché aggiungendo il metodo `vola()` non abbiamo pensato al fatto che non tutte le anatre non volano.

>[!warning]
>L'ereditarietà è utile per il riuso, ma meno per la manutenzione

#### Come possiamo risolvere il problema?

1) Sovrascriviamo il metodo vola nell'`AnatraDiPlastica`

![[Pasted image 20240903122105.png|400]]

Ma se aggiungiamo un altro tipo di anatra, `AnatraEsca`?

Le anatre esca sono esche: non volano né starnazzano

2) Implementiamo un'interfaccia per ogni comportamento dell'anatra

L'ereditarietà non è sufficiente, proviamo con le interfacce

![[Pasted image 20240903122317.png|500]]

#### E' una buona scelta?

- **Si**: permette a ciascuna sottoclasse di implementare i comportamenti che effettivamente essa deve modellare

- **No**: distrugge ogni possibile riuso del codice, perché dobbiamo reimplementare le interfacce per ogni sottoclasse

**Abbiamo bisogno dei design pattern**

---
### Design pattern

>[!info] Principio di design
>Identifica gli aspetti della tua applicazione che variano e separarli da quelli che rimangono uguali

- Come separarli? **Incapsulandoli**

- In questo modo tali parti del sistema varieranno in modo indipendente dalle altre parti

- Eliminando i metodi corrispondenti ai comportamenti che vogliamo modellare a parte:

![[Pasted image 20240903165018.png|500]]

#### Modellare i comportamenti di una classe 

Progettiamo un'interfaccia funzionale per ogni comportamento e per ogni possibile tipo di comportamento implementiamo l'interfaccia.

![[Pasted image 20240903165505.png|500]]

#### Integrare i comportamenti nella classe

La classe Anatra ora delega i suoi comportamenti di voli e starnazzo, invece di implementarli direttamente

![[Pasted image 20240903191530.png|500]]

Dove impostare il comportamento di volo specifico per ciascuna sottoclasse di Anatra?

Nel costruttore di ciascuna sottoclasse:

```java
public class AnatraDomestica extends Anatra
{
	public AnatraDomestica()
	{
		compVolo = new VoloConAli();
		compStarnazzo = new Starnazzo();
	}
}
```

#### Metodi "personalizzabili"

Grazie all'incapsulamento separato dei comportamenti abbiamo in realtà dei metodi "personalizzabili"

Per esempio, potremmo aggiunger alla classe Anatra i metodi:

```java
protected void setComportamentoDiVolo(ComportamentoDiVolo c)
{
	compVolo = c;
}

protected void setComportamentoDiStarnazzo(ComportamentoDiStarnazzo c)
{
	compStarnazzo = c;
}
```

---
### Strategy pattern

E' un pattern comportamentale e descrive un modo attraverso il quale possiamo cambiare il comportamento runtime degli oggetti.

Questo significa che abbiamo degli oggetti che vanno a decidere una strategia, per eseguire una determinata operazione, modificabile facilmente a runtime.

#### Esempio classe Monster

```java
public class TestDriver
{
	public static void main (String args[])
	{
		Monster m = new Monster();
		m.attack();
	}
}
```

Non abbiamo ancora una classe Monster e il metodo attack() quindi li andiamo a creare

```java
public class Monster
{
	void attack()
	{
		//...//
	}
}
```

Se eseguiamo `TestDriver` il programma esegue il main.

Ora vogliamo definire un altro attacco, quindi far si che il mostro decida a runtime che attacco utilizzare in base alle altre informazioni. 

Dobbiamo **scorporare** la strategia con cui viene effettuato l'attacco dalla classe `Monster`.

Definiamo un'interfaccia che avrà come metodo `attack`:

```Java
public interface AttackStrategy
{
	public void attack();
}
```

Quindi tutti i metodi che implementeranno tutte le strategie avranno il metodo `attack`.

Ora dobbiamo definire una simple strategy.

L'idea è quella di fare un refactoring della classe `Monster`.

```Java
public class SimpleAttackStrategy implements AttackStrategy
{
	@Override
	public void attack()
	{
		System.out.println ("ATTACK!!"); //Questa è la mia attack strategy
	}
}
```

Ora devo far utilizzare a Monster `AttackStrategy`.

All'interno di `Monster` definisco l'attributo `attackStrategy` di tipo `AttackStrategy`.

```Java
public class Monster
{
	AttackStrategy attackStrategy;

	public Monster () //costruttore
	{
		attackStrategy = new SimpleAttackStrategy();
	}

	void attack()
	{
		attackStrategy.attack();
	}
}
```

Demando al valore corrente di `AttackStrategy` la scelta di quale sia l'operazione da eseguire.

Quindi abbiamo fatto un refactoring, abbiamo estrapolato dalla classe `Monster` la sua strategia d'attacco e l'abbiamo messa in una classe a sé stante che implementa `AttackStrategy`.

