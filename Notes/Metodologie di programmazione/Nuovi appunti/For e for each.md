### Ciclo for

```java
for (inizializzazione; condizione; incremento)
{
	//codice
}
```

#### Esempio

```java
for (int i=0; i<10; i++)
{
	//
}
```

### For each

E' un ciclo for che si utilizza quando è necessario elaborare tutti gli elementi di un array o di una raccolta.

```java
for (type itVar: array)
{
	//Operazioni
}
```

Dove **type** è il tipo della variabile iteratore (corrispondente al tipo di dati degli elementi nell'array!).
**itVar** è il suo nome e **array** è un array, cioè l'oggetto su cui viene eseguito il ciclo.

>[!warning]
>Un ciclo for each può essere applicato agli array e a qualsiasi classe che implementa l'interfaccia `java.lang.Iterable`.

```java
for (int i = 0; i < array.lenght; i++)
{
	//codice
}
```


