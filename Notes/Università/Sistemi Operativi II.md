
### Shell in Linux

>[!info] Cos'è lo shell?
>E' un interprete di comandi e spesso viene chiamato anche *terminale*.

**bash**
Scrive un prompt che attende che l'utente scriva un comando.

#### Sintassi comandi

Ogni comando verrà indicato così:

```
comando [opzioni] argomentiobbligatori
```

Ci deve essere almeno 1 argomento se `{argomento}`

```
cp [-r] [-i] [-a] [-u] {filesorgenti} filedestinazione
```

Ci possono essere 0,1 o più argomenti opzionali se `[opzione]`

```
ps [opzioni] [pid...]
```

Gli argomenti vanno separati da carattere indicato se `[carattere opzione...]`

```
chmod mode [, mode...] filename
```

Opzioni tipicamente composte da

```
-carattere (vecchia versione)
--parola (nuova versione)
```

Ad esempio sono equivalenti per il comando `cp`

```
-i -r
--interactive --recursive
```

Le opzioni possono avere un argomento

```
-k1, -k 1, --key=1
```

Le opzioni senza argomento sono raggruppabili

```
-b -r -c e equivalente a -brc
```

Esistono anche le opzioni BSD-style, che sono senza dash

```
tar xfz nomefile.tgz
```


#### Verificare la versione della shell

Si utilizzano tre opzioni:

```
echo
```

```
echo $0
```

```
ps -p "$$" -ocmd -h
```

---

### Filesystem

Il filesystem è un'area di memoria gerarchica strutturata di file e directory
Le directory sono contenitori di file e altre directory, per il sistema sono dei file.

Esistono file regolari e non regolari:
- *regolari*: contengono una sequenza di bit dell'area di memoria sulla quale c'è il filesystem e possono avere caratteri binari o ASCII
- *non regolari o speciali*: link o file che vengono utilizzati per modellare unità di I/O a blocchi/caratteri

La struttura del filesystem in Linux parte con una directory radice (*root*).

```
cd / 
```

In una stessa directory e’ vietato creare
- 2 file con lo stesso nome
- 2 directory con lo stesso nome
- Un file ed una directory con lo stesso nome

#### Path

Ogni file o directory è raggiungibile dalla directory principale `/` mediante un path assoluto.

**Esempio**

```
/home/utente1/dir1/dir11/dir112/file.pdf
```

Il carattere `~` equivale a dire `/home/userX`.

```
~/dir1/dir11/dir112/file.pdf
```

Per conoscere la current working directory (`cwd`) si deve usare il comando

```
pwd
```

- `[Path]` può essere assoluto o relativo
- `cd` senza path ritorna alla home
- Nel path si possono usare `..` (parent directory) `.` directory attuale

>[!warning] Cose mistiche
>- Usando il comando `mkdir namedir` vengono create le directory `~/Immagini`, `~/Immagini/faces` e se le directory già esistono, viene creata `~/Immagini1`

#### Contenuto di una directory

In una directory ci sono file nascosti e tipicamente sono file di configurazione o usati a supporto di comandi e applicazioni.

Per visualizzare i file nascosti si usa il comando:

```
ls [-a | --all]
```

---
## C

#### Funzioni

**Sintassi**
```
<return-type> fn-name (parameter-list)
	{
		declaration of variables
		executable statements
	}
```

`;` viene usato per terminare uno statement

```C
x,y;
x = 0;
x = y + 1;
```

Un blocco può contenere 0 o più statement e i blocchi possono essere innestati.

```C
#include <stdio.h>

/*
Direttiva pre-processore
stdio.h file header –contiene costanti e prototipi funzioni
<> indicano che il file header e’ un file standard del C in
/usr/include
“” indicano che il file header e’ dell’utente e si trova nella
directory corrente o in un path specificato
-I permette di specificare le directory in cui cercare
gli header file
*/

int main() {
	printf(“scrivi quello che vuoi!!!! \n”); // scrive su stdout
	return 0; //indica che il programma ha terminato con
		successo//
}
```

Per compilare ed eseguire i programmi (su Linux) si usa:

```
gcc -Wall prog.c
```
Stampa tutti i messaggi di warning

```
gcc -Wall prog-name.c -lm
```

`-lm` va specificato se si includono le librerie matematiche `<math.h>`, per esempio per usare funzione come $\sin, \cos, \log,\dots$

Il risultato è un file eseguibile `a.out`
Per specificare il nome dell'output si usa
```
gcc -Wall prog-name.c -o executable-name.o
```

#### Precompilazione e compilazione

La precompilazione esegue tutte le direttive del compilatore ed elimina tutti i commenti.
La compilazione controlla che la sintassi sia a posto. Per ogni chiamata a funzione, controlla che venga rispettato il corrispettivo header (che quindi deve esistere al momento della chiamata!). 
Crea effettivamente del codice macchina, ma solo per il contenuto delle funzioni.
Ogni chiamata a funzione ha una destinazione simbolica

Per precompilare si usa
```
cpp nome-file.c > nome-file-precompilato.c
```

`>` serve per salvare l'output del primo file nel secondo.

Per compilarlo si usa
```
gcc -c nom-file-precompilato.c -o nome-file.o
```

