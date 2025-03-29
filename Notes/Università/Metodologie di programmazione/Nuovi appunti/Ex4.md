### Cosa sono i Design Pattern? Perché esistono? Quali vantaggi possono recare se adottati?

I design pattern sono soluzioni progettuali usate per risolvere problemi comuni in modo efficace nel design del software. Sono dei concetti generali a cui far riferimento per risolvere uno specifico problema.

I design pattern forniscono strutture che possono essere riapplicate in diversi progetti, riducendo in questo modo la necessità di scrivere un nuovo codice completamente da capo.

Molti pattern rendono il codice più flessibile permettendone una maggiore leggibilità e facilità di manutenzione, riducendo la possibilità di errore in fase di compilazione del codice stesso. Inoltre, l'uso di un pattern può aiutare a gestire meglio eventuali modifiche o l'aggiunta di nuove funzionalità.

I design pattern di distinguono in tre categorie in base al loro scopo.

**Creazionali**: forniscono meccanismi di creazione degli oggetti aumentando la flessibilità e il riutilizzo del codice.

**Strutturali**: spiegano come assemblare oggetti e classi in strutture più ampie, mantenendo flessibili ed efficienti le strutture.

**Comportamentali**: si occupano della comunicazione efficace e dell'assegnazione dei compiti tra oggetti.

 ---
 
### Pattern Decorator

E' un pattern strutturale che permette di aggiungere funzionalità in modo dinamico a un oggetto senza alterare le sue classi. 
Il principio alla base del decorator è l'**Open Closed Principle**, vale a dire che le classi sono aperte all'estensione ma chiuse alla modifica.

Questo pattern si ottiene "decorando" l'oggetto, cioè avvolgendolo in un nuovo oggetto che aggiunge nuovi comportamenti, lasciando intatta la classe astratta originale.

Questo pattern si usa quando si ha un oggetto esistente e si vogliono aggiungere nuove funzionalità in modo flessibile e modulare, oppure quando non si può modificare direttamente il codice dell'oggetto originale.

Il decorator funziona in questo modo: c'è una base (interfaccia o classe astratta) e i vari decoratori implementano o ereditano da quella classe.
I decoratori hanno un riferimento all'oggetto che stanno decorando e possono aggiungere comportamenti prima o dopo aver delegato il lavoro all'oggetto originale.
#### Esempio classe Food

Supponiamo di avere una classe astratta `Food` e diversi cibi. Prendiamo come esempio la classe `Hamburger`.

Supponiamo ora di voler aggiungere dinamicamente degli extra, come l'insalata o il cheddar, senza modificare la classe `Hamburger`.

```Java
public abstract class Food{
	public abstract String getName();
	public abstract double cost();
}
```

La classe `Hamburger` estenderà `Food`.

```Java
public class Hamburger extends Food{
	@Override
	public String getName(){
		return "Burger";
	}

	@Override
	public double cost(){
		return 5.50; //costo base di un Hamburger
	}
}
```

Ora si potrà creare la classe astratta `Decorator` che estende `Food` e ha un riferimento a un oggetto di tipo `Food`.

Verrà usato **protected** poiché la classe decorator potrebbe essere estesa da altre sottoclassi che potrebbero, a loro volta, voler accedere al campo `food` per eseguire operazioni.

```Java
public abstract class FoodDecortor extends Food {
    protected Food food;

    public FoodDecorator(Food food) {
        this.food = food;
    }

    @Override
    public String getName() {
        return food.getName();
    }

    @Override
    public double cost() {
        return food.cost();
    }
}
```

Ora si possono creare decoratori per aggiungere nuove funzionalità (cheddar e insalata in questo caso).

```Java
public class CheddarDecorator extends FoodDecorator{
	public CheddarDecorator(Food food){
		super(food);
	}

	@Override
    public String getName() {
        return food.getName() + ", Cheddar";
    }

    @Override
    public double cost() {
        return food.cost() + 0.30; //aggiunge il costo del cheddar
    }
}
```

```Java
public class SaladDecorator extends FoodDecorator{
	public SaladDecorator(Food food){
		super(food);
	}

	@Override
    public String getName() {
        return food.getName() + ", Salad";
    }

    @Override
    public double cost() {
        return food.cost() + 0.10; //aggiunge il costo dell'insalata
    }
}
```

##### Test

```Java
public class HamburgerShop {  
    public static void main(String[] args) {  
        Food cheeseburger = new Hamburger(); // Un hamburger senza ingredienti aggiuntivi  
        System.out.println(cheeseburger.getName() + " €" + cheeseburger.cost());  
  
        cheeseburger = new CheddarDecorator(cheeseburger); // Aggiungo il cheddar  
        System.out.println(cheeseburger.getName() + " €" + cheeseburger.cost());  
  
        cheeseburger = new SaladDecorator(cheeseburger); // Aggiungo l'insalata  
        System.out.println(cheeseburger.getName() + " €" + cheeseburger.cost());  
    }  
}
```

![[Pasted image 20240917155256.png|450]]

#### Vantaggi

Con il decorator pattern è possibile estendere le funzionalità di una classe senza alterarne il codice.
Inoltre, è possibile combinare i decoratori aggiungendo o rimuovendo comportamenti in modo dinamico. Il decorator pattern è una valida alternativa all'estensione attraverso l'ereditarietà.

---

### Pattern Observer Observable

E' un pattern comportamentale progettato in modo tale da stabilire una relazione una-a-molti tra oggetti.

Si basa su due componenti principali: l'**observable** e l'**observer**.
Gli observer osservano gli observable. Quando gli observable cambieranno il proprio stato notificheranno l'evento a tutti gli observer.

#### Esempio classe attore

Supponiamo che un certo attore abbia una pagina Twitter (Observable) e una lista di followers (Observer).

Questo specifico design pattern servirà a notificare tutti i followers di un nuovo tweet pubblicato dell'attore in questione.

Innanzitutto, si implementa l'interfaccia `Subject` che permette di registrare, rimuovere e implementare un metodo per notificare gli observer quando lo stato viene modificato.

```Java
public interface Subject{
	public void register(Observer o); //registra l'obsrver
	public void unregister (Observer o); //annulla la registrazione
	public void notifyAllObserver (String s); //notifica tutti gli observer
}
```

Si implementa l'interfaccia `Observer` che definisce il metodo `update()`, il quale verrà chiamato ogni volta che il soggetto invia una notifica (quando l'attore pubblicherà un tweet).

```Java
public interface Observer{
	public void update (String name, String s);
}
```

Si crea la classe concreta `Actor` che implementa `Subject` e mantiene lo stato d'interesse e notifica gli observer.

```Java
public class Actor implements Subject{
	private String actorName;
	private ArrayList <Observer> followers = new ArrayList <Observer>();

	public Actor (String actorName){
		this.actorName = actorName;
	}

	@Override
	public void register(Observer o){
		followers.add(o); //aggiunge il follower
		System.out.println(o + " has started following " + actorName);
	}

	public void unregister(Obserber o){
		followers.remove(0); //rimouove il follower
		System.out.println(o + " has stopped following " + actorName);
	}

	@Override
	public void notifyAllObserver (String s){
	
		for (Observer observer : followers){
			observer.update(actorName, s);
		}
	}

	public void tweet (String t){
		System.out.println(actorName+ " has tweeted " +"\"" + t + "\"");
		notifyAllObserver(t);
	}
}
```

Il metodo `notifyAllObserver` scorre `followers` e richiama il metodo `update` passandogli il nome della celebrità e la stringa `s`. 

Ora si crea la classe `Follower` che implementa il metodo `update()` per reagire alle notifiche inviate dal soggetto.

```Java
public class Follower implements Observer
{
	private String followerName;

	public Follower(String followerName)
	{
		this.followerName = followerName;
	}

	@Override
	public void update(String name, String s)
	{
		System.out.println(followerName + " has recived " + name + "'s tweet \"" + s + "\"");
	}

	@Override
	public String toString()
	{
		return "Follower [Name = " + followerName + " ]";
	}
}
```

##### Test

```Java
public class Client {  
    public static void main(String[] args)  
    {  
        Actor davidTennant = new Actor ("David Tennant");  
        Actor mattSmith = new Actor ("Matt Smith");  
  
        Follower darioMoccia = new Follower ("Dario Moccia");  
        Follower jackSparrow = new Follower ("Captain Jack Sparrow");  
        Follower scroogeMcDuck = new Follower ("Scrooge McDuck");  
  
        davidTennant.register(scroogeMcDuck);  
        davidTennant.register(darioMoccia);  
  
        mattSmith.register(jackSparrow);  
  
        davidTennant.tweet("ALLONS-Y!!");  
        mattSmith.tweet("Trust me, I'm the Doctor");  
  
        davidTennant.unregister(darioMoccia);  
    }  
}
```

![[Pasted image 20240917204641.png|600]]

#### Vantaggi

L'observer pattern permette di comunicare uno stato o un evento a un insieme di oggetti in modo indipendente.
Nuovi observer possono essere aggiunti senza modificare il codice dell'Observable. Infatti, ogni implementazione di Observer può essere aggiunta registrandola.
Gli aggiornamenti vengono inviati automaticamente a tutti gli observer quando lo stato dell'observable cambia in modo tale da eliminare la necessità di richiedere continuamente le informazioni.