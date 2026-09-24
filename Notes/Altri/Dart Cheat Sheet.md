Cheat Sheet su *Dart* per il progetto di AO3.

![[Pasted image 20260924153705.png]]

---
### Variabili

```Dart
void main(List<String> arguments){
	int n = 5;
	double n = 5.5;
	String str = "hello";
	
	print(n);
	print(str);
}
```

>[!note]
>Se una variabile non viene inizializzata, avrà come valore predefinito `null` (come in Java)

Si possono utilizzare anche le parole chiave `var` e `dynamic`

**dynamic**
Il tipo di una variabile viene stabilito a tempo di esecuzione (runtime).

```Dart
dynamic v = 5;
v = "hello";
```

Per fare un test, possiamo scrivere il seguente codice:

```Dart
dynamic v = 5;
print(v.runtimeType); //printa il tipo di dato che abbiamo al momento dell'esecuzione
v = "hello";
print(v.runtimeType);
```

In output si otterrà: 

![[Pasted image 20260924155109.png]]

**var**
Il tipo di dato viene determinato a tempo di compilazione e non può più cambiare.

```Dart
var v = 20; // v è int
x = 10; // nessun errore perché 10 è intero
x = "hello"; // errore di compilazione
```

Infatti:

![[Pasted image 20260924161424.png]]

>[!warning]
>Se una variabile `var` non viene inizializzata, verrà trattata come `dynamic`

**final**
Una variabile `final` può essere inizializzata con un valore a runtime. Può essere assegnata una sola volta e accetta funzioni o metodi eseguiti a runtime.

```Dart
final currentTime = DateTime.now(); // viene calcolato quando il codice va in esecuzione

currentTime = DataTime.now(); //errore perché non si può assegnare nuovamente una variabile final
```

>[!warning]
>`final` blocca solo il riferimento, quindi a una lista posso essere aggiunti elementi.
>```Dart
>final list = [1, 2, 3];
>list.add(4); // la lista diventa [1, 2, 3, 4]
>list = [4, 5]; // non va bene perché con final non è possibile cambiare riferimento
>```
>![[Pasted image 20260924164947.png]]

**const**
Una variabile `const` deve avere un valore fisso e determinabile *prima* che il programma venga avviato (a tempo di compilazione). Quindi, non può accettare valori calcolati a runtime;

```Dart
const pi = 3.14;
const text = "Welcome";

const time = DateTime.now(); // errore di compilazione
```

![[Pasted image 20260924165320.png]]

>[!warning]
>`const` blocca sia il riferimento che il valore, quindi non è consentita alcuna modifica.
>```Dart
>const list = [1, 2, 3];
>list.add(4); // errrore perché la variabile è immutabile
>list = [4, 5]; // non va bene perché con const non è possibile cambiare riferimento
>```
>![[Pasted image 20260924165730.png]]
>
>![[Pasted image 20260924165751.png]]

>[!info]
>In Dart, `const` riutilizza sempre la stessa istanza in memoria ogni volta che viene dichiara con gli stessi valori, quindi si risparmia sulla memoria.
>```Dart
>var a = const [1, 2];
>var b = const [1, 2];
>print(identical(a, b)); // ritorna true se puntano alla stessa area di memoria
>```
>![[Pasted image 20260924170152.png]]
>
>In Flutter è molto utile quando viene messo davanti ai `Widget` (per esempio `const Text('Ciao')`). In questo modo il motore grafico non ridisegna o ricrea quel widget se non è mai cambiato.

**nullable e non-nullable**

Prima di *Dart 2.12* e *Flutter 2*, tutte le variabili potevano contenere `null` di default. 
Questo provocava frequenti errori a tempo di esecuzione (_runtime crashes_) quando si tentava di accedere a metodi o proprietà di un oggetto che in realtà era `null`.

Con l'introduzione della *Sound Null Safety*, il sistema di tipi di Dart è diventato *non-nullable* di default. Ciò significa che il compilatore garantisce a tempo di compilazione che una variabile standard non possa mai contenere il valore `null`.

![[Pasted image 20260924172443.png]]

Poiché nella logica di un'applicazione è frequente dover gestire informazioni opzionali, Dart introduce l'operatore `?` per rendere il tipo *nullable*, indicando al compilatore che l'assenza di un valore `null` è un comportamento valido e previsto.

```Dart
int? prova;
print(prova); // il programma non darà più errore perché prova può essere null
```

#### Overview principali dati built-in




---

