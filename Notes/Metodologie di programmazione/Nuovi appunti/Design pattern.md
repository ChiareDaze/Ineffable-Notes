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

**Abbiamo bisogno dei design pattern!**

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

Ora implementiamo una nuova classe `PowerAttackStrategy` che implementa `AttackStrategy`.

```Java
public class PowerAttackStrategy implements AttackStrategy
{
	@Override
	public void attack()
	{
		System.out.println ("POWERATTACK!!");
	}
}
```

Come faccio nel `TestDriver` a cambiare la strategia di attacco?

```Java
public class TestDriver
{
	public static void main (String args[])
	{
		Monster m = new Monster();
		m.attack();
		m.setAttackStrategy(new PowerAttackStrategy());
		m.attack();
	}
}
```

E creo il metodo `setAttackStrategy`.

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

	void setAttackStrategy(AttackStrategy newAttackStrategy)
	{
		attackStrategy = newAttackStrategy;
	}
}
```

In questo modo posso cambiare le strategie ti attacco del mostro.

>[!info]  In sintesi
>- Abbiamo preso una classe che ha un determinato comportamento
>- Abbiamo estratto questo comportamento attraverso uno strategy (quindi creando un'interfaccia e poi una classe che implementa l'interfaccia)
>- Abbiamo generalizzato e adattato a varie esigenze l'interfaccia semplicemente creando delle classi che la implementano 
>- Abbiamo, infine, utilizzato `setAttackStrategy` per cambiare il comportamento della classe `Monster`

>[!Important] Perché è importante il Pattern Strategy?
>- Consente di avere delle gerarchie di oggetti molto profonde 
>- E' comodo da sviluppare

---

### Singleton pattern

Assicura che, della classe singleton, ne esista solo una sola istanza.

Innanzitutto creiamo la classe `DriveTest` e creiamo la classe `Singleton`.

```Java
public class DriverTest
{
	public static void main(String[] args)
	{
		//...//
	}
}
```

La classe non potrà essere richiamata con:

```Java
Singleton s = new Singleton;
```

Questo perché `new` crea una nuova istanza e non vogliamo che questo succeda.

Creiamo la classe `Singleton` che non dovrà avere un costruttore.

```Java
class Singleton
{
	private Singleton() 
	{
		//...//
	}
}
```

Quando compileremo il programma andrà in errore proprio perché il costruttore è `private`.

Il singleton gestisce al suo interno in modo privato un'istanza del suo stesso tipo.

```Java
class Singleton
{
	private Singleton instance;

	private Singleton() 
	{
		//...//
	}
}
```

`Instance` **non è mai modificabile**.

L'unico elemento pubblico che mi serve è un metodo getter che ritorna un `Singleton`.

```Java
class Singleton
{
	private Singleton instance;

	private Singleton() 
	{
		//...//
	}

	public Singleton getInstance()
	{
		
	}
}
```

Devo ancora risolvere il problema della creazione delle istanze.

Quindi scriveremo:

```Java
class Singleton
{
	private Singleton instance;

	private Singleton() 
	{
		//...//
	}

	public Singleton getInstance()
	{
		if (instance == null)
			instance = new Singleton();
	}
}
```

Ho ancora un problema: visto che dal codice client (il codice che utilizza il Singleton) non posso usare `new` non è possibile che il metodo non sia statico perché se il metodo è associato a un'istanza che devo poter creare (ma in questo caso non possiamo creare l'istanza dal momento in cui dichiaro `private` il costruttore).

Quindi dichiarerò `getIstance()` come **static**.

```Java
class Singleton
{
	private Singleton instance;

	private Singleton() 
	{
		//...//
	}

	public static Singleton getInstance()
	{
		if (instance == null)
			instance = new Singleton();
	}
}
```

Ora il programma darà errore sulle righe

```Java
if (instance == null)
	instance = new Singleton();
```

Perché se `getInstance()` è un metodo statico, potrà accedere solo a variabili statiche.

Quindi dichiariamo **static** anche `instance`

```Java
class Singleton
{
	private static Singleton instance;

	private Singleton() 
	{
		//...//
	}

	public static Singleton getInstance()
	{
		if (instance == null)
			instance = new Singleton();

		return instance;
	}
}
```

A questo punto, tornando a `DriverTest`

```Java
Singleton s = new Singleton();
```

dovrà essere scritto come

```Java
Singleton s = Singleton.getInstance();
```

Con `Singleton.getInstance()` sto richiamando un metodo **statico** associato alla classe.

Per capire come funziona il programma aggiungiamo un nuovo oggetto `s2` nel main e se `s` e `s2` sono uguali allora dovrà stampare `ok`.

```Java
public class DriverTest
{
	public static void main(String[] args)
	{
		Singleton s = Singleton.getInstance();
		Singleton s2 = Singleton.getInstance();

		if (s == s2)
		{
			System.out.println("ok");
		}
	}
}
```

Eseguendo il programma verrà stampato `ok`.

Questo perché gli oggetti `s` e `s2` sono entrambi il valore della variabile `instance`. 

La prima volta che accedo alla riga

```Java
Singleton s = Singleton.getInstance();
```

Viene inizializzata `instance` utilizzando il costruttore e viene ritornata.

Quando eseguiamo la riga

```Java
Singleton s2 = Singleton.getInstance();
```

`Instance` non sarà più **null** perché è uguale al valore che le ho assegnato eseguendo la riga precedente.

Questo vuol dire che le verrà assegnato lo stesso oggetto che è stato inizializzato precedentemente.

Le classi che saranno un singleton potranno eventualmente ereditare da questo singleton, oppure implementare al loro interno questo pattern.

### Pattern Observer Observable

Due elementi importanti: gli "osservatori" (Observer) e gli "osservati" (Subject).

Gli "osservatori" osserveranno gli "osservati" e quando gli "osservati" faranno qualcosa, notificherà l'evento a tutti gli "osservatori".

#### Esempio celebrità-fan

```Java
public interface Subject
{
	public void register(Observer o); //registra l'osservatore
	public void unregister(Observer o); //annulla la registrazione
	public void notifyAllObserver(String s); //notifica tutti gli osservatori
}
```

Creo la classe `Celebrity` che implementa `Subject`

```Java
public class Celebrity implements Subject
{
	private String celebrityName;
	private List <Observer> followers;

	public Celebrity (String celebrityName)
	{
		super();
		this.celebrityName = celebrityName; //nome celebrità
		this.followers = new ArrayList<>(); //lista followers (Osservatori)
	}

	@Override
	public void register(Observer o)
	{
		followers.add(o); //aggiunge il follower
	}

	@Override
	public void unregister(Observer o)
	{
		followers.remove(o); //rimuove il follower
	}

	@Override
	public void notifyAllObserver(String s)
	{
		for (Observer observer : followers)
		{
			observer.update(celebrityName, s);
		}
	}

	public void tweet (String t)
	{
		System.out.println(CelebrityName+ " has tweeted " + t);
		notifyAllObserver(t);
	}
}
```

Il metodo `notifyAllObserver` scorre `followers` e richiama il metodo `update` passandogli il nome della celebrità e `s`.   

`Observer` è l'interfaccia che implementeranno i vari fan e ha solo `update` come metodo.

```Java
public interface Observer
{
	public void update (String name, String s);
}
```

Ora creiamo la classe `Follower` che andrà a implementare l'interfaccia `Observer`.

```Java
public class Follower implements Observer
{
	private String followerName;

	public Follower
	{
		super();
		this.follower = followerName;
	}

	@Override
	public void update(String name, String s)
	{
		System.out.println(followerName + " has recived " + s + "'s tweet " + name)
	}

	@Override
	public String toString()
	{
		return "Followers [followerName = " + followerName + " ]";
	}
}
```

Creiamo il main

```Java
public class Client
{
	public static void main(String[] args)
	{
		Celebrity davidTennant = new Celebrity ("David Tennant");
		Celebrity michaelSheen = new Celebrity ("Michael Sheen");

		Follower goofy = new Follower ("Goofy");
		Follower pluto = new Follower ("Pluto");
		Follower scroogeMcDuck = new Follower ("Scrooge McDuck");

		davidTennant.register(scroogeMcDuck);
		davidTennant.register(goofy);

		michaelSheen.register(pluto);

		davidTennant.tweet("ALLONS-Y");
		michaelSheen.tweet("DAVID!!! WHAT HAS HAPPEN TO YOUR HAIR!!!")
	}
}
```

I messaggi verranno notificati a tutti i followers.

Il tweet verrà inviato solo agli utenti registrati.

---

### Builder pattern

Si occupa del modo in cui viene creato un oggetto.

#### Quando usiamo il Builder pattern?

1. Quando una classe ha troppe variabili e alcune di loro sono dello stesso tipo creando, in questo modo, confusione nel client program;
2. Quando alcuni parametri sono facoltativi e il programma dovrà passarli come argomento nullo;
3. Quando la creazione dell'istanza della classe è troppo pesante e complessa.

#### Esempio classe Computer


```Java
public class Computer
{
	//parametri necessari
	private String RAM;
	private String HDD;
	private String CPU;

	//parametri facoltativi
	private boolean isGraphicsCardEnabled;
	private boolean isBluetoothEnabled;

	private Computer (Builder builder)
	{
		this.RAM = ram;
		this.HDD = hdd;
		this.CPU = cpu;
		this.isGraphicsCardEnabled = isGraphicsCardEnabled
		this.isBluetoothEnabled = isBluetoothEnabled;
	}
}
```

Per ogni parametro dobbiamo creare una metodo `getter`.

```Java
public class Computer
{
	//parametri necessari
	private String RAM;
	private String HDD;
	private String CPU;

	//parametri facoltativi
	private boolean isGraphicsCardEnabled;
	private boolean isBluetoothEnabled;

	private Computer (Builder builder)
	{
		this.RAM = ram;
		this.HDD = hdd;
		this.CPU = cpu;
		this.isGraphicsCardEnabled = isGraphicsCardEnabled
		this.isBluetoothEnabled = isBluetoothEnabled;
	}

	public String getHDD() {
			return HDD;
		}
	
		public String getRAM() {
			return RAM;
		}
	
		public boolean isGraphicsCardEnabled() {
			return isGraphicsCardEnabled;
		}
	
		public boolean isBluetoothEnabled() {
			return isBluetoothEnabled;
		}

}
```

Creiamo ora classe `Builder`, che dovrà essere statica e dovrà essere annidata in modo che potrà utilizzare il costruttore della classe.

La classe dovrà gli stessi parametri di `Computer` e un costruttore dove gli argomenti sono tutti i parametri necessari.

```Java
public static class Builder
{
	//parametri necessari
	private String RAM;
	private String HDD;
	private String CPU;

	//parametri facoltativi
	private boolean isGraphicsCardEnabled;
	private boolean isBluetoothEnabled;

	public Builder(String ram, String hdd, String cpu)
	{
		this.RAM = ram;
		this.HDD = hdd;
		this.CPU = cpu;
	}
}
```

Ora dobbiamo creare dei metodi per impostare i parametri facoltativi.

```Java
public static class Builder
{
	//parametri necessari
	private String RAM;
	private String HDD;
	private String CPU;

	//parametri facoltativi
	private boolean isGraphicsCardEnabled;
	private boolean isBluetoothEnabled;

	public Builder(String ram, String hdd, String cpu)
	{
		this.RAM = ram;
		this.HDD = hdd;
		this.CPU = cpu;
	}

	public void setGraphicsCardEnabled (boolean isGraphicsCardEnabled)
	{
		this.isGraphicsCardEnabled = isGraphicsCardEnabled;
	}

	public void setBluetoothEnabled (boolean isBluetoothEnabled)
	{
		this.isBluetoothEnabled = isBluetoothEnabled;
	}
}
```

Ora dobbiamo cambiare i metodi per restituire l'istanza di `Builder`.

Basta cambiare **void** in **Builder** e scrivere `return this` (ritorna la corrente istanza dell'oggetto).

```Java
public static class Builder
{
	//parametri necessari
	private String RAM;
	private String HDD;
	private String CPU;

	//parametri facoltativi
	private boolean isGraphicsCardEnabled;
	private boolean isBluetoothEnabled;

	public Builder(String ram, String hdd, String cpu)
	{
		this.RAM = ram;
		this.HDD = hdd;
		this.CPU = cpu;
	}

	public Builder setGraphicsCardEnabled (boolean isGraphicsCardEnabled)
	{
		this.isGraphicsCardEnabled = isGraphicsCardEnabled;
		return this;
	}

	public Builder setBluetoothEnabled (boolean isBluetoothEnabled)
	{
		this.isBluetoothEnabled = isBluetoothEnabled;
		return this;
	}
}
```

Ora creiamo un metodo che restituirà l'istanza di `Computer`.

In genere questo metodo è chiamato `build()`.

```Java
public Computer build ()
{
	return new Computer(this);
}
```

Ora scriviamo il main

```Java
public class ComputerClient
{
	public static void main(String args[])
	{
		Computer comp = new Computer.Builder("2GB", "2TB", "Intel i7").build();

		Computer comp1 = new Computer.Builder("2GB", "2TB", "Intel i7").setGraphicsCardEnabled(true);
	}
}
```

---
### Decorator

E' un pattern strutturale che permette di aggiungere dinamicamente funzionalità a un oggetto senza modificare il suo codice originale o alterare le sue classi.

Questo si ottiene "decorando" l'oggetto, cioè avvolgendolo in un nuovo oggetto che aggiunge nuovi comportamenti, lasciando intatta l'interfaccia originale.

#### Quando si usa decorator?

Quando si ha un oggetto esistente e vuoi aggiungere nuove funzionalità in modo flessibile e modulare, oppure quando non si può modificare direttamente il codice dell'oggetto originale (per esempio, per evitare di creare una gerarchia di classi molto complessa o per non toccare il codice esistente).

#### Come funziona?

Decorator segue una logica simile alla composizione. C'è una base (interfaccia o classe astratta) e i vari decoratori implementano o ereditano da quella classe.

I decoratori hanno un riferimento all'oggetto che stanno decorando e possono aggiungere comportamenti prima o dopo aver delegato il lavoro all'oggetto originale.

#### Esempio Beverage

Supponiamo di avere un'interfaccia per una **Beverage** e diverse implementazioni di bevande come `Caffè`. 
Ora, vogliamo aggiungere dinamicamente degli "extra" come **latte** o **zucchero** senza modificare la classe `Caffè`.

Implementiamo  l'interfaccia `Beverage`.

```Java
public interface Beverage {
    String getDescription();
    double cost();
}
```

Creiamo la classe `caffè` che implementa `Beverage`.

```Java
public class Coffee implements Beverage {
    @Override
    public String getDescription() {
        return "Coffee";
    }

    @Override
    public double cost() {
        return 1.50; // Costo base del caffè
    }
}
```

Creiamo la classe astratta `Decorator` che implementa `Beverage` e ha un riferimento a un oggetto `Beverage`.

Usiamo **protected** perché la classe decoratrice astratta potrebbe essere estesa da altre sottoclassi, che potrebbero voler accedere direttamente al campo `beverage` per eseguire ulteriori operazioni. 

```Java
public abstract class BeverageDecorator implements Beverage {
    protected Beverage beverage;

    public BeverageDecorator(Beverage beverage) {
        this.beverage = beverage;
    }

    @Override
    public String getDescription() {
        return beverage.getDescription();  // Delegazione all'oggetto decorato
    }

    @Override
    public double cost() {
        return beverage.cost();  // Delegazione all'oggetto decorato
    }
}
```

Ora possiamo creare decoratori per aggiungere funzionalità come latte e zucchero.

```Java
public class LatteDecorator extends BeverageDecorator {
    public LatteDecorator(Beverage beverage) {
        super(beverage);
    }

    @Override
    public String getDescription() {
        return beverage.getDescription() + ", Latte";
    }

    @Override
    public double cost() {
        return beverage.cost() + 0.50;  // Aggiunge il costo del latte
    }
}
```

```Java
public class SugarDecorator extends BeverageDecorator {
    public SugarDecorator(Beverage beverage) {
        super(beverage);
    }

    @Override
    public String getDescription() {
        return beverage.getDescription() + ", Sugar";
    }

    @Override
    public double cost() {
        return beverage.cost() + 0.20;  // Aggiunge il costo dello zucchero
    }
}
```

Scriviamo il main

```Java
public class Main {
    public static void main(String[] args) {
        Beverage coffee = new Coffee();  // Crea un caffè semplice
        System.out.println(coffee.getDescription() + " $" + coffee.cost());

        // Aggiungi latte al caffè
        coffee = new LatteDecorator(coffee);
        System.out.println(coffee.getDescription() + " $" + coffee.cost());

        // Aggiungi anche zucchero al caffè con latte
        coffee = new SugarDecorator(coffee);
        System.out.println(coffee.getDescription() + " $" + coffee.cost());
    }
}
```

L'output sarà:

```java
Coffee $1.5 
Coffee, Latte $2.0 
Coffee, Latte, Sugar $2.2
```

>[!Important] Vantaggi del Decorator
>- Flessibilità: si può aggiungere nuove funzionalità senza modificare le classi esistenti;
>- Modularità: si può combinare i decoratori in modo flessibile, aggiungendo o rimuovendo comportamenti dinamicamente;
>- Riutilizzo del codice: i decoratori possono essere riutilizzati con altri oggetti che implementano la stessa interfaccia.


>[!warning] Svantaggi del Decorator
>- Tanti oggetti: se usato eccessivamente, il pattern può generare molte piccole classi e oggetti, complicando la manutenzione;
>- Debug più complesso: capire la combinazione esatta dei decoratori può diventare difficile in sistemi complessi.

---
