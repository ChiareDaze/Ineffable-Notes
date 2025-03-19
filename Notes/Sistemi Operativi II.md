
### Shell in Linux

>[!info] Cos'è lo shell?
>E' un interprete di comandi e spesso viene chiamato anche *terminale*.

**bash**
Scrive un prompt che attende che l'tente scriva un comando.

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

