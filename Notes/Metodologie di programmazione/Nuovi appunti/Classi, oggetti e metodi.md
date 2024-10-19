### Cosa possono fare?

- Modellare gli oggetti del mondo reale
- Rappresentare oggetti grafici
- Rappresentare entità software (immagini, file, eventi, ecc.)
- Rappresentare concetti astratti (regole di un gioco, posizioni di un giocatore)
- Rappresentare stati di un processo, di esecuzione, ecc.

Una classe è un pezzo del codice sorgente di un programma che descrive un particolare tipo di oggetti.

Le classi sono definite dal programmare e forniscono un prototipo astratto per gli oggetti di un particolare tipo.

Definisce anche la struttura in termini di **campi** (stato) e **metodi** (comportamenti) degli oggetti.

Un oggetto è un'**istanza** (un esemplare) di una classe
Un programma può creare e usare uno o più oggetti (istanze) della stessa classe.

#### Ex. Classe automobile

**Campi**

```java
String modello;
Color colore;
int numPasseggeri;
double benzina;
```

**Metodi**

- Aggiungi/togli passeggero
- Riempi serbatoio
- Segnala quantità

### Ex. Oggetto una certa automobile

**Campi**

```java
String modello = "5";
Color colore = Color.PINK;
int numPasseggeri = 1;
double benzina = 50;
```

**Metodi**

- Come la classe

### Classe e oggetto a confronto

**Classe**
E' definita mediante parte del codice sorgente del programmatore ed è scritta da quest'utlimo.

Specifica la struttura dei campi dei suoi oggetti e il comportamenti dei suoi oggetti mediante il codice dei metodi.

**Oggetto**
E' un'entità all'interno di un programma in esecuzione ed è creato quando un programma "gira" (dal metodo **main** o da un altro metodo).

Contiene specifici valori dei campi che possono cambiare durante l'esecuzione.
L'oggetto si comporta nel modo prescritto dalla classe quando il metodo corrispondente viene chiamato a tempo di esecuzione. 

#### Ex. Classe anello e oggetto anello1,..., anello182

**Classe Anello**

![[Pasted image 20240711175252.png|150]]

```java
int x;
int y;
int r;
```

**Metodi**

- Ruota

**Oggetti**

![[Pasted image 20240711180231.png|200]]

### Campi

- Un campo (detto anche variabile di istanza) costituisce la **memoria privata** di un oggetto.
- Ogni **campo** ha un tipo di dati
- Ogni campo ha un nome fornito dal programmatore

**Dichiarare un campo**

```java
private static final tipo_di_dati nome;
```

### Metodi

E' tipicamente **pubblico**, cioè visibile a tutti.
Il nome di un metodo per convenienza inizia con una lettera minuscola, mentre le parole seguenti iniziano con lettera maiuscola (camelCase)

![[Pasted image 20240711180918.png|500]]

**Definizione di un metodo**

```java
public tipo_di_dato nomeDelMetodo (tipo_di_dati nomeParamn1,...,)
```

Un metodo può restituire un valore al chiamante

```java
public int getValue() {return value;}
```

La parola chiave **void** nell'intestazione del metodo indica che il metodo non restituisce alcun valore:

```java
public void reset(int newValue) {value: newValue;}
```

### Campi

Sono variabili dichiarate all'interno di una classe ma al di fuori di qualsiasi metodo, costruttore o blocco. I campi rappresentano le proprietà o lo stato di un oggetto e ogni istanza della classe avrà la propria copia.

#### Ex. classe persona

```java
public class Persona 
{ 
	// Dichiarazione dei campi private String nome; 
	private int età; 
	
	// Costruttore
	public Persona(String nome, int età) 
	{ 
		this.nome = nome;
		this.età = età;
	} 
	
	// Metodi per accedere e modificare i campi 
	public String getNome() 
	{ 
		return nome; 
	} 
	
	public void setNome(String nome) 
	{ 
		this.nome = nome; 
	} 
	
	public int getEtà() 
	{ 
		return età;
	} 
	
	public void setEtà(int età) 
	{ 
		this.età = età; 
	} 
}
```

### Costruttori

Sono metodi per la creazione degli oggetti di una classe e possiedono sempre lo stesso nome della classe.
Inizializzano i campi dell'oggetto, prendono zero, uno o più parametri e non hanno valori di uscita.
Una classe può avere più costruttori che differiscono nel numero e nei tipi dei parametri.

#### Ex. Classe Counter

```java
public Counter()
{
	value = 0; //inizializzazione dei campi
}

public Counter (int initialValue)
{
	value = initialValue () //input del costruttore
}
```


### Parole chiave nelle dichiarazioni dei campi

#### Visibilità 

- `Private`: Accessibile solo all'interno della stessa classe
- `Protected`: Accessibile alle classi nello stesso pacchetto e alle sottoclassi
- `Public`: accessibile da qualsiasi altra classe
- `Default`: Accessibile solo alle classi nello stesso pacchetto

#### Modificatori addizionali

- `static`: il campo è condiviso tra tutte le istanze della classe
- `final`: il campo può essere assegnato solo una volta e il suo valore non può essere cambiato
