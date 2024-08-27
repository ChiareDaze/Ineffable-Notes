Un'interfaccia è un insieme di metodi che una classe deve implementare se vuole implementare quell'interfaccia.

Un'interfaccia è un tipo di riferimento che può contenere solo **metodi astratti** e **campi costanti** (che sono implicitamente public, static e final).

Vengono utilizzate per definire un contratto che deve essere implementato da una classe concreta. 
Quindi, una classe che implementa un'interfaccia deve fornire un'implementazione per tutti i metodi definiti nell'interfaccia.

#### Esempio

```java
public interface FormaGeometrica
{
	double PI =  3.14;
	double area();
	double perimetro();
}
```

#### Implementazione

Implementare un interfaccia significa creare una classe che implementa i metodi (astratti) contenuto dall'interfaccia.

#### Esempio

```java
public class Cerchio implements FormaGeometrica
{
	private doubole raggio;

	private Cerchio (double raggio)
	{
		this.raggio = raggio;
	}

	@Override
	public double area()
	{
		return PI * raggio * raggio;
	}

	@Override
	public double perimetro()
	{
		return 2 * PI * raggio;
	}
}
```

### Metodi di default e statici

Le interfacce possono anche contenere metodi di default e statici che possono essere implementati direttamente nell'interfaccia stessa.

>[!info] 
>- I metodi statici possono essere chiamati utilizzando il nome dell'interfaccia seguito dal nome del metodo;
>- I metodi di default danno libertà a chi implementa l'interfaccia di scegliere se sovrascrivere il metodo di default o utilizzare l'implementazione predefinita.

#### Esempio

```java
public interface FormaGeometrica
{
	double PI = 3.14;

	default double areaCirconferenza (double raggio)
	{
		return PI * raggio * raggio;
	}

	static double areaQuadrato (double lato)
	{
		return lato * lato;
	}

	double area();
	double perimetro();
}
```

### Estendibilità

Le interfacce possono estendere altre interfacce, consentendo la creazione di gerarchie di interfacce. 
Una classe che implementa un’interfaccia estesa deve fornire implementazioni per tutti i metodi definiti nelle interfacce padre.

### Interfacce funzionali

Le interfacce funzionali sono un tipo speciale di interfacce che hanno un solo metodo astratto, che può essere implementato come una funzione lambda. Queste interfacce sono anche note come interfacce a singolo metodo o SAM (Single Abstract Method) interfaces.

Le interfacce funzionali sono state introdotte per semplificare l’uso delle funzioni lambda in Java, che sono blocchi di codice anonimi che possono essere passati come argomenti a metodi o assegnati a variabili. Le funzioni lambda possono essere utilizzate per creare oggetti che implementano interfacce funzionali, il che può semplificare il codice e renderlo più conciso ed espressivo.

### Classi astratte

