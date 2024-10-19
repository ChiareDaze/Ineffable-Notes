 >[!info] Programma
>- Come fa un computer a funzionare?
>- Come l'hardware si interfaccia
>- Gestione dei programmi

---
### Sistema operativo

Il suo scopo principale è quello di offrire servizi agli utenti.
Offre un ambiente di esecuzione facilitato alle applicazioni utente (per esempio permette di usare la ram utilizzando variabili con determinati nomi).
Offre anche un ambiente grafico per l'utente.

Per fare tutto questo il sistema operativo deve comunicare con l'hardware e dare gli opportuni comandi.

Le risorse hardware più importanti sono i processori, la ram e i dispositivi di I/O.

#### Sistema monoprocessore

![[Pasted image 20240924155459.png|300]]

**Modello di Von Neumann**

Composto da tre blocchi che si possono isolare all'interno del computer.
- Processore (CPU)
- RAM
- Moduli di i/o

Questi tre blocchi devono interagire tra loro, quindi c'è un canale di comunicazione chiamato *System Bus*.

All'interno della CPU ci sono delle zone di memoria aggiuntive chiamate *Registri*.
##### Processore

E' il "cervello" del computer ed è quello che si occupa di tutte le computazioni.
Se c'è una computazione fatta dal computer, tipicamente è fatta dal processore.

##### RAM

E' una memoria volatile (se il computer viene spento, il suo contenuto viene cancellato).

##### Moduli di I/O

Comprendono dispostivi di memoria secondaria non volatili, dispositivi per la comunicazione, tastiere, mouse, ecc...

#### Registri del processore

Sono delle zone di memoria molto più veloci di quelli della RAM.

I registri del processore sono divisibili in due categorie:
- Registri visibili dall'utente
- Registri non visibili dall'utente
##### Registri visibili all'utente

Sono utilizzati da chi programma in assembler o dai compilatori di linguaggi non interpretati.

Ci sono alcuni processori che hanno delle istruzioni in assembler che costringono a usare quegli registri

Altri servono per diminuire gli accessi alla RAM.

Possono condividere dati o indirizzi.

>[!info] Nel caso in cui contengono indirizzi
>- Possono contenere puntatori diretti
>- Possono essere dei registri - indice: offset rispetto a qualche altro indirizzo
>- Possono essere puntatori a segmento: se la memoria è divisa in segmenti che contengono l'indirizzo di inizio di un segmento
>- Puntatori a stack: puntano all'inizio di uno stack

##### Registi di controllo e stato

Sono usati dal processore per controllare l'uso del processore stesso oppure sono usati da funzioni privilegiate del sistema operativo.

- Program counter: usati per istruzioni da eseguire
- Instruction register: contiene l’istruzione prelevata più di recente
- Program status word: contiene informazioni molto importanti come la disabilitazione degli interrupt
- Flag: compattati in un unico registro

Tutti questi registri vengono letti o modificati in modo *implicito* da opportune istruzioni assembler (esempio: un jump che modifica il pc).

##### Registri interni

Usati dal processore tramite microprogrammazione.

Contengono i dati da scrivere in memoria oppure forniscono lo spazio dove scrivere i dati letti dalla memoria.

#### Esecuzione di istruzioni

I computer sano fare solo due cose: *fetch* ed *execute* di istruzioni.
Il sistema operativo si basa su questo processo.

**Fetch**
Prende il contenuto del program counter in cui c'è un indirizzo, va in ram, prende il contenuto della cella di memoria, lo mette nell'instruction register

**Execute**
Il valore del pc viene incrementato (`pc + 4`).
Prende quello che c'è nell'intsruction register e lo esegue.

![[Pasted image 20241005115508.png|500]]

Questo processo inizia nel momento stesso in cui il computer viene acceso e si ferma quando il computer viene spento.

#### Categorie di istruzioni

- Scambio dati tra processore e memoria
- Scambio dati tra processore e dispositivi di I/O
- Manipolazione di dati (operazioni aritmetiche)
	- Nel MIPS si possono fare solo con i registri
- Modifica del controllo (jump)
- Operazioni riservate (abilitazioni e disabilitazioni)

#### Come può essere eseguito un programma a un livello molto basso?

Immaginiamo di avere una macchina che ha dei registri a solo 16 bit utilizzati per memorizzare istruzioni e interi.

![[Pasted image 20241005120739.png|500]]

Nel caso dell'istruzione, i primi 4 bit servono per l'opcode (fa capire che istruzione è).

Nel caso dell'intero, il primo bit è il segno e il resto è il numero.

Supponiamo di conoscere 3 di questi opcode:
- (`0001 - load`) e immaginiamo di dover fare `load $ac from memory` (prende un indirizzo nella RAM e lo mette nel registro `$ac`)
- (`0002 - store`) e immaginiamo di dover fare `store $ac to memory` (prende quello che c'è in `$ac` e lo salva in memoria)
- (`0101 - add`) e immaginiamo di dover fare `add $ac from memory` (prende `$ac` e lo addiziona al contenuto della memoria a quell'inidirizzo e il risultato lo mette in `$ac`)

![[Pasted image 20240924161453.png|400]]

La RAM a partire dall'indirzzo 300, ha un programma di tre istruzioni (1940, 5941, 2941).

Lo scopo finale è addizionare dei numeri e metterli in un registro.

1. Il pc inizialmente vale `300`, la memoria carica nell'instruction register `1940` (fetch). 
	Guardo l'opcode (prima cifra dell'istruzione e la converto in binario `1 -> 0001`, quindi faccio una load) e `0003` viene caricato in `$ac`. Il pc viene incrementato per passare all'istruzione successiva (execute).
2. Viene caricato `5941` nell'istruction register (fetch). Guardo l'opecode (`5 -> 0101`, quindi faccio una add) e somma `0003` (contenuto in `$ac`) e `0002`. Il pc viene incrementato (execute).
3. Viene caricato `2941` (fetch). Guardo l'opcode (`2 -> 0010` quindi faccio uno store) e `0005` viene caricato all'indirizzo `941`

#### Interruzioni

Sono il paradigma dell'interazione hardware/software.
Interrompono la normale esecuzione sequenziale del processore.

Come conseguenza, viene eseguito dal software "di sistema", che tipicamente non è stato scritto dall'utente che sta eseguendo un certo programma.

Questo software di sistema è parte del sistema operativo.

Le cause delle interruzioni sono molteplici e danno luogo a diverse classi di interruzioni:

- Da programma
- Da I/O
- Da fallimento hardware
- Da timer

#### Interruzioni sincrone e asincrone

Le interruzione da programma sono le uniche *sincrone*, cioè sono l'immediata conseguenza di una certa istruzione.

Le altre sono *asincrone* perché vengono sollevate molto dopo l'istruzione che le ha causate e alcune non sono neanche causate dall'esecuzione di istruzioni.

##### Asincrone

Si dividono in:

**Interruzioni da input/output**

Sono generate dal controllore di un dispositivo di I/O.7
Generalmente i dispositivi di I/O sono più lenti del processore e quindi, il processore manda un comando al dispositivo e poi aspetta che il dispositivo lo "interrompa" quando è riuscito a completare la richiesta.
Infine, segnalano il completamento o l'errore di un'operazione I/O.


**Interruzioni da fallimento hardware**

Potrebbero non avere niente a che fare con alcune istruzioni (per esempio un'improvvisa mancanza di potenza) e quindi l'hardware manda un'interruzione.


**Interruzioni da comunicazione tra CPU**

Nei computer moderni spesso sono presenti più CPU e la comunicazione tra questi processori è effettuata attraverso interruzioni.


**Interruzioni da timer**

Sono generate da un dispositivo interno al processore (clock).
Tipicamente sono usate dal sistema operativo per eseguire alcune operazioni a intervalli regolari.


Per i processori Intel, gli interrupt sono solo questi.

---
### I/O programmato

E' il più vecchio modo di fare I/O.
Se il processo fa una lettura, il processo stesso andrà a verificare lo status finché l'operazione non è completa.

#### Accesso diretto alla memoria

Le istruzioni di i/o tipicamente richiedono di trasferire informazioni tra dispositivo di i/o e memoria

Trasferisce un blocco di dati direttamente dalla/alla memoria
Un'interruzione viene mandata quando il trasferimento è completo.

Liberiamo la cpu per eseguire qualcos'altro

#### Multiprogrammazione

Un processore deve eseguire più programmi contemporaneamente.

La sequenza con cui i programmi sono eseguiti dipende dalla loro priorità e dal fatto che siano o meno in attesa di input/output.

Alla fine della gestione di un’interruzione, il controllo potrebbe non tornare al programma che era in esecuzione al momento dell’interruzione.

#### Gerarchia della memoria

![[Pasted image 20240927140421.png|300]]

Andando dall'alto verso il basso:

- Diminuisce la velocità di accesso
- Diminuisce il costo al bit
- Aumenta la capacità
- Diminuisce la frequenza di accesso alla memoria da parte del processore

#### Memoria secondaria

- E' un tipo di memoria non volatile.
- Memoria "ausiliaria" ed "esterna"

#### Memoria cache

- La velocità del processor è maggiore della velocità di accesso alla memoria principale.
- Usata per immagazzinare i dati più utili
- E' molto veloce
- Mantiene un insieme di dati piccoli

#### Memoria principale e cache

![[Pasted image 20240927141123.png|400]]

##### Cache

Contiene copie di porzioni della memoria principale

Il processore prima controlla se un dato è nella cache
Se no, il corrispondente blocco di memoria viene caricato nella cache

E' probabile che il dato appena caricato serva ancora nell'immediato futuro.

