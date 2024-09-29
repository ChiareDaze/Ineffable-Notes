
### Stream

- Sono una sequenza di elementi su cui possono essere effettuate una o più operazioni 
- Vengono creati a partire da una sorgente di dati (per esempio `java.util.Collection`)
- Non memorizzano né modificano i dati della sorgente, ma operano su di essa
- Supportano operazioni sequenziali e parallele

#### Operazioni intermedie e terminali

**Intermedie**: quando restituiscono un altro stream su cui continuare a lavorare.

**Terminali**: quando restituiscono il risultato atteso.

Una volta che uno stream è stato consumato (operazione terminale), non può essere riutilizzato.
##### Operazioni intermedie

- `filter()`: filtra gli elementi in base a una condizione
- `map()`: trasforma gli elementi in base a una funzione
- `sorted()`: ordina gli elementi

##### Operazioni terminali

- `forEach()`: esegue un'azione per ogni elemento dello stream
- `collect()`: Raccoglie gli elementi in una struttura dati (ad esempio una lista).
- `reduce()`: Riduce gli elementi a un singolo risultato, come la somma o la concatenazione.

#### Metodi principali

![[Pasted image 20240911172208.png|500]]

Gli stream hanno un comportamento *pigro* (lazy behaviour), questo significa che le operazioni intermedie non vengono eseguite immediatamente, ma solo quando si richiede l'esecuzione di un'operazione terminale.

Le operazioni possono essere senza stato o con stato.

**Senza stato**: l'elaborazione dei vari elementi può procedere in modo indipendente.

**Con stato**: l'elaborazione di un elemento potrebbe dipendere da quella di altri elementi.


---
#### Come si ottengono

Gli stream possono essere creati a partire da collections, liste, set, int, long, double, array...

![[Pasted image 20240911173657.png|500]]

---
#### Esempi

##### Filtra, moltiplica per 2 e stampa i numeri pari

```Java 
//senza stream
List <Integer> numbers = Array.asList(1,2,3,4,5,6);
for (Integer num : numbers)
{
	if (num % 2 == 0)
	{
		int result = num * 2;
		System.out.println(result);
	}
}
```

```Java
//con stream
List <Integer> numbers = Array.asList(1,2,3,4,5,6);
numbers.stream() //crea lo stream della lista
	.filter(n -> n % 2 == 0) //Filtra: prende solo i numeri pari
	.map(n -> n * 2) //Mappatura: moltiplica per 2
	.forEach(System.out::println); //Operazione terminale: stampa
```