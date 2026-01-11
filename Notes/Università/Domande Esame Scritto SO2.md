>[!note] Domanda Numero 1 🟢
>
>Il seguente comando copia da `filein` a `fileout` 100 byte intervallati di 10 byte, ovvero byte_1, byte_11, byte_21, etc...
>
>```bash
>dd if=filein of=fileout bs=1 seek=10 count=100
>```
> 
> Scegli un'alternativa:
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:**
>>- `bs=1` indica che utilizzerà blocchi con dimensione da 1byte
>>- `seek=10` indica che salterà i primi `10` blocchi (10byte) del file in input (`filein`)
>>- `count=100` indica che inserirà nel file in output `fileout` soltanto `100` blocchi (100byte)

>[!note] Domanda Numero 2 🟢
>
>Supponiamo di avere una directory `/home/dir` creata da root con permessi di accesso `0777/drwxrwxrwx` *(owner root)* ed al suo interno il file `filename`, creato da `root`, con permessi di accesso `0770/-rwxrwx---` *(owner root)*.
>
>Un qualsiasi utente può rimovere il file `filename` eseguendo, in user mode, il comando `rm /home/dir/filename`
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>**Motivazione:**
>>- La directory `/home/dir` ha permessi `0777` → tutti (owner, gruppo, altri) hanno *lettura, scrittura e attraversamento (esecuzione)*.
>>- Il file `/home/dir/filename` ha permessi `0770` ed è di proprietà di root → solo root e il suo gruppo possono leggerlo, scriverlo o eseguirlo.
>>- Quindi il file si trova ***dentro una directory scrivibile da tutti***.
>>  
>>In Linux, il permesso di cancellare un file non dipende dai permessi del file stesso, ma dai permessi sulla directory che lo contiene.
>>
>>Un utente per cancella un file nella directory, deve avere *sulla directory*:
>>- permesso di scrittura (`w`) → per modificare il contenuto della directory (aggiungere/rimuovere file)
>>- permesso di esecuzione (`x`) → per attraversarla (navigare dentro)
>>
>>In questo caso:
>>- `/home/dir` ha permessi `drwxrwxrwx` (ovvero `777`)
>>- Tutti gli utenti hanno `rwx` (lettura, scrittura, esecuzione)
>>
>>Quindi un qualsiasi utente può cancellare un file all'interno di `/home/dir`, indipendentemente dai permessi del file.
>>
>>**Come impedire la cancellazione:**
>>- un opzione è rimuovere il permesso di **scrittura** per "others" sulla directory, cambiando i permessi in `drwxrwxr-x`, ma facendo ciò non sarebbe più possible creare nuovi file nella cartella (per un utente qualsiasi)
>>- un altra opzione è rimuovere il diretto di **esecuzione** per "others" sulla directory, cambiando i permessi in `drwxrwxrw-`, ma facendo ciò non sarebbe più possibile attraversare la directory (per un utente qualsiasi)
>>
>>Dato che nessuno di queste due soluzione è perfetta è stato introdotto lo **sticky bit (t)** che se applicato su una directory (permessi = `drwxrwxrwt`) obbliga l'utente ad avere i permessi di scrittura sul file per cancellarlo.

>[!note] Domanda Numero 3 🟢
>
>Si consideri il comando `ln -s myfile mylink`. Dopo la sua esecuzione, l'output dei comandi `du myfile` e `du mylink` sarà diverso.
>
>- [ ] Falso
>- [x] Vero
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:**
>>
>>Quando si esegue il comando `ln -s myfile mylink`, si crea un collegamento simbolico chiamato `mylink` che punta a `myfile`.
>>
>>- Il comando `du myfile` restituirà la dimensione effettiva del file `myfile`.
>>- Il comando `du mylink` restituirà generalmente un output di **0** byte, poiché il collegamento simbolico non occupa spazio significativo.
>>
>>Quindi, l'output di `du myfile` e `du mylink` sarà diverso.

>[!note] Domanda Numero 4 🟢
>
>Il comando `ls -r mydir` lista il contenuto di tutte le directory con radice `mydir`.
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** la flag `-r` (o `--reverse`) fa sì che l'output venga mostrato in ordine inverso, non che si elenchino tutte le directory a partire da `mydir`.
>>
>>Per listare il contenuto di tutte le directory con radice `mydir` (ricorsivamente) si deve utilizzare la flag `-R`.

>[!note] Domanda Numero 5 🟢
>
>Nel comando `# cd ~/Lezione1/esempi/filesystem` è stato utilizzato un path relativo:
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** il simbolo `~` rappresenta la home directory dell'utente attuale , quindi il percorso specificato è un **path assoluto**. I percorsi relativi non iniziano con `/` o `~`, ma sono basati sulla posizione attuale all'interno del filesystem.

>[!note] Domanda Numero 6 🟢
>
>Per visualizzare l'atime di un file quale dei seguenti comandi è corretto?
>
>- [x] `ls -lu nomefile`
>- [ ] `ls -lc nomefile`
>- [ ] `ls -la nomefile`
>
>>[!done]- Risposta
>>```
>>ls -lu nomefile
>>```
>>
>>---
>>
>>**Motivazione:**
>>- `-a` mostra anche gli elementi nascosti (ovvero il cui nome inizia con `.`)
>>- `-l` mostra le informazioni estese (long)
>>- `-u` ordina l'output per `atime` (ma non lo mostra)
>>- `-lu`, la flag `u` se unita a `-l` ovvero `-lu` mostrato come orario l'*atime*, ma ordina per nome
>>- `-c` ordina output per *ctime* (change time)
>>- `-lc`, la flag `c` se unita a `-l` ovvero `-lc` mostrato come orario il *ctime*, ma ordina per nome
>>
>>Queste cose non vanno imparate a memoria, basta vedere il `man ls`

>[!note] Domanda Numero 7 🟢
>
>Per visualizzare la lista dei file presenti nella CWD ordinati per modified time si utilizza il comando:
>
>- [x] `ls -lt`
>- [ ] `ls -lut`
>- [ ] `ls -la`
>
>>[!done]- Risposta
>>
>>`ls -lt`
>>
>>---
>>
>>**Motivazione:**
>>- `-a` mostra anche gli elementi nascosti (ovvero il cui nome inizia con `.`)
>>- `-l` mostra le informazioni estese (long)
>>- `-lt` l'output esteso ordinato per `mtime` (modified time)
>>- `-u` ordina output per l'_atime_ (access time)
>>- `-lu`, la flag `-u` se unita a `-l` ovvero `-lu` mostrato come orario l'*atime*, ma ordina per nome
>>- `-lut`, la flag `-lu` se unita a `-t` ovvero `-lut` mostrato come orario l'*atime* ed ordina per *atime*
>>- `-c` ordina output per _ctime_ (change time)
>>- `-lc`, la flag `-c` se unita a `-l` ovvero `-lc` mostrato come orario il *ctime*, ma ordina per nome
>>- `-lct`, la flag `-lc` se unita a `-t` ovvero `-lct` mostrato come orario il *ctime* ed ordina per *ctime*
>>  
>>Queste cose non vanno imparate a memoria, basta vedere il `man ls` 

>[!note] Domanda Numero 8 🟢
>
>Si supponga di avere un file di testo `filein` contenente *abcdefghilmnopqrstuvwxyzABCDEFGHILMNOPQRSTUVWXYZ* dopo l'esecuzione del comando `dd if=filein of=fileout bs=2 skip=3 count=10` cosa conterrà `fileout`?
>
>- [x] *ghilmnopqrstuvwxyzAB*
>- [ ] *ghilmnopqrstuvwxyzABCDEFGHILMN*
>- [ ] *GHILMNOPQRSTUVWXYZ*
>
>>[!done]- Risposta
>>
>>`ghilmnopqrstuvwxyzAB`
>>
>>**Motivazione:**
>>- `if=filein`: specifica il file di input (`filein`)
>>- `of=fileout`: specifica il file di output (`fileout`)
>>- `bs=2`: imposta la dimensione del blocco a 2 byte
>>- `skip=3`: salta i primi 3 blocchi di input, quindi 3 * 2 = 6 byte (ovvero salta `abcdef`)
>>- `count=10`: copia 10 blocchi (10 * 2 = 20 byte) dopo i byte saltati (ovvero copia *ghilmnopqrstuvwxyzAB*)
>>  
>>Pertanto, `fileout` conterrà *ghilmnopqrstuvwxyzAB*

>[!note] Domanda Numero 9 🟢
>
>Il comando `ls -ltc` restituisce la lista dei file nella CWD ordinati per `atime`.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione:** il comando `ls -ltc` restituisce la lista dei file nella directory corrente (CWD) ordinati per **ctime** ovvero la data di modifica dei metadati del file, non per **atime** (data di accesso).

>[!note] Domanda Numero 10 🟢
>
>Sia `nomefile` un file memorizzato nella CWD, il comando `touch nomefile` crea un file vuoto che sostituisce il file esistente.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** `touch nomefile` va ad aggiornare l'access time di nome file non lo sostituisce. L'unico caso in cui `touch nomefile` crea un file vuoto è quando `nomefile` non esiste.

>[!note] Domanda Numero 11
>
>Il valore *totale 1512* del seguente codice rappresenta la dimensione della directory in numero di blocchi su disco:
>
>```bash
>studente@debian9 :~ $ ls -l apache-tomcat-8.0.27/ 
>totale 1512 
>drwxr-xr-x 2 studente studente
>```
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero

>[!note] Domanda Numero 12 🟢
>
>Un utente che appartiene al gruppo `sudo` può direttamente accedere, in scrittura, al file `/etc/passwd`.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione:** per accedere deve comunque utilizzare il comando `sudo`

>[!note] Domanda Numero 13
>
>Entrambi i path che seguono sono path assoluti per l'utente studente:
>
>```bash
>studente@debian9:~$ /home/studente/dir1/dir2 
>studente@debian9:~$ ~/dir1/dir2/
>```
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero

>[!note] Domanda Numero 14 🟢
>
>Consideriamo il file eseguibile `myProgram` con proprietario `utente1` e con permessi di accesso `-rwxr-xr-x`, se `utente2` esegue `myProgram` si osserva che il `RUID == EUID`.
>
>- [ ] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:** 
>>- `RUID` (Real User ID) è l'in dell'utente che ha eseguito il programma
>>- `EUID` (Effective User ID) rappresenta l'ID dell'utente con i permessi effettivi del processo
>>  
>>Gli unici casi in cui `RUID != EUID` è quando:
>>- il programma è stato eseguito con sudo, quindi `RUID` è l'id dell'utente che ha eseguito il programma e `EUID` è l'id dell'utente *root*
>>- il programma ha nei permessi i bit `setuid` o `setgid` attivi, in questo caso il `EUID` sarebbe stato dell'utente/gruppo proprietario del file eseguibile
>>
>>In questo caso non è stato utilizzato `sudo` e non sono attivi i bit `setuid` o `setgid`, quindi `RUID == EUID`

>[!note] Domanda Numero 15 🟢
>
>Consideriamo il file eseguibile `myProgram` con proprietario `utente1` e con permessi di accesso `-rwsr-xr-x`, se `utente2` esegue `myProgram` si osserva che il `RUID == EUID`.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione** -  i permessi di accesso mostrano che il bit `setuid` è attivo (-rw**s**r-xr-x) quindi quando l'`utente2` esegue il programma:
>>- il `RUID` (Real User ID) sarà uguale all'id del `utente2`
>>- l' `EUID` (Effective User ID) sarà uguale all'id dell'utente proprietario, ovvero l'`utente1`

>[!note] Domanda Numero 16 🟢
>
>Supponiamo di avere una directory `/home/dir` creata da `root` con permessi di accesso `1777/drwxrwxrwt` *(owner root)* ed al suo interno il file `filename`, creato da `root`, con permessi di accesso `0770/-rwxrwx ---` *(owner root)*. 
>
>Un qualsiasi utente può rimovere il file filename eseguendo, in user mode, il comando `rm /home/dir/filename`.
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione:**
>>- la cartella ha lo **sticky bit** attivo (drwxrwxrw**t**) quindi l'unico modo per eliminare il file è avere diritti di scrittura su esso
>>- un utente in *usermode* non ha nessun privilegio sul file, dato che i permessi su esso sono `-rwxrwx ---` e è stato creato da `root`

>[!note] Domanda Numero 17 🟢
>
>I permessi di accesso del file eseguibile `/usr/bin/passwd` sono impostati a `4755/-rwsr-xr-x` per impedire che un qualsiasi utente, operante in usermode, possa eseguire il comando `passwd` e quindi modificare il file `/etc/passwd`.
>
>- [ ] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione:** È vero che file eseguibile `/usr/bin/passwd` ha i permessi impostati ha `4755/-rwsr-xr-x` ma *non è vero che* questo impedisce che un qualsiasi utente, operante in usermode, possa eseguire il comando `passwd` e quindi modificare il file `/etc/passwd`.
>>
>>Infatti in -rwsr-xr-**x** l'ultima `x` da il permesso ad un qualsiasi utente ad eseguire il comando.

>[!note] Domanda Numero 18 🟢
>
>I permessi di accesso del file eseguibile `/usr/bin/passwd` sono impostati a `1755/-rwxr-xr-t` per consentire ad un qualsiasi utente, operante in usermode, di eseguire il comando `passwd` e quindi modificare il file `/etc/passwd`.
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione:** é vero che i permessi `1755/-rwxr-xr-t` permettono ad un qualsiasi utente di eseguire il comando, ma in realtà il file `/usr/bin/passwd` ha come permessi `4755/-rwxr-xr-x` e non `1755/-rwxr-xr-t`.
>>
>>Infatti lo *sticky bit (t)* è inutile quando utilizzato su un file quindi il comportamento di `4755/-rwxr-xr-x` è equivalente a `1755/-rwxr-xr-t`.

>[!note] Domanda Numero 19 🟢
>
>Il comando `chmod 6774 nomefile` imposta i permessi di `nomefile` a `- rwS rwS r--`.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>**Motivazione** - il comando `chmod 6774` imposta i permessi a `-rwsrwsr--` non a `-rwSrwSr--`, infatti:
>>- abbiamo `s` (piccolo) sull'utente quando è attivo sia `setuid` sia l'esecuzione `x`
>>- abbiamo `S` (grande) sull'utente quando è attivo l'`setuid` ma non l'esecuzione `x`
>>  
>>>ragionamento analogo per la sezione gruppo

>[!note] Domanda Numero 20 🟢
>
>Il comando `sudo adduser utente1 studente` genera un errore se il gruppo `studente` esiste ma l'utente `utente1` non esiste.
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:** Se `utente1` non esiste, il comando genererà un errore, poiché `adduser` cerca di aggiungere un utente a un gruppo, ma non può farlo se l'utente non è stato creato.
>>
>>Se dovesse esistere l'utente ma non il gruppo verrebbe comunque generato un errore.
>>
>>L'unico caso in cui l'operazione va a buon fine è se esistono sia l'utente che il gruppo.

>[!note] Domanda Numero 21 🟢
>
>Il comando `touch -cat202006021200 filename` imposta l'`atime` ed il `ctime` di `filename` al '2 giugno 2020 ore 12:00'.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** il comando non ha senso, il comando coretto è `touch -t 202006021200 filename`
>>
>>---
>>
>>**Sessione pratica:** eseguiamo il comando `touch -cat202006021200 filename` e non avviene nessun cambiamento (controlla utilizzando `ls -lu filename` e `ls -lc filename`)
>>
>>Invece se eseguiamo il comando `touch -t 202006021200 filename` e poi eseguiamo i comandi `ls -lu filename` e `ls -lc filename` otteniamo come output:
>>
>>```
>>-rw-r--r-- 1 501 dialout 0 Jun  2  2020 filename
>>```

>[!note] Domanda Numero 22 🟢
>
>Il comando `ls -R mydir` lista il contenuto di tutte le directory con radice `mydir`.
>
>- [ ] Falso
>- [x] Vero
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:** la flag `-R` sta per *recursive* quindi effettua `ls` ricorsivamente su tutte le directory contenute in `mydir`.

>[!note] Domanda Numero 23 🟢
>
>Si assuma di avere due shell aperte, etichettate come shell_1 e shell_2 e si consideri la seguente sequenza di comandi (shell_i:cmd indica che cmd e' eseguito nella shell i, i=1,2) eseguiti in usermode. Quale è il loro effetto?
>
>```bash
>shell_1: xterm
>shell_2: ps -C xterm 
>#restituisce xtermPID
>shell 2: kill -s SIGINT xtermPID
>```
>
>- [ ] Il processo xterm viene portato nello stato Interrupted (`I`)
>- [ ] Nulla. Un segnale di SIGINT inviato in usermode non viene considerato dal processo che lo riceve.
>- [ ] Il processo xterm viene terminato con segnale SIGINT
>
>>[!done]- Risposta
>>
>>Il processo xterm viene terminato con segnale SIGINT
>>
>>---
>>
>>**Motivazione:** Quando un processo riceve il segnale `SIGINT` viene terminato ovvero viene cancellata la sua esecuzione (se facciamo `ps -e` non sarà più possibile trovarlo). 
>>
>>>***Note:***
>>>- Lo stato `I` non esiste
>>>- `SIGINT` equivale al segnale `SIGKILL`
>>>- `SIGINT` e `SIGKILL` sono i segnale che vengono mandati al processo running sulla shell quando premiamo i tasti `ctrl + c`.
>>
>>Per maggiori informazioni sugli stati di un processo vedi [[Processi in linux#^88b0db|Processi in linux - stati]] per maggiori informazioni su `kill` vedi [[Comandi linux per gestione processi#^ff47ab|Comandi linux per gestione processi - kill]]

>[!note] Domanda Numero 24 🟢
>
>Si assuma di avere due shell aperte, etichettate come shell_1 e shell_2 e si consideri la seguente sequenza di comandi (shell_i:cmd indica che cmd è eseguito nella shell i, i=1,2) eseguiti in usermode. Quale è il loro effetto?
>
>```bash
>shell_1: xterm
>shell_2: ps -C xterm
>#restituisce xtermPID
>shell 2: kill -s SIGSTOP xtermPID
>```
>
>- [x] Il processo xterm viene messo nello stato `T`
>- [ ] Nulla. In usermode l'invio di un segnale di `SIGSTOP` ad un processo non ha effetto
>- [ ] Il processo xterm viene mandato in esecuzione in background
>
>>[!done]- Risposta
>>
>>Il processo xterm viene messo nello stato `T`
>>
>>---
>>
>>**Motivazione:** quando un processo riceve il segnale `SIGINT` viene terminato ovvero va nello stato `T` (stopped)
>>
>>Per maggiori informazioni sugli stati di un processo vedi [[Processi in linux#^88b0db|Processi in linux - stati]] per maggiori informazioni su `kill` vedi [[Comandi linux per gestione processi#^ff47ab|Comandi linux per gestione processi - kill]]

>[!note] Domanda Numero 25 🟢
>
>Per conoscere lo stato di un job in esecuzione si deve utilizzare il comando:
>
>```bash
>~$ jobs -p
>```
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** il comando `jobs -p` ritorna il PID dei processi in esecuzione sulla corrente shell

>[!note] Domanda Numero 26 🟢
>
>Il comando
>
>```bash
>sudo adduser --home=/home/testdir --no-create-home usertest
>```
>
>- [x] Crea l'utente `usertes`t ma genera dati inconsistenti nel file `/etc/passwd`
>- [ ] Genera un errore
>- [ ] Crea l'utente `usertest` e la directory `/home/usertest` assegnandola come home directory all'utente
>
>>[!done]- Risposta
>>
>>Crea l'utente `usertest` ma genera dati inconsistenti nel file `/etc/passwd`
>>
>>---
>>
>>**Motivazione:**
>>
>>Questo comando specifica il percorso della home directory del nuovo utente(`/home/testdir`), ma ha anche l'opzione `--no-create-home` di conseguenza:
>>- viene creato l'utente `usertest` inserendo in `/etc/passwd` una riga contenete le informazione dell'utente tra cui la sua home directory che viene assegnata a `/home/testdir`
>>- ma "per colpa" di `--no-create-home` non viene create la directory `/home/testdir` vera e propria nel file system
>>  
>>L'unico caso in cui questo comando non da problemi è se la cartella `/home/testdir` fosse già esistente
>>
>>**Prova Pratica:**
>>
>>Dopo aver eseguito il comando `sudo adduser --home=/home/testdir --no-create-home usertest`, l'output di `cat /etc/testdir` è:
>>
>>```txt
>>root:x:0:0:root:/root:/bin/bash
>>myuser:x:1000:1000::/home/myuser:/bin/bash
>>usertest:x:1001:1001:,,,:/home/testdir:/bin/bash
>>```

>[!note] Domanda Numero 27 🟢
>
>I seguenti segnali possono essere catturati e gestiti da un programma c eseguito in usermode
>
>```bash
>SIGINT
SIGABRT
SIGTERM
>```
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero

>[!note] Domanda Numero 28 🟢
>
>I seguenti segnali non possono essere catturati e gestiti da un programma c eseguito in usermode
>
>```bash
>SIGKILL
>SIGINT
>SIGABRT
>```
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso

>[!note] Domanda Numero 29 🟢
>
>I comandi `~$ sudo -u usertest` e `~$ su -l usertest` sono equivalenti
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Morivazione:**
>>
>>|   |   |
>>|---|---|
>>|`sudo -u usertest`|Esegue un comando come l'utente `usertest` senza cambiare la shell corrente. Può essere usato per eseguire un comando specifico come quell'utente, ed è necessario che l'utente attuale abbia i permessi di sudo per farlo. In oltre richiede la password dell'utente che ha eseguito il comando|
>>|`su -l usertest`|Cambia l'utente attivo a `usertest`, caricando l'ambiente dell'utente (incluso il path e le variabili di ambiente) come se l'utente avesse effettuato il login. Questo comando richiede la password dell'utente `usertest`.|

>[!note] Domanda Numero 30 🟢
>
>I seguenti comandi producono lo stesso risultato
>
>```bash
>dd if=filein of=fileout bs=100 count=1
>dd if=filein of=fileout bs=1 count=100
>```
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione** - entrambi copiano i primi 100byte di `filein` in `fileout`, infatti:
>>- il primo copia un solo blocco da 100byte ($1 \cdot 100\text{byte} = 100\text{byte}$ )
>>- il secondo copia 100 blocchi da un 1byte ($100 \cdot 1\text{byte} = 100\text{byte}$)

>[!note] Domanda Numero 31 🟢
>
>Supponiamo di avere un file di nome filename e di eseguire il comando `ln filename link1` i file `filename` e `link1` hanno inode diversi.
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** `ln filename link1` crea un hard link tra `filename` e `link1` di conseguenza condividono l'inode.
>>
>>---
>>
>>**Prova Pratica:**
>>
>>Eseguo i comandi `touch filename` (pre creare il file `filename`) e poi `ln filename link1` per creare l'hard link tra `filename` e `link1`.
>>
>>Ora eseguendo il comando `stat filename`, ottengo in output:
>>
>>```
>>File: filename
>> Size: 0               Blocks: 0          IO Block: 4096   regular empty file
>>Device: 31h/49d Inode: 62          Links: 1
>>Access: (0644/-rw-r--r--)  Uid: (  501/ UNKNOWN)   Gid: (   20/ dialout)
>>Access: 2025-10-06 15:23:45.000000000 +0000
>>Modify: 2025-10-06 15:23:45.000000000 +0000
>>Change: 2025-10-06 15:23:45.000000000 +0000
>>Birth: -
>>```
>>
>>Ora eseguendo il comando `stat filename`, ottengo in output:
>>
>>```
>>File: link1
>>Size: 0               Blocks: 0          IO Block: 4096   regular empty file
>>Device: 31h/49d Inode: 62          Links: 1
>>Access: (0644/-rw-r--r--)  Uid: (  501/ UNKNOWN)   Gid: (   20/ dialout)
>>Access: 2025-10-06 15:23:45.000000000 +0000
>>Modify: 2025-10-06 15:23:45.000000000 +0000
>>Change: 2025-10-06 15:23:45.000000000 +0000
>>Birth: -
>>```
>>
>>Possiamo vedere che entrambi hanno lo stesso Inode (62)

>[!note] Domanda Numero 32 🟢
>
>Si consideri il comando `ln -s myfile mylink`. Dopo la sua esecuzione, `myfile` e `mylink` avranno un diverso inode.
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero
>>
>>**Motivazione:** `ls -s` crea un *soft*  link, che ha differenza del hard *link* non punta direttamente all’inode del file originale.

>[!note] Domanda Numero 33
>
>Il comando `chmod 6774 nomefile` imposta i seguenti permessi per il file `nomefile` `-rwsrwsr--`.
>
>- [ ] Falso
>- [x] Vero
>
>>[!done]- Risposta
>>
>>Vero

>[!note] Domanda Numero 34 🟢
>
>Assuma di avere due shell aperte, etichettate come shell_1 e shell_2 e supponga di eseguire, in usemode, la sequenza di comandi che segue (shell_i: cmd indica che cmd è eseguito nella shell_i, i=1,2). Quale è il loro effetto sul processo xterm?
>
>```bash
>shell_1: sleep 300
>shell_2: ps -C sleep
>#restituisce sleepPID
>shell_2: kill -s SIGSTOP sleepPID
>shell_2: kill -s SIGCONT sleepPID
>```
>
>- [ ] Il processo sleep viene prima portato nello stato `T` e poi mandato nuovamente in esecuzione in foreground
>- [x] Il processo sleep viene mandato in esecuzione in background
>- [ ] Nessuno. In usermode i processi ignorano il segnale di `SIGSTOP`. L'invio del segnale `SIGCONT` quindi non modifica lo stato del processo
>
>>[!done]- Risposta
>>
>>Il processo sleep viene mandato in esecuzione in background
>>
>>---
>>
>>**Motivazione:**
>>- il segnale `SINGSTOP` manda il processo nello stato `T` (stopped)
>>- il segnale `SIGCONT` manda il processo in esecuzione in background

>[!note] Domanda Numero 35 🟢
>
>Il comando `~$ sleep 30 | sleep 15 | sleep 10 &` crea 1 job in background
>
>- [ ] Falso
>- [x] Vero
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:** Quando si utilizza l'operatore pipeline (`|`) questo crea un unico job che contiene tutti i comandi specificati e l’operatore ampersand (`&`) lo manda in background.
>>
>>**Test Pratico:** Eseguiamo il comando `sleep 30 | sleep 15 | sleep 10 &`, ora se eseguiamo il comando `jobs` per vedere i job in esecuzione sulla shell otteniamo in output:
>>
>>```
>>[1]  + running    sleep 30 | sleep 15 | sleep 10
>>```
>>
>>Se dopo 10 secondi dall'inizio del job eseguiamo `jobs` otteniamo:
>>
>>```
>>[1]  + running    sleep 30 | sleep 15 |
>>        done       sleep 10
>>```
>>
>>Se dopo 15 secondi dall'inizio del job eseguiamo `jobs` otteniamo:
>>
>>```
>>[1]  + running    sleep 30 |
>>        done       sleep 15 | sleep 10
>>```
>>
>>Se dopo 30 secondi dall'inizio del job eseguiamo `jobs` otteniamo:
>>
>>```
>>[1]  + 407 done       sleep 30 |
>>        408 done       sleep 15 |
>>        409 done       sleep 10
>>```

>[!note] Domanda Numero 36 🟢
>
>La directory `/tmp` ha i permessi di accesso impostati a `1777/drwxrwxrwt` per consentire a tutti gli utenti di leggere, creare e rimuovere file anche se non hanno permessi di scrittura su di essi.
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** è vero che `\tmp` ha come permessi `1777/drwxrwxrwt` ma non è vero che questi permessi permettono a tutti di rimuovere i file dalla cartella, dato che lo sticky bit è attivo (drwxrwxrw**t**) questo obbliga ad avere i diretti di scrittura sul file per eliminarlo.

>[!note] Domanda Numero 37 🟢
>
>Consideriamo il file eseguibile `myProgram` con proprietario `utente1` e con permessi di accesso `-rwxr-xr-x`. Se `utente2` esegue myProgram si osserva che il RUID è diverso dal EUID
>
>- [x] Falso
>- [ ] Vero
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** il `RUID` e il `EUID` di un processo sono sempre uguali tranne nei casi in cui:
>>- il programma è eseguito con sudo
>>- il fil eseguibile ha i bit `setuid` o `setgid` attivi
>>  
>>In questo caso `myProgram` non viene eseguito con `sudo` e non ha i bit `setuid` o `setgid` attivi, quando `RUID == EUID`.

>[!note] Domanda Numero 38
>
>Supponiamo di avere una directory `/home/dir` creata da root con permessi di accesso `1777/drwxrwxrwt` *(owner root)* ed al suo interno il file `filename`, creato da `root`, con permessi di accesso `0770/-rwxrwx---` *(owner root)*. Un qualsiasi utente può rimovere il file `filename` eseguendo, in user mode, il comando rm /home/dir/filename
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:**
>>- Dato che la directory `/home/dir` ha lo *sticky bit* (`t`) attivo se un utente vuole modificare in file deve avere i diritti di esecuzione du di esso.
>>- Dato che i permessi del file `filename` sono impostati ha `-rwxrwx---` solo l'utente proprietario o gli utenti che fanno parte degli stessi gruppi dell'utente proprietario hanno diritto di esecuzione sul file.
>>  
>>Di conseguenza un utente qualsiasi non ha diritto di esecuzione sul file e quindi non può eliminarlo.

>[!note] Domanda Numero 39 🟢
>
>Per eseguire con successo il comando `studente@hostname~$ sudo -u usertest stat file_di_usertest` quale password deve essere fornita?
>
>- [ ] La password dell'utente `usertest`
>- [x] La password dell'utente `studente`
>- [ ] La password di `root`
>
>>[!done]- Risposta
>>
>>La password dell'utente studente
>>
>>---
>>
>>**Motivazione:**
>>
>>Il comando `sudo` richiede la password dell'utente che sta eseguendo il comando che in questo caso è `studente`
>>  
>>Infatti l'header dello shell (`studente@hostname~$`) mostra che l'utente è studente

>[!note] Domanda Numero 40 🟢
>
>Il comando `adduser utente1` e poi `adduser utente1 studente` , dopo aver creato l'utente `utente1`, genera errore nell'esecuzione del secondo comando in quanto `utente1` esiste già.
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>Se faccio `adduser utente1 studente` non genera un errore perché l'utente `utente1` esiste già, infatti questo comando prova ad aggiungere l'utente `utente1` al gruppo `studente`.
>>
>>Gli unici casi in cui questo comando genera un errore è quando l' utente `utente1` non esiste, o quando il gruppo `studente` non esiste.

>[!note] Domanda Numero 41 🟢
>
>Dopo l'esecuzione del comando `ln filename link1`, il comando `stat filename` e `stat link1` avranno output uguale a meno del campo "File".
>
>- [x] Vero
>- [ ] Falso
>
>>[!done]- Risposta
>>
>>Vero
>>
>>---
>>
>>**Motivazione:** eseguendo `ln filename link1` andiamo a creare un nuovo file (`link1`) che è un hard link a `filename`, di conseguenza abbiamo che `link1` punta allo steso *inode* di `filename`, per questo condividono tutte le informazioni tranne il nome del file.
>>
>>**Prova Pratica:**
>>
>>Eseguo i comandi `touch filename` (pre creare il file `filename`) e poi `ln filename link1` per creare l'hard link tra `filename` e `link1`.
>>
>>Ora eseguendo il comando `stat filename`, ottengo in output:
>>
>>```
>>File: filename
>> Size: 0               Blocks: 0          IO Block: 4096   regular empty file
>>Device: 31h/49d Inode: 62          Links: 1
>>Access: (0644/-rw-r--r--)  Uid: (  501/ UNKNOWN)   Gid: (   20/ dialout)
>>Access: 2025-10-06 15:23:45.000000000 +0000
>>Modify: 2025-10-06 15:23:45.000000000 +0000
>>Change: 2025-10-06 15:23:45.000000000 +0000
>>Birth: -
>>```
>>
>>Ora eseguendo il comando `stat filename`, ottengo in output:
>>
>>```
>>File: link1
>>Size: 0               Blocks: 0          IO Block: 4096   regular empty file
>>Device: 31h/49d Inode: 62          Links: 1
>>Access: (0644/-rw-r--r--)  Uid: (  501/ UNKNOWN)   Gid: (   20/ dialout)
>>Access: 2025-10-06 15:23:45.000000000 +0000
>>Modify: 2025-10-06 15:23:45.000000000 +0000
>>Change: 2025-10-06 15:23:45.000000000 +0000
>>Birth: -
>>```

>[!note] Domanda Numero 42 🟢
>
>Una directory con i permessi di accesso impostati a `rw- --- ---` permette all'utente proprietario della directory di: leggere il contenuto della directory inclusi gli attributi del file; impostare la directory come cwd; attraversare la directory;
>
>- [ ] Vero
>- [x] Falso
>
>>[!done]- Risposta
>>
>>Falso
>>
>>---
>>
>>**Motivazione:** I permessi `rw- --- ---` permettono all'utente proprietario di:
>>- "leggere" la directory (ad esempio utilizzare `ls` su di essa)
>>- "scrivere" sulla directory ovvero creare e rimuovere file dalla directory (ma senza `x` in realtà non è possibile)
>>
>>Non può attraversare la directory quindi non può impostarla come `CWD`