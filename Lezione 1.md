### List comprehension

- E' usato per scrivere le liste in maniera in maniera più compatta
- E' molto efficiente

```python
f = [<exp o val da resituire> for <condizione> if <condizone>]
```

>[!warning] Attenzione
>Se si vuole scrivere l'else nella list comprehension bisogna mettere il for alla fine

##### Ex.
###### Funzione con list comprehension che prende i primi 8 numeri interi e stampa una lista con il valore dei numero se pari o "dispari" se dispari

```python
f= [i if i % 2==0 else "dispari" for i in range (8)]
print (f)
```

---
### Lambda function

- Funzioni "usa e getta" o "anonima"
- Sono funzioni "fatte al volo"
- Può accettare un numero qualsiasi di argomenti, ma può avere solo un'espressione

```python
x = lambda y : <exp>
```

##### Ex.

###### Lambda function che stampa il valore in input + 10

```python
x=lambda a: a+10
print (x(3))
```

---
### Dizionari

- E' una collezione non ordinata di oggetti indirizzati tramite chiavi (invece che per posizione come nelle mappe)
- E' quindi una mappa da chiavi a valori, e i suoi oggetti si recuperano specificandone la chiave corrispondente
- Può essere creato specificandone l’insieme di coppie `chiave:valore` separate da virgole e delimitato da parentesi graffe

```python
d = {key1:val1, key2:val2}
```

>[!info] Metodi più usati
>- `d.get("key")` -> restituisce il valore associato alla chiave
>- `d.keys()` -> restituisce una lista di chiavi del dizionario
>- `d.values()` -> restituisce una lista di valori del dizionario
>- `d.tems()` -> restituisce una lista di tuple con chiavi e valori `[(key1, val1), (key2, val2)]`
>- `d.del()` -> cancella una coppia

##### Ex.

###### Funzione che prende in input la lista precedente e stampa un dizionario che ha come chiave le lettere e come valori il numero di occorrenze (quante volte un numero è contenuto nella lista)

```python
d={}

for i in range (len(lista)):

    for j in lista[i]:
        print (j)
        
        if j not in d:
            d[j]=1
        else:
            d[j]+=1
            
print (d) # stampa il dizionario
print (d["p"]) # stampa il valore associato a p

a= d.get("p") # restiruisce il valore associato a "p"

print (a)
print (d.keys()) # stampa le chiavi del dizionario
print (d.values()) # stampa i valori del dizionario
print (d.items()) # stampa una lista di tuple con chiavi e valori
```

---
