**Proprietà CIA**
- confidenzialità: le informazioni non devono essere divulgate a persone non autorizzate
- integrità: i dati non devono essere modificati da persone non autorizzate
- disponibilità: non ci devono essere interruzioni del servizio

- autenticità: garanzia che un messaggio sia inviato da una fonte autentica
- non ripudiabilità: tracciare in modo univoco le azioni di un utente/programma

**Classificazione attacchi**
Provenienza:
- outsider: dall'esterno
- insider: dall'interno
Tipologia:
- attivo: l'attante altera i dati o il funzionamento del sistema
- passivo: osserva e raccoglie informazioni

**Conseguenze attacco**
- unauthorized disclosure: dati divulgati da persone non autorizzate
- deception: informazioni date a un utente non autorizzato
- usurpation: viene preso il controllo del sistema
- disruption: interruzione delle funzionalità del sistema

**Principi di sicurezza di una sistema**
- i sistemi devono essere semplici e piccoli
- richiedere più condizioni per l'autenticazione
- più layer di sicurezza
- utenti devono avere i privilegi minimi per poter svolgere il proprio lavoro
- la sicurezza non deve essere basata sulla segretezza del codice
- l'accesso deve basarsi sui permessi e non sulle esclusioni
- ogni accesso a una risorsa deve essere verificato

**Cifratura simmetrica**
garantisce la confidenzialità dei dati. Mittente e destinatario condividono la stessa chiave con cui cifrare e decifrare il messaggio.
Può essere attaccata attraverso *criptoanalisi* e *forza bruta*.

- DES
- 3DES
- AES
- RC4
- ECB
- CBC
- CFB
- CTR

DES e 3DES si basano sulla rete di Feistel

**Rete di Feistel**
Composta da una serie di round composti da sostituzioni e permutazioni basati su una chiave.
Il blocco di plaintext (preferibilmente 128 bit) viene diviso in due.
La round function prende in input la chiave (128-256 bit) e la parte destra del blocco. L'output viene messo in xor con la parte sinistra del blocco.
Poi la parte a destra viene messa a sinistra e viceversa

**DES (Data encryption standard)**
block cipher
Blocco da 64 bit e chiave da 56 bit.
Struttura di Feistel a 16 round
Viene generata una sottochiave per ogni round a partire da quella originale

**3DES**
block cipher
Viene applicato il DES tre volte
Usa 2 o 3 chiavi. E' retrocompatibile con il DES e permette di decifrare messaggi cifrati con il DES
Cifratura: Cifratura(K1) -> Decifratura(K2) -> Cifratura(K3)
Decifratura: Decifratura(K3) -> Cifratura(K2) -> Decifratura(K1)

**AES(advanced encryption standard)**
block cipher
Prende un blocco di plaintext da 128 bit e la chiave 128 o 192 o 256 bit.
Il blocco viene copiato nello state array che viene aggiornato dopo ogni stage. Il risultato finale viene messo in una matrice di output
1. viene generata la chiave in base al numero di stage
2. add round key
3. substitute bytes: sostituzione byte a byte del blocco attraverso una tabella. I primi 4 bit vengono usati per la coordinata x e gli ultimi 4 per la coordinata y. 
4. Shift rows: composto da 4 righe. La prima non viene modificata, la seconda viene shiftata da 1 a sinistra, la terza di 2 a sinistra e la quarta di 3 a sinistra
5. mix column: vengono presi i 4 byte di una colonna e otteniamo nuovi i nuovi 4 byte in output
6. add round key: ha come input la chiave e le colonne mixate. Restituisce un vettore da 44 words

**RC4**
Stream cipher
Utilizza una chiave di lunghezza variabile da 1 a 256 bytes che viene utilizzata per inizializzare lo state array.
1. Viene inizializzato lo state array S con tutti i valori da 0 a 255
2. Viene inizializzato un altro vettore T. Se la lunghezza della chiave è uguale a 256, viene trasferita in questo vettore, altrimenti i primi n bit della chiave vengono copiati nell'array e viene aggiunto un padding che ripete la chiave tante volte quanto basta per riempire il vettore
3. Per effettuare la permutazione si calcola un indice sommando l'indice precedente, il valore corrente dello state array S\[i] e il valore corrente dell'array T\[i]. Tutto questo viene fatto inn modulo 256 in modo tale da non sforare il valore 255
4. Viene fatto lo swap tra S\[i] e S\[j]
5. Dopo aver inizializzato S, la chiave non viene più utilizzata. Per generare gli stream si itera su S, dove ogni elemento S\[i] vene scambiato con un altro elemento di S
6. Per cifrare si utilizza lo XOR del valore k con il successivo byte del plaintext

**ECB (electronic codebook)**
Blocchi di n bit vengono cifrati n bit alla volta con la stessa chiave. Per messaggi molto lunghi questo metodo non è sicura perché potrebbero esserci ripetizioni nel testo e quindi potrebbe essere possibile fare della criptoanalisi

**CBC (cipher block chaining)**
L'input dell'algoritmo viene messo in xor con il blocco precedente cifrato. Il primo blocco viene messo in XOR con un vettore di inizializzazione.
Per la decifratura ogni blocco viene passato all'algoritmo e il risultato viene messo in xor con il precedente blocco di cyphertext

**CFB (cipher feedback)**
Con questo metodo si può convertire qualsiasi block cipher in stream cipher.
La funzione di cifratura prende in input uno shift di n bit che per la prima unità viene applicato a un vettore di inizializzazione. Gli n bit più significativi del registro vengono messi in xor con l'unità precedente di plaintext. Questo processo continua finché tutte le unità di plaintext vengono cifrate.

**CTR (Counter mode)**
Come suggerisce il nome, viene utilizzato un counter che corrisponde alla grandezza dei blocchi del plaintext. Il counter deve essere diverso per ogni plaintext. Di solito si inizializza il counter e poi si incrementa ogni volta di 1.

**Distribuzione della chiave**
Quando due end system vogliono comunicare tra loro, stabiliscono una connessione logica. Per tutta la durata della sessione tutti i dati vengono cifrati con una *one time session key* che viene distrutta quando la comunicazione viene chiusa.
Per distribuire la session key viene utilizzata la *permanent key*.
Gli elementi fondamentali in questa configurazione sono il *key distribution center* e il *security service module*
Per avere una distribuzione sicura della chiave:
1. un host invia una richiesta per parlare con un altro host
2. il SSM salva il pacchetto e chiede al KDC l'autorizzazione
3. tra il SSM e il KDC avviene una comunicazione cifrata con una master key. Se il KDC approva la comunicazione genera una sessione key e la invia ai due SSM utilizzando una chiave permanente per ogni SSM
4. L'SSM può quindi stabilire la connessione tra i due sistemi e rilasciare il pacchetto di connessione

**Crittografia a chiave asimmetrica**
Risolve il problema della distribuzione della chiave e garantisce autenticazione e confidenzialità.
Viene utilizzata una coppia di chiavi, una pubblica e una privata.
*Algoritmi*:
- Funzioni hash semplici
- HMAC
- RSA
- Authenticated encryption
- Diffie-Hellman

**Funzione di Hash**
Prende in input un messaggio di dimensione variabile e restituisce un'impronta i dimensione fissa.
Esistono 6 regole fondamentali. Data una funzione di hash $H$:
1. Deve essere difficile trovare una coppia $(x,y)$ tale che $H(x)=H(y)$
2. Per ogni blocco $x$ deve essere difficile trovare un valore $y$ con $x \neq y$ tale che $H(x)=H(y)$
3. $H(x)$ deve essere facilmente calcolabile per ogni $x$ in input
4. $H$ produce un output di lunghezza fissa
5. $H$ può essere applicata a blocchi di qualsiasi dimensione
6. $H$ non deve essere invertibile. Quindi dato un codice hash $h$ deve essere difficile calcolare un $x$ tale che $H(x) = h$

**Hash utilizzato per l'autenticazione (One way hash function)**
Distinguiamo 3 modalità:

*One Way Hash Function + Symmetric Encryption*
1. L'hash function prende in input il messaggio
2. Cifra il codice hash attraverso la chiave simmetrica e lo aggiunge al messaggio
3. Il mittente invia messaggio + hash cifrato
4. Il destinatario prende il messaggio e genera l'hash
5. Decifra l'hash che era stato aggiunto al messaggio
6. Confronta l'hash decifrato con quello generato per verificare l'integrità del messaggio

*One Way Hash Function + Public Key Encryption*
1. L'hash function prende in input il messaggio
2. Cifra il codice hash attraverso la chiave privata del mittente e lo aggiunge al messaggio
3. Il mittente invia messaggio + hash cifrato
4. Il destinatario prende il messaggio e genera l'hash
5. Decifra l'hash che era stato aggiunto al messaggio con la chiave pubblica del mittente
6. Confronta l'hash decifrato con quello generato per verificare l'integrità del messaggio

*One Way Hash Function + Secret value (no encryption)*
1. Viene aggiunta la chiave all'inizio e alla fine del messaggio
2. L'hash function prende in input il messaggio + le chiavi
3. Il codice hash viene aggiunto al messaggio SENZA essere cifrato
4. Il mittente invia messaggio + hash
5. Il destinatario prende il messaggio ci aggiunge le chiavi all'inizio e alla fine e genera l'hash
6. Confronta l'hash del messaggio con quello generato per verificare l'integrità del messaggio

**SHA-512**
E' una funzione di hash che produce un output da 512 bit da un input variabile.
E' una delle tre evoluzioni dello SHA-1, nello specifico è la più sicura perché produce un output più lungo.
*Procedimento*
1. Il messaggio viene completato con un padding formato da un 1 seguito da tanti 0 quanti servono per arrivare a 896 modulo 1024.
2. Viene anche aggiunto un blocco da 128 bit contenente la lunghezza del messaggio 
3. Questo nuovo blocco viene diviso in tanti blocchi da 1024 bit ciascuno
4. Vengono utilizzati 8 registi da 64 bit, inizializzati a dei valori calcolati prendendo i primi 64 bit delle radici quadrate dei primi 8 numeri primi
5. Il cuore dell'algoritmo è la funzione composta da 80 round. Ogni round:
	- Aggiorna il contenuto del buffer
	- utilizza un valore a 64 bit derivato dal messaggio
	- utilizza costanti che rappresentano i primi 64 bit delle parti frazionarie delle radici cubiche dei primi 80 numeri primi
6. Vengono effettuate rotazioni circolari e funzioni basate su or and not e xor
7. l'output all'80esimo round viene sommato al valore iniziale del buffer prima di entrare nella funzione
8. l'output va in ingresso come buffer al blocco successivo
9. alla fine si ottiene un digest da 512 bit

**HMAC**
Tratta la funzione di hash come una black box, cioè non interessa com'è costruito, ma il suo input e il suo output.
Gli obiettivi dell'HMAC sono:
- utilizzare senza modificare le esistenti funzioni hash
- consentire di sostituire delle funzioni hash con altre più sicure
- preservare le performance della funzione hash
- utilizzare le chiavi in modo semplice
- fornire un'analisi crittografica
*Procedimento*
1. Viene fatto uno XOR tra la chiave estesa (aggiungendo 0 a sinistra per farla arrivare a n bit) e un valore ipad (che inverte la metà dei bit di K). Viene così creato un blocco S\[i] da aggiungere al messaggio
2. Il messaggio + S\[i] è l'input della funzione di hash insieme a un vettore di inizializzazione casuale
3. Si fa uno XOR tra la chiave estesa e un valore opad (che inverte l'altra metà dei bit di K) che produce un blocco S\[i] da aggiungere al digest
4. Il risultato è l'input della funzione di hash insieme al vettore di inizializzazione casuale e si ottiene l'HMAC

Il destinatario una volta ricevuto il messaggio dal mittente, calcolerà a sua volta il valore dell'HMAC e se i due valori (HMAC del mittente e quello del destinatario) coincidono, allora sarà sicuro dell'autenticità e dell'integrità del messaggio.

Questo algoritmo come punti di forza ha anche la robustezza agli attacchi di forza bruta.

**RSA**
Algoritmo a chiave pubblica con cifrario a blocchi. Il testo in chiaro e il testo cifrato sono numeri interi compresi tra $0$ e $n-1$ per un certo $n$.
Ha un chiave pubblica $Pu=\{ e,n \}$ e una chiave privata $Pr=\{ d,n \}$. 
Mittente e destinatario conoscono $e$ e $n$, ma solo il destinatario conosce $d$.

Dato il messaggio in chiaro $M$ e il testo cifrato $C$:

$$
C = M^{ e } \space \text { mod } \space n  
$$
$$
M = C^{ d } \space \text { mod } \space n = (M^{ e } )^{ d } \space \text { mod } \space n = M^{ ed } \space \text {  mod } \space n  
$$

*Requisiti*
- deve essere impossibile trovare $d$ avendo $e$ e $n$
- deve essere facile calcolare $M^{ e }$ e $C^{ d }$
- Deve essere sempre possibile trovare valori tali che $M^{ ed } = M \space \text {  mod } \space n \space \space\space \forall \space M < n$

Per quanto riguarda l'ultimo punto, per soddisfare $M^{ ed } \space \text {  mod } \space n$, é necessario soddisfare $e \cdot d \space \text { mod } \space \Phi(n) = 1$.

$\Phi(n)$ è il *toziente di Eulero* che rappresenta il numero di interi positivi più piccoli di $n$ che sono primi di $n$.
Però, se abbiamo $n$ molto grande si dovrebbero controllare tutti i numeri primi (impossibile)
La matematica dice che se $n = q \cdot p$ con $p$ e $q$ primi, allora possiamo calcolare $\Phi(n)= (p-1) \cdot (q-1)$.
Quindi, se conosciamo i due numeri che generano $n$, allora possiamo calcolare $\Phi(n)$.

*Passaggi*
1. Scelgo $p$ e $q$ primi e diversi tra loro
2. Calcolo $n = p \cdot q$
3. Calcolo $\Phi(n) = (p-1)\cdot(q-1)$
4. Seleziono $e$ facendo $MCD(\Phi(n),e) = 1$
5. Calcolo $d$ sapendo che $e \cdot d \space \text { mod } \space \Phi(n) = 1$
6. Creo la chiave $Pu = \{ e,n \}$
7. Creo la chiave $Pr = \{ d,n \}$
8. Cifro il messaggio con $C = M^{ e } \space \text { mod } \space n$ 

Maggiore sono i bit di $d$, più si ha sicurezza contro la forza bruta ma al tempo stesso si ha un rallentamento delle prestazioni.
E' stato dimostrato che se $e<n$ e $d<n^{ 1/4 }$ allora $d$ può essere determinato.

Inoltre è vulnerabile ai timing attacks che sfruttano il tempo impiegato per decifrare per determinare la chiave.
1. L'attacnte crea un messaggio cifrato e lo invia. Quando il computer analizza il bit, se quel bit è 1, allora l'operazione sarà molto lenta. Altrimenti più veloce.
2. Viene cronometrato il tempo e in base a quanto ci mette, viene rivelata la chiave

Le contromisure sono di tre tipi:
- Constant exponential time: il computer viene costretto a impiegare lo stesso tempo massimo, ma questo peggiora le prestazioni
- Random delay: viene applicato un delay in un momento a caso, ma l'attacnte potrebbe calcolare la media dei tempi e trovare il tempo reale
- Blinding: consiste nell'ingannare oil cronometro dell'hacker modificando il messaggio ricevuto

**Diffie-Hellman**
L'algoritmo permette a due utenti di scambiarsi la chiave in modo sicuro.
Vengono scelti due elementi pubblici:
- un numero primo $q$
- $\alpha < q$, dove $\alpha$ è la radice primitiva di $q$

Una radice primitiva modulo $n$ è un numero $g$ che elevato a potenza riesce da solo a generare tutti i numeri possibili di quel modulo.
Non tutti i numeri possiedono radici primitive, cioè avviene solo per $2$, $4$, $p^{ k }$ e $2p^{ k }$ dove $p$ è un numero primo dispari.

*Procedimento*
- Il mittente genera le sue chiavi. Prima seleziona una chiave privata $X_{A}$ tale che $X_{A}<q$ e poi calcola la chiave pubblica $Y_{A} = \alpha^{ X_{A} }\space \text { mod } \space q$
- Il mittente genera le sue chiavi. Prima seleziona una chiave privata $X_{B}$ tale che $X_{B}<q$ d poi calcola la chiave pubblica $Y_{B} = \alpha^{ X_{B} }\space \text { mod } \space q$
- Mittente e destinatario si scambiano le chiavi pubbliche
- Il mittente calcola $K = (Y_{B})^{ X_{A} } \space \text {  mod } \space q$
- Il destinatario calcola $K = (Y_{A})^{ X_{B} } \space \text {  mod } \space q$
- Le chiavi appena calcolate verranno utilizzate per le comunicazioni future

Questo tipo di algoritmo è vulnerabile all'attacco *man in the middle*. Qui l'attaccante si frappone tra i sue utenti.
L'attaccante genera le sue chiavi private. Intercetta le chiavi di mittente e destinatario e trasmette le sue.
In questo modo, mittente e destinatario calcolano le proprie chiavi a partire da quelle trasmesse dall'attaccante e quest'ultimo potrà leggere tutti i messaggi.
Questo problema può essere evitato andando a utilizzare firme digitali o certificati a chiave pubblica.

**Firma digitale e certificati a chiave pubblica**
Serve per verificare l'integrità e la non-ripudiabilità del messaggio e l'autenticità del mittente.
L'idea è quella di creare un un pacchetto di dati che accompagna il messaggio.

Il mittente deve calcolare l'hash del messaggio, cifrare l'hash ottenuto con la sua chiave privata e inviare il messaggio in chiaro insieme al all'hash.
Il destinatario effettua l'hash sul messaggio in chiaro, decifra con la chiave pubblica del mittente l'hash ricevuto e lo confronta con quello calcolato.

Il problema in questo tipo di algoritmo è che qualcuno potrebbe essersi finto il vero mittente quando ha pubblicato la sua chiave pubblica. Per questo, vengono utilizzati i *certificati a chiave pubblica*.

I certificati sono composti da:
- La chiave pubblica da distribuire
- L'ID del possessore
- Informazioni sulla *Certification Authority* (Aruba, PosteItaliane,... che si occupa di verificare l'appartenenza delle chiavi)
- Periodo di validità

*Come si crea il certificato*
1. La CA crea il certificato usando una funzione di hash su tutto il certificato e genera una firma digitale utilizzando la propria chiave privata
2. Allega la firma e il certificato NON verificato
3. Invia il certificato verificato all'utente

Ora il certificato potrò essere pubblicato dall'utente e chiunque potrà verificarlo attraverso la chiave pubblica della CA:
- L'utente calcola l'hash del certificato (senza firma)
- Tramite la chiave pubblica della CA decifra la firma e verifica se combacia con l'hash ottenuto

**User Authentication**
Prevede due step:
- identificazione: identificazione della persona
- authentication: provare che la persona è realmente chi dice di essere

**Metodi di autenticazione**
- *qualcosa che la persona sa*: password, pin
- *qualcosa che la persona ha*: smart card, chiavi elettroniche
- *qualcosa che la persona è*: impronte digitali
- *qualcosa che la persona fa*: azioni come parlare, scrivere

**Autenticazione con qualcosa che l'utente sa**
Le pw offrono sicurezza, ma questa viene compromessa dal comportamento umano:
- utilizzare un pw per ogni oggetto al quale si accede, ma è scomodo
- se qualcuno di non autorizzato si impossessa della pw, bisogna cambiarla e avvisare tutti gli utenti autorizzati
- se pw viene dimenticata o persa, gli amministratori devono fornirne una nuova

**Attacchi alle password**
- *Attacco a dizionario*: raccolte di parole e frasi celebri di film/serie tv/... che spesso vengono utilizzate come password. Questo attacco viene utilizzato anche dagli amministratori di sistema per capire se gli utenti hanno usato password deboli
- *rainbow table*: pw identiche avranno la stessa cifratura. Se un attaccante riesce a impossessa di una tabella con pw cifrate, può comunque sapere chi sta utilizzando la stessa pw anche se non sa quale sia. Come contromisura viene utilizzato il *salt* che aggiunge dei dati come per esempio la data di iscrizione al sistema o altri dati randomici

**Gestione delle pw in Unix**
Si basa sull'utilizzo di funzioni hash e il salt per la protezione delle pw.
Quando viene creata una nuova pw:
- viene unita al salt
- La stringa di pw + salt viene elaborata da una funzione di hash che da in output un digest di lunghezza fissa
- L'algoritmo è progettato per essere computazionalmente lento, in modo tale da ostacolare i tentativi di attacco
- Il digest e il salt vengono memorizzati all'interno del file delle pw di sistema

Il salt serve:
- a prevenire la visibilità di due pw identiche
- ostacolare attacchi a dizionario (un salt di $b$ bit moltiplica la complessità del calcolo a $2^{ b }$)

Le minacce su questo sistema sono:
- programmi di pw cracking sfruttando l'accesso guest
- furto del file delle pw e esecuzione del programma di pw cracking in locale

**Politiche di accesso**
Guidano l'implementazione dei meccanismi di controllo degli accessi.
- Controllare ogni accesso periodicamente: i privilegi degli utenti cambiano nel tempo, quindi potrebbe essere possibile che un utente debbano essere rimossi dei privilegi
- *least privilege*: ogni utente deve avere il minimo numero di privilegi necessari per poter svolgere il proprio lavoro.
- verificare che gli utenti utilizzino in modo corretto i loro privilegi

**Implementazione del controllo degli accessi**
Implementato dal sistema operativo stesso. L'access control deve seguire il *reference monitor* che è un principio di progettazione secondo cui sistema deve essere:
- sempre disponibile in modo da poter validare ogni tentativo di accesso
- immune alle manomissioni
- corretto

*Modelli per la gestione dell'AC*
- Access control directory
- Access control matrix
- Access control list

**Access control directory**
Ogni utente ha una file directory che elenca tutti i file a cui ha accesso.
Ovviamente nessun utente ha accesso in scrittura sulla file directory. E' il so che la gestisce in base ai comandi che riceve.

E' facile da implementare, ma ha anche dei contro:
- la lista potrebbe avere dimensioni enormi se ci sono tanti file
- Se un utente $A$ da accesso a un utente $B$ e $B$ a sua volta lo trasmette a $C$, $A$ perde traccia di chi ha il permesso sul file
- Gli pseudonimi sono un problema, perché se $A$ possiede un file $F$ e $B$ possiede un altro file chiamato $F$ e entrambi trasmettono l'accesso ai due file a $C$, $C$ non saprebbe distinguere quale file è di $A$ e quale è di $B$
- Rinominare i file potrebbe generare inconsistenze nei permessi

**Access control matrix**
E' una tabella dove le righe sono gli utenti e le colonne le risorse a cui devono accedere. In ogni cella ci sono i permessi corrispondenti.
La matrice viene usata raramente perché è una struttura inefficiente.

**Access control list**
C'è una lista per ogni oggetto e questa mostra per tutti gli utenti quali permessi hanno su quel file.
In questa struttura è possibile implementare permessi di default senza andare a cercare una entry per ogni utente.
- Vantaggi: rapidità nel conoscere la lista di coloro che hanno accesso a un oggetto
- Svantaggi: lentezza nel determinare a quali oggetti ha accesso un utente

**Capability Token**
E' un token non falsificabile che fornisce al suo possessore dei permessi su un oggetto.
E' una tripla di soggetto, oggetto e permessi.
*Rendere il token non falsificabile (2 soluzioni)*
1. Il SO memorizza i token nel kernel e all'utente vengono forniti una struttura interna. Quando un utente vuole accedere a un oggetto, il SO crea il token
2. Il token viene dato all'utente, ma è autenticato con una chiave che possiede solo il SO. Se l'utente prova a modificarlo, la firma digitale si rompe e il SO se ne accorge subito, rifiutando l'accesso

*Propagazione del token*
Il token può essere propagato per propagare i permessi.
L'utente $A$ ha una capability e la copia a $B$. $B$ a sua volta la copia a $C$. Se $B$ vuole essere prudente, può fare una copia per $C$ ma togliere il permesso di propagazione. In questo modo $C$ potrà usare la risorsa, ma non potrà a sua volta fare copie per un utente $D$.

*Revoca del token*
il SO non perde di vista le copie, tiene una *tabella di puntatori*. Quando l'utente originario decide di revocare il permesso, il SO va a vedere quella tabella, segue tutti i collegamenti e distrugge sia il token originale sia tutte le copie che erano state propagate nel tempo.

**DAC (Discretionary Access Control)**
E' uno schema dove a un'entità vengono concessi diritti di accesso e che tale entità può concedere ad altri. Utilizza la matrice di accesso strutturata soggetto (utenti) x oggetto (record, file, database).

Dato che si sono molti spazi vuoti e sparsi, le implementazioni sono di due tipi:
- decomponendo la tabella per colonne (ACL)
- decomponendo la tabella per righe (Capability token)

**RBAC (Role based access control)**
Basa i diritti di accesso in base ai ruoli assegnati agli utenti. I ruoli sono generalmente definiti in base alle funzioni lavorative all'interno di un'organizzazione, e a ciascun ruolo vengono assegnati diritti di accesso specifici alle risorse.

E' facilmente applicabile il principio del *least privilege*

Per implementare questo meccanismo abbiamo bisogno di una tabella che per ogni utente quale ruolo/ruoli possiede. Serve anche una access control matrix che per ogni ruolo indica quali permessi ha.

*Modelli di riferimento*:
- RBAC0: introduce il concetto di utente, ruoli, permessi e sessione
- RBAC1: introduce le gerarchie dei ruoli per ridurre la complessità della gestione degli accessi 
- RBAC2: introduce i vincoli 
- RBAC3: combina i tre modelli precedenti

**ABAC (Attribute based access control)**
Definisce condizioni sia sugli oggetti che sui soggetti. Ci sono 3 elementi principali in questo modello:
- Attributi (del soggetto, dell'oggetto o dell'environment)
- Policy model
- Architecture model

ABAC verifica l'accesso agli oggetti considerando le regole sugli attributi. Quando un utente prova ad accedere a una risorsa, la richiesta viene analizzata da un meccanismo di access control. Il meccanismo è guidato a sua volta dal policy model, e basandosi su di esso, definisce gli attributi del soggetto, della risorsa e dell'ambiente per determinare l'autorizzazione.

**Buffer Overflow**
In questo tipo di attacco, un processo tenta di memorizzare dati oltre i limiti di un buffer a dimensione fissa, eccedendo lo spazio pre-allocato.
Ciò che può provocare è:
- corruzione di dati
- Quando una funzione chiama un'altra, i suoi parametri e indirizzi di ritorno vanno nello stack. Un utente malintenzionato potrebbe sovrascrivere parametri e indirizzi di ritorno, e dirottare il flusso del programma verso il codice malevolo
- stack smashing: se l'heap non viene controllata può espandersi in maniera anomala finendo per collidere e schiacciare lo stack

Le *contromisure sono*:
- Controllare sempre le lunghezze dei dati prima di effettuare scritture, confermare i limiti sugli array, usare utilità di gestione delle stringhe sicure e limitare i privilegi dei programmi
- Usare linguaggi ad alto livello come Java o Python perché controllano automaticamente i limiti
- Difese a tempo di esecuzione:
	- Impedire di eseguire il codice nello stack
	- Randomizzare lo spazio degli indirizzi che modifica l'indirizzo in cui si trovano heap e stack per rendere difficile prevedere dove si trovano buffer vulnerabili
- Utilizzo del *canary*: a livello del sistema operativo viene applicato un livello protettivo attorno al frame dello stack inserendo un valore esca (canary).

**Incomplete mediation**
La *mediazione* è l'atto di verificare l'autorizzazione di un soggetto a eseguire un'azione.
Il problema arriva quando non avviene un controllo esaustivo. Per esempio, un sito di e-commerce che usa un URL in chiaro per i parametri d'acquisto (prezzo e quantità). Il server si affida al browser dell'utente e se quest'ultimo modifica l'URL e backend non convalida questi dati, allora l'attaccante pagherà di meno i prodotti. 
*Contromisure*:
- Convalidare sempre i dati che riceviamo con quelli che abbiamo nel database

**Time-of-Check to Time-of-Use**
Sfrutta l'intervallo di tempo tra il momento in cui il sistema controlla un'autorizzazione e il momento in cui usa il file. In questo lasso di tempo l'attaccante potrà modificare la risorsa, poi il programma userà il dato alterato, aggirando i controlli di sicurezza.
*Contromisure*
- eliminare il tempo tra il controllo e l'uso
- copiare i dati dell'utente in un'area sicura del SO ed eseguire una validazione direttamente sulla copia

**Backdoor**
Durante lo sviluppo dei software, gli sviluppatori lasciano spesso delle "porte di servizio" che non passano per i controlli di sicurezza.
Il problema nasce quando si scordano di rimuoverle e quindi un attaccante può scovarle e entrare nel sistema da lì, superando i controlli.

**Fasi di intrusione di un attaccante**
1. Acquisizione del bersaglio e raccolta informazioni (per esempio invio di email di richiesta informazioni)
2. L'accesso iniziale avviene sfruttando le vulnerabilità della rete o nei sistemi di autenticazione
3. Dopo aver ottenuto l'accesso iniziale, l'attaccante cerca di ottenere privilegi più elevati utilizzando le vulnerabilità locali
4. L'attaccante accede o modifica le informazioni sul sistema o si sposta su altri sistemi della rete target
5. L'attaccante può installare backdoor o malware per consentire accesso continuo
6. L'attaccante cancella le proprie tracce, nascondendo file installati e modificando i log

**Tipi di Malware**
In base a come si propagano:

*Virus*
E' un programma che si replica infettando altri programmi non maligni andando quindi a modificarli inserendo il proprio codice.
La sua caratteristica principale è  che non può funzionare e replicarsi se non c'è un programma ospite.
Possono essere resident se insediano nella memoria e rimane attivo finché il sistema non si spegne, oppure possono essere transient se vivono e muoiono con l'esecuzione dell'ospite.
E' composto da tre parti:
1. Meccanismo di infezione: permette al virus di replicarsi
2. Payload: azioni che il virus fa oltre a diffondersi
3. Trigger: evento che determina quando il payload si attiva

Ciclo di vita:
1. fase dormiente: virus inattivo o in attesa di essere attivato
2. propagazione: si diffonde su altri programmi o aree di memoria
3. attivazione: viene attivato dal trigger
4. esecuzione: esegue il suo codice malevolo

Virus Melissa:
- Il virus disabilitava il menù macro e le funzionalità associate
- Infettava ogni documento aperto sul sistema
- Mandava copie di se stesso via email ai primi 50 indirizzi, controllando se era presente la chiave `melissa` nel registro di sistema
- dopo le email creava la chiave `melissa`
- se veniva raggiunto un trigger, veniva inserita una citazione dei Simpson nel documento

*Worm*
E' un programma che diffonde copie di sé stesso attraverso la rete (email e messaggistica, trasferimento di file). A differenza dei virus, non ha bisogno di un ospite (standalone).
Selezione vittime:
- Casuale
- Tramite una lista di utenti
- Topologica: sfrutta la rubrica dell'host
- infetta le sottoreti vicine evitando il firewall

*Trojan Horse*
Oltre al suo scopo primario nasconde un secondo effetto dannoso (schermata di login che permette il login, ma al tempo stesso invia le informazioni all'attaccante)

Malware in base alle azioni:

*Time Bomb*
Si attivano quando si verifica una certa condizione (condizione logica o orario prestabilito)

*Ransomware*
Cifra i dati della vittima e chiede un riscatto per decifrarli

*Rootkit*
Si installa nelle sezioni privilegiate del sistema operativo ed è molto difficile da rilevare

**SQL Injection**
Sfrutta la scarsa sanitizzazione degli input per inviare comandi SQL direttamente al database backend.
L'attacco interrompe prematuramente la stringa attesta dal database utilizzando il singolo apice `'` e aggiunge un nuovo comando, inserisce poi alla fine il simbolo del commento per omettere tutto il resto del codice legittimo.

*SQLi in band*
Utilizza lo stesso canale di comunicazione sia per mandare l'injection al DBMS sia per ricevere indietro i dati.
- Tautologia: inietta una o più condizioni sempre vere per esempio `' OR 1 = 1` per aggirare l'autenticazione
- Commento a fin linea: l'attaccante usa il commento `--` per iniettare codice malevolo e disattivare quello legittimo che segue
- Piggybacked: l'attaccante accoda una query distruttiva a una legittima

*SQLi out of band*
Utilizzato quando le informazioni non possono tornare indietro via HTTP, ma il database possiede connettività in uscita vulnerabile per inviare i dati tramite altri canali

*Contromisure*
- Usare *query parametrizzate* per evitare che l'input sia direttamente concatenato alla query, specificando la struttura della query stessa
- Usare classi che permettono la validazione automatica che incapsula la query
- Assicurarsi che i valori numerici non contengano caratteri non numerici

**Cross-Site Scripting XSS**
Sfrutta il fatto che le comunicazioni HTTP trasmettono in chiaro script incorporati. In questo modo costringono il browser o il server ad eseguire codice malevolo mascherato da contenuto legittimo.
Per esempio l'inserimento di uno script malevolo nei commenti di un blog e chiunque carichi quella pagina eseguirà lo script senza accorgersene.
*Contromisure*
- Validazione e sanitizzazione dell'input
- utilizzo di framework e librerie che offrono protezione integrate contro l'XSS

**Hardware Protection of Memory**
*Fence*
Impongono limiti hardware statici o dinamici per definire dove finisce il SO e dove comincia lo spazio utente
- statici: limitazione hardware fissa, il confine tra memoria del sistema operativo e lo spazio dei programmi utente è stabilito a un indirizzo di memoria specifico ed è immutabile
- dinamici: utilizza uno specifico registro che memorizza l'indirizzo di confine. Può cambiare nel tempo

*Base/bound registers*: sono coppie di registri utilizzati per tracciare l'indirizzo di base e il limite superiore consentito.
- Il base register memorizza l'indirizzo di memoria da cui inizia lo spazio assegnato a uno specifico programma utente
- Il bound register memorizza l'indirizzo che stabilisce il limite superiore. Ogni volta che il programma tenta di accedere alla memoria, l'hardware verifica che l'indirizzo richiesto sia tra il valore e base e il valore bound

*Tagged Architecture*
Associa a ogni singola parola di memoria un'etichetta di permessi esplicita.
-  *Segmentazione*: un programma, dal punto di vista "logico", è un insieme di blocchi contigui. Tuttavia, nella memoria fisica reale, questi blocchi vengono posizionati in aree diverse e separate. Quando un programma richiede un dato, non accede direttamente alla RAM. La richiesta passa attraverso il Sistema Operativo che "traduce" l'indirizzo logico in indirizzo fisico. Il SO utilizza una tabella (*segmentation translation table*) che associa ogni segmento alla sua cella di partenza nella memoria fisica (indirizzo base). Per trovare il dato esatto, il sistema si posiziona all'indirizzo di partenza e vi somma l'offset

- *Paginazione*: I segmenti hanno dimensioni variabili. Questo costringe il sistema a eseguire controlli complessi e continui per verificare che gli indirizzi non superino la fine del segmento. Si introduce la paginazione. Il programma logico non è più diviso in segmenti di grandezza variabile, ma in pagine tutte della stessa dimensione. Di conseguenza, anche la memoria fisica viene divisa in blocchi fissi della stessa misura, chiamati page frames. Offre gli stessi benefici della segmentazione, ma rende la gestione della memoria molto più efficiente e semplice per il sistema

- *Segmentazione Paginata*: Nella realtà, per ottenere il massimo dell'efficienza e della sicurezza, i sistemi operativi moderni utilizzano un meccanismo ibrido e più robusto che concatena le due tecniche. Invece di avere una singola tabella, si usano due tabelle concatenate.
	1. Si cerca l'indirizzo
    2. La prima tabella (Segment Translation Table) non punta più direttamente alla memoria fisica, ma punta a una seconda tabella dedicata _esclusivamente_ a quel segmento specifico (Page Translation Table)
    3. L'offset viene convertito in un numero di pagina
    4. La Page Translation Table ci dice a quale indirizzo fisico si trova quella specifica pagina.
    5. Infine, ci si sposta a quell'indirizzo fisico e si somma l'offset "residuo" per trovare la parola esatta in memoria

**Cifratura dei database**
La cifratura rappresenta l'ultima linea di difesa per proteggere i dati sensibili all'interno di un database.
La cifratura può essere applicata a diversi livelli: sull'intero database, sulla singola tabella, a livello di record (riga), di attributo (colonna) o sul singolo campo.
Tuttavia, cifrare un db presenta due svantaggi:
- Gli utenti devono avere a disposizione le chiavi per decrittare, ma fornire le chiavi sicure solo per alcune parti di un database è complesso
- E' difficile cercare sui record

Spesso la gestione del database viene delegata a un fornitore esterno. Per garantire la privacy, i dati vengono inviati al fornitore già cifrati e *non* gli viene fornita la chiave di decrittazione.

Ogni elemento del database viene crittografato singolarmente utilizzando la stessa chiave crittografica. L'utente cerca i record con chiave primaria di un valore specifico. Il server cripta la chiave e restituisce i record associati.
Questo, però, ci limita quando dobbiamo selezionare range di valori o ricerche basate sull'ordinamento naturale.
Perciò si crittografa ogni riga (record) come un unico blocco di dati. Per recuperare i dati si dividono gli intervalli di valori dei dati in partizioni, a cui ognuna è associato un indice. Gli indici facilitano il recupero dei dati senza decriptare l'intervallo completo

**Denial of Service (Dos)**
Non è sempre un blocco totale del servizio, ma può anche indicare un forte rallentamento del servizio.
- Ping of death: se l'attaccante possiede più banda dela vittima può saturare la rete inviando innumerevoli richieste di ping
- smurf attack: l'attaccante invia un pacchetto broadcast finto alla rete utilizzando come IP di origine quello della vittima (spoofing). Tutti i computer rispondono contemporaneamente verso l'host della vittima congestionandola. 
- echo-chargen: l'attacnte manda un pacchetto a $B$ fingendosi $A$. $B$ crede che il pacchetto provenga dal chargen di $A$ e quindi lo rispedisce a $A$. Si instaura così un loop infinito
- SYN-Flood: Il protocollo TPC prevede un three-way handshake. L'attaccante manda tante richieste SYN fornendo un IP falso. Il server risponde con SYN-ACK ma l'ACK di conferma non arriverà mai lasciando la porta del server aperta in attesa, esaurendo velocemente le risorse disponibili
- teardrop: un attaccante può inviare frammenti di datagrammi che si sovrappongono tra loro rendendo impossibile la ricostruzione e causando un rallentamento nel sistema

**Distributed Denial of Service (Ddos)**
Si usano più sistemi per generare attacchi. Viene installato un agente di attacco controllato dall'attaccante tramite malware.
Questa rete prende il nome di *botnet* e segue una struttura a cascata pensata per proteggere chi ha organizzato l'attacco. Ha anche la funzione di rimanere attivo nel caso di crash di alcune porzioni della rete.
L'attaccante invia comandi a un primo livello di macchine (Server Master) che a loro volta li inviano ai server a stretto contatto con i bot.

*Contromisure*
- Controlla costantemente le vulnerabilità

**Honeypot**
E' un esca per attirare gli attaccanti lontano da punti critici, simulando risorse e servizi vulnerabili senza contenere dati o funzioni reali.
*Obiettivi*:
- distrarre l'attaccante 
- monitorare le attività sospette
- non devono comunicare con l'esterno (se succede significa che è compromesso)

*Tipologie*:
- Low interaction: simulano parzialmente alcuni servizi per fornire una prima interazione senza implementare una verso sistema
- high interaction: sistema reale completo di servizi. Servono a distrarre l'attaccante più a lungo

*Dove posizionarli*
1. fuori il firewall esterno
2. nella DMZ (demilitarized zone), cioè una zona di rete accessibile dall'estrno che ospita servizi come web e posta
3. nella rete interna

**Firewalls**
Dispositivo che esegue un codice per filtrare il traffico tra una rete interna e una esterna.
Il firewall decide cosa passa e cosa no basandosi su due filosofie:
- *default permit*: tutto quello che non è esplicitamente vietato è permesso
- *default deny*: tutto ciò che non è esplicitamente concesso è vietato

**Tipologie di firewall**
*Pocket/URL Filtering*: il più semplice e veloce. Analizza un pacchetto per volta guardando solo gli indirizzi IP e le porte senza memoria del passato

*Circuit Level Gateway*
Verifica e autorizza la connessione logica nel momento in cui viene creata, ma una volta stabilita lascia passare i dati successivi senza controllare

*Stateful Inspection*
Mantiene in memoria lo stato della connessione. Correla le informazioni dei pacchetti precedenti con quelli successivi

*Deep Packet Inspector (DPI)*
Oltre agli IP ispeziona anche il contenuto dei pacchetti. Può anche alterare i dati in uscita anonimizzando il traffico

*Application Proxy Gateway*
Lavora al livello più alto (livello Applicazione). Si comporta come un intermediario. Riceve i dati, li analizza in base a come si comporta l'app e poi crea una nuova connessione verso la macchina interna. E' molto lento

*Guard*
Un proxy molto sofisticato permette regole programmabili.
Interpreta a fondo i pacchetti e ne genera di nuovi per garantire sicurezza. In base allo storico delle richieste riesce a capire se autorizzare o meno determinate azioni. E' limitato solo da ciò che è computabile, quindi è in grado di applicare qualsiasi regola riusciamo a programmare

*Sandbox*
Se il firewall nota un codice in entrata sospetto, lo esegue in un ambiente isolato limitandogli l'accesso alle risorse

**Differenza tra Proxy Gateway Firewall**
- Firewall: monitora e controlla il traffico di rete in base a regole predefinite. Il traffico passa in entrata e in uscita passa per il firewall. Viene inserito tra la rete locale e internet per stabilire un collegamento controllato.
- Gateway: è un server intermedio che agisce come intermediario tra gli utenti e internet. Media il traffico tra client e server per migliorare la sicurezza, anonimato e prestazioni. A livello applicazione viene contattato da un utente che viene identificato e poi contatta l'applicazione sull'host remoto, mettendo in contato utente e applicazione. A livello di circuito mette in contatto due utenti con due connessioni TCP (uno tra host interno e sé stesso e una tra sé stesso e l'host esterno). Non esamina il contenuto dei dati, ma controlla quali connessioni sono consentite

**Spoofing**
Consiste nell'uso di indirizzi falsificati nei pacchetti. Alcuni di questi indirizzi potrebbero corrispondere a sistemi reali che potrebbero rispondere con pacchetti di errore poiché non si aspettavano di ricevere quei pacchetti di risposta. Il risultato è un aumento di traffico diretto verso il sistema bersaglio. 
L'uso di pacchetti del genere rende difficile identificare il sistema attaccante

**Intrusion detection**
E' un dispositivo dedicato esclusivamente a monitorare le attività per identificare eventi sospetti o malevoli.
Le sue funzioni sono:
- monitoraggio utenti
- controllo approfondito delle configurazioni per scovare vulnerabilità
- controllo integrità dei file
- analisi statistica pe scovare comportamenti anomali

I suoi obiettivi sono essere veloce, accurato, semplice e operare in tempo reale nascondendo la propria presenza agli attaccanti.
L'accuratezza è misurata tramite:
- falsi positivi
- falsi negativi
Gli amministratori devono trovare il giusto bilanciamento dei due problemi.

Tecniche di scanning IDS:
- *Signature based*: usa il pattern matching cercando corrispondenze tra firme di attacchi noti. Un problema di questi IDS è che la firma non esiste nel database. L'IDS è cieco e inoltre l'attaccante può ingannare l'IDS inserendo pacchetti spazzatura per sfasare la firma
- *Heuristic/Anomaly-based*: costruisce un modello del comportamento normale e fa scattare gli allarmi ogni volta che avviene un'eccezione. Per farlo impara nel tempo tramite tecniche di Machine Learning e Intelligenza Artificiale

**Intrusion Prevention System IPS**
E' quando un IDS ha la capacità di agire e bloccare attivamente i danni di cui si accorge, prende il nome IPS.
L'IPS può rispondere in 4 modi:
- Non intervenire attivamente, ma aumentare l'acquisizione dei dati per studiare l'attaccante senza farsi notare
- Mandare allerte a altri componenti protettivi della rete
- Richiedere l'intervento di un amministratore
- Modifica in tempo reale la rete per fermare la minaccia

$$ risultato = P_{max} \land \forall P \in PAESE ( |Mucchietto(P_{max})| \ge |Mucchietto(P)| ) $$
