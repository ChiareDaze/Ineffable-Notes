>[!info] Programma
>- Come fa un computer a funzionare?
>- Come l'hardware si interfaccia
>- Gestione dei programmi

---
### Sistema operativo

Esiste perché serve a gestire risorse hardware di un sistema computerizzato.
Il suo scopo è quello di fornire un insieme di servizi agli utenti.

Sistema monoprocessore

![[Pasted image 20240924155459.png|300]]

- Processore (CPU): si occupa di tutte le computazioni
- Memoria principale: 
	- volatile: se si spegne il computer, se ne perde il contenuto
	- talvolta chiamata memoria reale o primaria
- Moduli di i/o
- "Bus" di sistema: mezzo per far comunicare tra loro le parti interne del computer (processori, memoria principale, e moduli di input/output)

#### Registri del processore

Registri visibili all'utente
Usati o da chi programma o dai compilatori di linguaggi non interpretati.

Registri di controllo di stato
Non visibili all'utente e usati da funzioni privilegiate del SO per controllare l'esecuzione dei programmi

Registri interni
usati dal processore tramite microprogrammazione, comunicazione con memoria e I/O.

![[Pasted image 20240924161453.png|400]]

A sinistra c'è la ram 
300-302 contengono le istruzioni.
La parte sotto contiene i dati.

#### Interruzioni

Possono contribuire alla modifica di un programma o l'ordine di esecuzione delle operazioni.
Interrompono le istruzioni.

metodo molto efficiente per scambiare informazioni tra le componenti.

Interruzioni sincrone e asincrone
Sincrone: hanno luogo come immediata conseguenza di una certa istruzione
Overflow
divisione per 0
debugging
riferimento ad indirizzo di memoria fuori dallo spazio disponibile dal programma
(vedi dopo)

Asincrone: sollevate dopo l'istruzione che le ha causate

Per le interruzioni asincrone, una volta che l’handler è terminato, si riprende dall’istruzione subito successiva a quella dove si è verificata l’interruzione

Con le sincrone non è detto
faults: errore corregibile, viene rieseguita la stessa istruzione
aborts: errore non corregibile
traps  system calls: si continua dall'istruzione successiva

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

