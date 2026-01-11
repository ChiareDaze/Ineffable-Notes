
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

---
### Appunti per le domande a crocette

#### dd

>[!info] Come funziona
>Il comando `dd` in Linux serve per la copia e la conversione di dati.
>E' utilizzato per trasferire da un file in input a un file in output.

**Sintassi**

```bash
dd if=<input file> of=<output file> [opzioni]
```

- `if`:  specifica il file di input
- `of`: specifica il file di output

**Opzioni**
- `bs = <size>`:  indica la dimensione dei blocchi che verranno utilizzati
- `count =<number>`: limita la copia a un numero specifico di blocchi
- `seek=<number>`: Specifica il numero di blocchi da saltare nel file di output prima di iniziare la scrittura
- `skeep = <number>`: Indica quanti blocchi di dati saltare dall'inizio del file di input.

#### ln

>[!info] Come funziona
>Il comando **`ln`** viene utilizzato in Linux per creare collegamenti (hard link  e symbolic link) tra file e directory.
>Permette di creare riferimenti a file esistenti, facilitando l'accesso e l'organizzazione dei dati nel filesystem

**Sintassi**

```bash
ln [opzioni] <target> <link_name>
```

- `<target>`: Il file o la directory di origine
- `<link_name>`: Il nome del nuovo collegamento da creare

>[!warning]
>Per distinguere tra symbolic link e hard link si utilizza l'opzione `-s`
>>[!example]
>>*Hard Link*
>>``` bash
>>ln original_file.txt hard_link.txt
>>```
>>*Symbolic Link*
>>```bash
>>ln -s original_file.txt symbolic_link.txt
>>```

**Opzioni**
- **`-s`**: Crea un collegamento simbolico
- **`-f`**: Forza la creazione del collegamento sovrascrivendo eventuali file esistenti con lo stesso nome
- **`-n`**: Non seguire i collegamenti simbolici esistenti

>[!note] Comando `du`
>per controllare l'uso dello spazio su disco di un file e di un collegamento (sia esso hard o simbolico).
>Supponiamo di avere un file chiamato **`myfile`** e un collegamento simbolico **`mylink`** che punta a **`myfile`**. Vediamo cosa restituisce il comando:
>
>*Symbolic Link*
>```bash
>du myfile du mylink
>```
>
>Output:
>- `du myfile`: Mostra la dimensione effettiva di **`myfile`**, ad esempio `4.0K` se il file occupa 4 kilobyte
>- **`du mylink`**: Mostra la dimensione di **`myfile`**, poiché `mylink` punta a **`myfile`**. Quindi, il risultato sarà lo stesso di `du myfile`
>
>*Hard Link*
 >Se **`mylink`** è un collegamento hard a **`myfile`**, il comportamento è simile:
 >```bash
 >`du myfile du mylink`
 >```
 >
>Output:
>- Entrambi i comandi forniranno la stessa dimensione di **`myfile`**.

#### ls

>[!info] Come funziona
>Il comando **`ls`** è utilizzato per elencare i file e le directory presenti in un filesystem. 
>È uno dei comandi più comuni e utili in ambiente Unix/Linux e offre molte opzioni per personalizzare l'output

**Sintassi**

```bash
ls [opzioni] [file|directory...]
```

Se non viene specificato alcun file o directory, `ls` elenca quelli presenti nella directory corrente.

### Opzioni

Ecco un elenco delle opzioni più utili e comuni per il comando **`ls`**:

| Opzione   | Descrizione                                                                                                                    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `-a`      | Mostra tutti i file, inclusi quelli nascosti (che iniziano con `.`)                                                            |
| `-c`      | Ordina output per ctime (change time)                                                                                          |
| `-l`      | Elenca i file in formato lungo, mostrando informazioni come i permessi, il proprietario, la dimensione e la data di modifica   |
| `-h`      | Mostra la dimensione dei file in un formato leggibile (es. KB, MB) con l'opzione `-l`                                          |
| `-R`      | Elenca ricorsivamente tutte le sottodirectory                                                                                  |
| `-t`      | Ordina i file per data di modifica, dal più recente al meno recente                                                            |
| `-S`      | Ordina i file per dimensione, dal più grande al più piccolo                                                                    |
| `-r`      | Inverti l'ordine di sort                                                                                                       |
| `-d`      | Mostra solo le directory, senza elencare i file al loro interno                                                                |
| `-1`      | Mostra un file per riga                                                                                                        |
| `-u`      | Ordina l'output per atime (access time), ma non lo mostra                                                                      |
| `-F`      | Aggiunge un simbolo alla fine dei nomi dei file per indicarne il tipo (ad es. `/` per le directory, `*` per i file eseguibili) |
| `--color` | Abilita la colorazione dell'output per differenti tipi di file                                                                 |
| `-i`      | Mostra il numero di inode di ciascun file                                                                                      |
| `-n`      | Mostra i nomi degli utenti e dei gruppi in formato numerico (ID invece di nomi)                                                |
| `-p`      | Aggiunge un `/` alla fine dei nomi delle directory                                                                             |
| `-Q`      | Riscontra i nomi dei file con virgolette                                                                                       |

>[!warning]
>Non confondere `-r` con `-R`.
>`-r` serve per listare il contenuto della directory in ordine inverso.
>`-R` lista ricorsivamente il contenuto delle directory con radice `mydir`

#### Percorso assoluto e relativo

**Percorso Assoluto**
E' un percorso che specifica la posizione di un file o di una directory a partire dalla radice del filesystem. In Linux, la radice è rappresentata dal simbolo `/`.

>[!info] Caratteristiche
>- *Inizia dalla radice*: Sempre fa riferimento al percorso completo partendo dalla directory principale
>- *Indipendente dalla posizione corrente*: Non importa in quale directory ci si trovi. Il percorso assoluto porterà sempre al file o alla directory specificati

**Percorso Relativo**

E' un percorso che specifica la posizione di un file o di una directory in relazione alla directory corrente in cui ci si trova. Non inizia dalla radice.

>[!info] Caratteristiche
>- *Inizia dalla directory corrente*: È composto da directory e file a partire dalla posizione attuale
>- *Dipendente dalla posizione corrente*: Cambiando la directory attuale, cambia anche il significato del percorso relativo


#### Simbolo `~`

Rappresenta la home directory dell'utente corrente. È un modo conveniente per fare riferimento rapidamente a questa directory senza scriverne il percorso completo.

>[!info] Caratteristiche
>- *Home Directory*: Ogni utente ha una propria home directory, di solito situata in **`/home/nome_utente`**. Ad esempio, se il tuo nome utente è **`user`**, la tua home directory sarà **`/home/user`**.
>- *Rappresentazione*: Usare `~` al posto di scrivere il percorso completo rende i comandi più brevi e più facili da digitare.

- Puoi usare **`cd`** per spostarti nella tua home directory in qualsiasi momento:

```bash
cd ~
```

- Se vuoi accedere a una directory chiamata `documenti` all'interno della tua home directory, puoi usare:

```bash
cd ~/documenti
```

Per vedere i file e le directory presenti nella tua home:

```bash
ls ~
```

Puoi anche usare **`~`** in altri comandi. Ad esempio, per copiare un file dalla home directory a una directory di lavoro:

```bash
cp ~/file.txt /path/to/destination/
```

#### Touch

>[!info] Come funziona
>Viene utilizzato principalmente per due scopi principali:
>- *Creare file vuoti*: Se il file specificato non esiste, `touch` lo crea come file vuoto
>- *Aggiornare la data di accesso e modifica*: Se il file esiste già, il comando aggiorna la data e l'ora della sua ultima modifica e accesso al momento corrente

**Opzioni**

- **`-a`**: Aggiorna solo l'access time
- **`-m`**: Aggiorna solo il modified time
- **`-c`**: Non crea file se non esistono
- **`-t`**: Permette di specificare un timestamp personalizzato nel formato `[[CC]YY]MMDDhhmm[.ss]`