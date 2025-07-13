### Cosa sono

Sono un modo per rendere il codice più flessibile e riutilizzabile.
Invece di scrivere un codice che funziona solo con un tipo specifico, si può scrivere un codice che funziona con qualsiasi tipo di dato, ma mantenendo comunque la sicurezza dei tipi.

I tipi generici sono come una variabile per i tipi di dato. Invece di specificare esattamente quale tipo di dato verrà utilizzato.

#### Esempio

```Java
class Scatola  <T>
{
	private T oggetto;

	public void setOggettp(T oggetto)
	{
		this.oggetto = oggetto;
	}

	public T getOggetto()
	{
		return oggetto;
	}
}
```

`<T>` è la dichiarazione del tipo generico ed è un segnaposto per qualsiasi tipo di oggetto.

### Perché si usano i tipi generici?

1. Riutilizzo del codice: non bisogna scrivere classi o metodi separati per ogni tipo du dato. Si può scrivere uno solo e riutilizzarlo per più tipi.

2. Sicurezza dei tipi: Java controlla che i tipi siano corretti. Per esempio, se si ha `Scatola<String>`, non ti permette di inserire un Integer per errore.

3. Eliminazione del casting: non bisogna fare conversioni manuali di tipo quando si prendono gli oggetti. Con i generici, Java sa già quale tipo di dato si sta usando.

#### Altri esempi

```Java
List<String> listaDiStringhe = new ArrayList<>();
listaDiStringhe.add("Ciao");
String parola = listaDiStringhe.get(0);  // Non serve fare un cast
```

`List<String>` indica che la lista contiene solo oggetti di tipo **String**. Questo evita errori e non c'è bisogno di fare il cast da **Object** a **String** quando si ottiene un elemento dalla lista.

```Java
Map<String, Integer> dizionario = new HashMap<>();
dizionario.put("Uno", 1);
dizionario.put("Due", 2);
```

In questo caso, la mappa collega una **String** a un **Integer**. Per esempio `"Uno"` è associato al valore `1`.

