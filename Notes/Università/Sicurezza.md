>[!info] Sicurezza informatica
>E' l'insieme delle misure e dei controlli che assicurano confidenzialità, integrità e disponibilità degli asset di un sistema informativo (hardware, software, firmware e informazioni).

**Confidenzialità**
Previene la divulgazione non autorizzata delle informazioni.
- *Confidenzialità dei dati*: assicura che le informazioni private non siano rese disponibili a individui non autorizzati
- *Privacy*: assicura che un individuo abbia il controllo su chi può accedere ai dati

**Integrità**
Proteggere il sistema da una modifica impropria del sistema. 
Garantisce la *non-ripudiabilità* (essere in grado di capire chi ha compiuto un'azione)
- *Integrità dei dati*: assicura che i dati non devono vengano compromessi
- *Integrità del sistema*: assicura che il sistema esegua le sue funzioni senza manipolazioni non autorizzate (es. un software che deve sempre svolgere ciò per cui è stato programmato)

**Disponibilità**
Assicurarsi che sia possibile accedere in modo rapido a informazioni e dati erogati da un sistema (riduzione degli accessi al sistema o servizi per accedere agli accessi).

Questi tre obiettivi sono stati integrati con altri due:
- **Accountability**: Permette di tracciare univocamente le azioni di un'entità (supporta la *non-ripudiabilità*, l'isolamento dei guasti e il rilevamento delle intrusioni) .
- **Autenticità**: autenticità delle informazioni che provengono da una sorgente. Significa verificare che gli utenti siano chi dicono di essere e che gli input provengano da fonti attendibili .

Qualora questi obiettivi venissero vilati, l'impatto per l'organizzazione si classifica in:
- *Basso*: effetto è limitato. Le funzionalità sono ridotte in modo percettibile ma non eccessivamente. Il danno che viene fatto all'asset è minore, la perdita finanziaria è bassa
- *Moderato*: effetto serio. Il danno che viene fatto all'asset è significativo, la perdita finanziaria è significativa 
- *Elevato*: effetto severo o catastrofico. Sono compromesse le funzionalità principali (es. attacco hacker in sapienza)

>[!info] Esempi
>- Impatto basso: Divulgazione di una directory pubblica oppure compromissione di un pool anonimo online. 
>- Impatto moderato: Compromissione di un forum oppure perdita della disponibilità di un portale che dà informazioni agli studenti.
>- Impatto elevato: Compromissione del database di un ospedale, cambiando le informazioni di un paziente.

### Sfide del cybersex (rivedi i punti)

1. La sicurezza non è semplice come sembra.
2. Bisogna sempre considerare i potenziali attacchi quando si progetta una difesa.
3. Le procedure di sicurezza sono spesso controintuitive.
4. Bisogna determinare il corretto posizionamento logico e fisico delle difese.
5. Richiede la gestione sicura di segreti (es. chiavi crittografiche).
6. *Asimmetria:* L'attaccante deve trovare una sola debolezza, il difensore deve trovarle ed eliminarle tutte per avere una sicurezza perfetta.
7. Spesso la sicurezza è un ripensamento aggiunto a fine progetto, invece di essere integrata fin dall'inizio.
8. Richiede monitoraggio regolare e costante.
9. Gli utenti percepiscono poco il beneficio degli investimenti in sicurezza finché non avviene un disastro.
10. La sicurezza forte è spesso vista come un ostacolo all'usabilità del sistema.

>[!note] Modello del cybersex
>Il modello relazionale della sicurezza si basa su questi concetti chiave:
>- *Asset*: hardware, software, dati, reti. Hanno un valore per i proprietari
>- *Vulnerabilità*: Una debolezza nel sistema o nelle procedure che può essere sfruttata da una minaccia. Le risorse possono essere corrotte (integrità), divulgate (confidenzialità) o rese indisponibili (disponibilità)
>- *Avversario*: L'entità (individuo o gruppo) che ha l'intento di condurre attività dannose
>- *Minaccia*: qualsiasi circostanza con il potenziale di avere un impatto negativo sugli asset sfruttando una vulnerabilità
>- *Attacco*: azione malevola effettiva che tenta di compromettere il sistema (è la minaccia che si concretizza)
>- *Contromisura*: dispositivo o tecnica per prevenire o mitigare gli attacchi e ridurre il rischio
>- *Rischio*: misura dell'entità della minaccia
> $$
>R = P \times D
>$$
>	Dove:
>	- $P$ è la probabilità di minaccia
>	- $D$ è il danno

>[!info] Classificazione degli attacchi
>- **Passivi:** tentano di apprendere informazioni senza alterare il sistema (es. intercettazione, analisi del traffico) .
>- **Attivi:** tentano di alterare il sistema o le operazioni . Si dividono in :
>	- _Replay:_ cattura e ritrasmissione non autorizzata di dati
>	- _Masquerade (Mascheramento):_ un'entità finge di esserne un'altra per ottenere privilegi
>	- _Modification of messages:_ alterazione, ritardo o riordino di messaggi legittimi
>	- _Denial of Service (DoS):_ previene o inibisce l'uso normale delle reti (es. sovraccaricando il sistema)
>- **Insider/Outsider:** a seconda se l'attaccante si trovi all'interno o all'esterno del perimetro di sicurezza

---
### Contromisure

Hanno l'obiettivo di minimizzare le minacce a un sistema.
Si distinguono contromisure di carattere:
- Tecnico
- Funzionale: relative alla gestione della sicurezza

*Tecniche*
- Controllo degli accessi per far si che solo le persone autorizzate possano accedere al sistema.
- Identificazione e autenticazione per verificare l'entità
- Protezione dei sistemi e della comunicazione (system e network security).
- Integrità del sistema e delle informazioni

*Funzionali*
- Consapevolezza e formazione
- Controllo e responsabilizzazione: periodicamente devo verificare che siano rispettati processi e che le misure per la gestione della sicurezza siano funzionanti.
- Certificazione, accreditamento e valutazione della sicurezza
- Pianificazione dell'emenrgenza: piano per gestire un'emergenza
- Manutenzione hardware e software
- Protezione fisica e ambientale
- Pianificazione delle attività relative alla sicurezza
- Sicurezza del personale (se il personale deve accedere a sistemi classificati prima si deve fare uno screening della storia del personale)
- Valutazione dei rischi che permette di stabilire le contromisure da applicare.
- Acquisizione di sistemi e servizi

**Requisiti di sicurezza misti**
- Gestione della configurazione
- Risposta agli incidenti
- Protezione dei dati

>[!info] Principi fondamentali della progettazione sicura dei sistemi
>- *Economy of mechanism*: il design deve essere il più semplice e piccolo possibile (facile da testare)
>- *Fail-safe default*: L'accesso deve basarsi sui _permessi_, non sulle _esclusioni_. Di default, l'accesso è negato
>>[!warning] Differenza tra esclusione e permesso
>>``` C
>>DWORD dwRet = IsAccessAllowed(...);
>>if (dwRet == ERROR_ACCESS_DENIED){
>>	//SECURITY CHECK FAILED
>>	//INFORM USER TAHT ACCESS IS DENIED
>>} else {
>>	//SECURITY CHECK OK
>>}
>>```
>>Questo codice usa la logica dell'esclusione. Il programma blocca l'accesso solo se la funzione
>>`IsAccessDenied()` da come output `ERROR_ACCESS_DENIED`.
>>Un hacker potrebbe intenzionalmente causare un errore nel sistema per bypassare il
>>controllo. Questo perché se la funzione `IsAccessDenied()` desse come output un altro
>>errore (Es. `ERROR_INVALID_PARAMETER` se viene inserito un parametro malformato), il valore
>>di ritorno non sarà `ERROR_ACCESS_DENIED`, l'`if` fallirebbe e l'esecuzione salterebbe
>>direttamente nell'`else`.
>>
>>Per applicare la logica del *permesso* (whitelist), dobbiamo rovesciare la condizione: di default l'accesso è negato, a meno che non si abbia esplicitamente il permesso.
>>```C
>>DWORD dwRet = IsAccessAllowed(...);
>>if (dwRet == SUCCESS_ACCESS_GRANTED) { 
>>	// Security check OK
>>} else {
>>	// Security check failed.
>>}
>>```
>>
>- *Complete mediation:* ogni accesso deve essere controllato dal meccanismo di sicurezza (evitare di basarsi solo sulla cache)
>- *Open design*: la sicurezza non deve basarsi sulla segretezza dell'algoritmo, ma della chiave .
>- *Separation of privilege*: richiedere attributi multipli per l'accesso (es. MFA - Multi Factor Authentication)
>- *Least privilege*: ogni utente/processo deve operare con i privilegi _minimi_ necessari per svolgere il proprio compito
>- *Layering (Defense in Depth)*: uso di barriere multiple e sovrapposte. Se una fallisce, le altre proteggono il sistema
>- *Psychological acceptability*: la sicurezza non deve interferire troppo con il lavoro degli utenti

>[!info] Superficie di attacco
>E' l'insieme di tutte le vulnerabilità raggiungibili in un sistema.
>Si divide in:
>- *Rete*: porte aperte e server esposti
>- *Software*: bug nel codice
>- *Umana*: social engineering o errore del personale
>A seconda della superficie di attacco si mette in relazione la
>superficie di attacco al layering
>Quando la superficie di attacco comincia a crescere si devono avere più livelli di sicurezza per proteggere il sistema.

>[!info] Alberi di attacco 
>![[Pasted image 20260302172245.png|100]]
>Struttura dati gerarchica che rappresenta un insieme di tecniche
>per sfruttare le vulnerabilità di sicurezza.
>- Il nodo radice è l'obiettivo dell'attaccante
>- I nodi intermedi sono i sotto-obiettivi
>- Le foglie sono gli attacchi che può fare per colpire un sotto-obiettivo
>	- I sotto-obiettivi possono esser in AND o OR tra loro
>Sono utilizzati dai team di sicurezza per capire qual è il percorso "più economico" o "più facile" per un attaccante.

---
# Crittografia

### Cifratura a chiave simmetrica

E una tecnica crittografica che garantisce la *confidenzialità* dei dati.

**Overview**
Mittente e destinatario devono condividere la stessa chiave segreta $K$,  per scambiare messaggi.

I suoi elementi sono:
- Un forte algoritmo crittografico
- Condivisione sicura della chiave

![[Pasted image 20260302125103.png|400]]

I principali tipi di attacco a questa tecnica sono:
- *Crittoanalisi*: sfruttare la natura matematica dell'algoritmo o se si conoscono delle caratteristiche del testo non cifrato per dedurre la chiave
- *Forza bruta*: di provano tutte le possibili chiavi fino a ottenere un testo sensato

>[!notes] Distribuzione delle chiavi
>Il punto debole decifratura a chiave simmetrica è la tecnica di distribuzione della chiave, perché non è possibile scambiare la chiave in modo sicuro se il canale non è protetto.
>Questo problema viene risolto con la *crittografia simmetrica*

Tra i principali algoritmi per la crittografia a chiave simmetrica troviamo:
- **DES (Data Encryption Standard)**: utilizza blocchi da 64 bit e una chiave da 56 bit che lo rende, però, molto debole contro i moderni processori di oggi
- **3DES (Triple DES)**: ripete il DES 3 volte usando 2 o 3 chiavi diverse, portando la lunghezza effettiva della chiave a 112 o 168 bit. I problemi principali sono che è molto lento e usa ancora blocchi piccoli da 64 bit
- **AES (Advanced Encryption Standard)**: sostituisce il 3DES poiché molto efficiente. La dimensione del blocco è di 128 e le dimensioni delle chiavi possono essere da 128, 192 o 256 bit.

L'AES utilizza l'architettura *Rijndael* che applica le sue trasformazioni all'intero blocco di 128 bit simultaneamente organizzandolo in una matrice. Questa struttura è ottimizzata per eseguire calcoli paralleli ed è adatta a processori moderni.
Gli algoritmi DES e 3DES utilizzano la *rete di Feistel* che divide il blocco a metà e, a ogni passaggio, cripta solo metà alla volta incrociandola con l'altra.
#### Tipologie di cifratura simmetrica

- *Block cipher*: cifra il testo elaborando un blocco alla volta, può riutilizzare le chiavi ed è il più comune
- *Stream cipher*: cifra il flusso di dati continuamente un byte alla volta, generando un flusso pseudocasuale. E' molto più veloce e usa meno codice
- *ECB (electronic codebook)*: è la modalità base per usare i cifrari a blocchi su messaggi lunghi. Ogni blocco viene cifrato singolarmente con la stessa chiave. Il problema legato a questo metodo è che se il testo in chiaro ha delle regolarità, allora queste appariranno anche nel testo cifrato

#### Autenticazione dei messaggi
La cifratura dei messaggi protegge dalla lettura non autorizzata, ma non dalla manomissione (attacchi attivi).
Con l'autenticazione, invece, garantiamo che il contenuto non venga alterato e la legittimità della fonte.

Si utilizza il **MAC (Message Authentication Code)**.
Attraverso la chiave $K$ e il messaggio $M$ si calcola un "tag":
$$
MAC=(K,M)
$$
Dopo aver calcolato il $MAC$ con la stessa chiave segreta, se il destinatario ottiene lo stesso risultato, allora ha la garanzia che il messaggio non sia stato modificato.

![[20260306-152331.jpg|500]]

Possiamo distinguere in autenticazione:
- *Con confidenzialità*: il messaggio è sia cifrato che autenticato, quindi il tag viene cifrato
- *Senza confidenzialità*: messaggio non cifrato e il tag viene semplicemente aggiunto al messaggio

L'autenticazione e la cifratura sono due funzioni che vengono eseguite separatamente.
#### Funzione Hash

Una funzione Hash $H(M)$ è un'alternativa al $MAC$ che non richiedere una chiave in input.
Prende un messaggio di dimensione variabile e restituisce un'impronta di dimensione fissa.
Per essere sicura, una funzione Hash deve:
1. essere applicabile a blocchi di qualsiasi dimensione
2. avere codice costante
3. essere una funzione efficiente dal punto di vista computazionale
4.  essere *one way* o *resistente alla preimage* (non deve essere invertibile)
5. avere resistenza debole alle collisioni ($H(y)=H(x)$). Deve essere impossibile avere due valori che danno lo stesso hash. Proprietà intrinseca della funzione e la probabilità di collisione è minima
6. Anche modificando un byte di un messaggio, cambia il valore dell'hash

**One-Way Hash function + Symmetric Encryption**

![[20260306-205602.jpg|600]]


**One-Way Hash function + Public Key Encryption**

![[20260306-232254.jpg|700]]


**One-Way Hash function + Secret value (no encryption)**

![[Pasted image 20260306233153.png|200]]

![[20260306-235324.jpg|700]]

Non è necessario utilizzare algoritmi per criptare/decriptare, per cui si risparmia nella computazione.
Il mittente calcola:
$$MD_{M} = H(K \space || \space M \space || \space K)$$
Dove:
- $M$ è il messaggio in chiaro
- $K$ è la chiave simmetrica
- $H()$ è la funzione di hash
- $MD_{M} \text { (Message Digest)}$ è il risultato prodotto della funzione hash

Ciò che viene inviato e $MD_{M} \space || \space M$, cioè il prodotto della funzione hash, concatenato al messaggio in chiaro.
Infine, il destinatario, che conosce $K$, calcola $MD_{M} = H(K \space || \space M \space || \space K)$ e la confronta con $MD_{M}$ per verificare l'integrità del messaggio.

### Crittografia a chiave pubblica (asimmetrica)

Risolve principalmente il problema della distribuzione della chiave. 
Viene utilizzata una coppia di chiavi matematicamente collegate tra loro, una *privata* e una *pubblica*, che garantiscono:
- *Confidenzialità*: il messaggio verrà cifrato con la chiave pubblica del mittente, che sarà in grado di decifrare il messaggio con la sua chiave privata
- *Autenticazione*: l'hash viene cifrato con la chiave privata del mittente e il destinatario decifrerà l'hash utilizzando la chiave pubblica del mittente, garantendone l'autenticità

Per i seguenti esempi e schemi, supponiamo di avere una situazione in cui il mittente Bob vuole mandare un messaggio al destinatario Alice.

![[Pasted image 20260308163330.png|600]]

Tra i principali algoritmi a chiave asimmetrica troviamo:
- *RSA*: utilizzato per la cifratura, firme digitali e scambio di chiavi
- *Diffie-Hellman*: serve **solo** per permettere a due entità di generare una chiave simmetrica condivisa attraverso un canale sicuro.
- *DSS (Digital Signature Standard)*: garantisce firma digitale con **SHA-1**
- *ECC (Elliptic Curve)*: sicuro quanto RSA , ma usa chiavi più corte. Perciò, è più veloce e leggero

![[Pasted image 20260308163806.png|500]]

>[!info] Qual è l'importanza della chiave asimmetrica?
>La crittografia asimmetrica e molto lenta dal punto di vista computazionale, rispetto a quella a chiave simmetrica. 
>Nella pratica, viene utilizzata solo all'inizio della comunicazione per lo scambio sicuro di una chiave simmetrica temporanea. 
>Dopodiché, il resto della comunicazione avviene attraverso la cifratura simmetrica *AES*.

---
### Firma digitale

Si intendono quegli algoritmi che ci permettono di verificare l'autenticità del mittente di un messaggio, la sua integrità e la non-ripudiabilità.
L'idea è quella di creare un pacchetto di dati che accompagna i messaggio. Per fare questo, vengono utilizzati algoritmi di cifratura (*DSA*, *RSA* e *Algoritmi a curva ellittica ECDSA*).

![[Pasted image 20260308172757.png|450]]

Il mittente calcola l'hash del messaggio, che verrà cifrato e inviato insieme al messaggio in chiaro.
Il destinatario, invece, calcola l'hash del messaggio in chiaro, decifra l'hash ricevuto con la chiave pubblica del mittente e, infine, confronta i due hash.

La natura stessa della crittografia asimmetrica richiede che la chiave pubblica sia distribuita liberamente a tutti. 
Tuttavia, il grande svantaggio è che chiunque può falsificare l'annuncio pubblico di una chiave. Un attaccante potrebbe fingere di essere il mittente legittimo (ad esempio Bob) e diffondere una propria chiave pubblica spacciandola per quella di Bob.
Se questo accade, l'attaccante sarà in grado di leggere tutti i messaggi cifrati destinati a Bob e potrà utilizzare queste chiavi contraffatte per autenticarsi falsamente al suo posto.

Per risolvere questo problema, si utilizza un *certificato a chiave pubblica*, che sono composti da:
- chiave pubblica da distribuire
- informazioni sul possessore della chiave (ID)
- informazioni sul verificatore dell'identità *Certification Authority* (ad esempio Aruba, Poste Italiane,...), cioè un'entità fidata che si occupa di verificare l'appartenenza delle chiavi
- periodo di validità

**Creazione del certificato**

![[Pasted image 20260308175514.png|400]]

L'utente:
1. crea la coppia di chiavi (pubblica e privata)
2. prepara un certificato non verificato che include il suo ID e la sua chiave pubblica
3. fornisce questo certificato a una *CA* in modo sicuro

La *Certification Authority*: 
- firma il certificato:
	- usando una funzione di hash su tutto il certificato
	- generando una firma digitale con la propria chiave privata
- allega la firma digitale al certificato non verificato
- invia il certificato verificato dall'utente

![[Pasted image 20260308175103.png|400]]

Ora, il certificato può essere pubblicato dall'utente e chiunque può verificarlo utilizzando la chiave pubblica della *CA*.

Il destinatario, calcola l'hash del certificato, a esclusione della firma.
Attraverso la chiave pubblica della *CA*, decifra la firma e la confronta con l'hash calcolato precedentemente, per verificare l'autenticità del mittente.

#### Digital Envelop

Utilizzare algoritmi a chiave asimmetrica è molto pesante dal punto di vista delle prestazioni.
Per alleggerire il sistema e mantenere comunque una trasmissione sicura viene utilizzata una chiave simmetrica che verrà poi utilizzata per il resto della conversazione.

![[Pasted image 20260310165101.png|500]]

1. Viene preparato il messaggio da inviare
2. Si genera una chiave simmetrica casuale che verrà utilizzata *solo* in questa comunicazione
3. Il messaggio viene cifrato con la chiave generata precedentemente
4. La chiave viene cifrata utilizzando la chiave pubblica del destinatario
5. La chiave cifrata viene allegata al messaggio e inviata al destinatario

![[Pasted image 20260310165511.png|500]]

Il destinatario dovrà:
1. decifrare la chiave simmetrica che era stata allegata al messaggio
2. decifrare il messaggio con la chiave ottenuta

#### Numeri casuali

Vengono molto usati nella crittografia in algoritmi a chiave pubblica o cifratura a flusso.
Devono rispettare le proprietà di *casualità* e *non predicibilità*.  

**Casualità**
- *Distribuzione uniforme*: la frequenza con cui un numero viene generato deve essere circa la stessa per tutti gli altri numeri
- *Indipendenza*: non deve essere possibile prevedere la sequenza di numeri generati

**Non predicibilità**
Ogni numero è statisticamente indipendente dagli altri numeri nella sequenza. Infatti, un attaccante non deve essere in grado di predire i numeri futuri basandosi su quelli già usciti.

Dato che avere dei numeri casuali puri è molto difficile, si devono generare dei numeri *pseudo-casuali*, cioè delle sequenze che soddisfano statisticamente un *random test*.
Per ottenere questi numeri ci si basa su delle fonti non deterministiche (per esempio gli *Hardware RNG*, ovvero delle statistiche come la temperatura, il jitter dei circuiti o i quantum effects).

---
### Cifratura simmetrica e confidenzialità dei messaggi

**Struttura di Feistel**
All'interno di ogni round vengono fatte le stesse operazioni.
Ogni round lavora con una chiave diversa.
fai bene appunti

**AES**
Struttura a round ma non segue l'architettura di Feistel
A partire dalla prima chiave vengono generate delle sottochiavi.

Data la chiave di partenza, viene espansa in un array di 44 parole a 32 bit.
Ciò che rende l'algoritmo sicuro sono le operazioni di sostituzione e trasposizione.

La sostituzione avviene attraverso una matrice di sostituzione.
Ogni byte vedo il suo equivalente in esadecimale e vedo le colonne e le righe.
La sostituzione viene memorizzata nell'array.
Dopodiché vengono mischiate le varie righe della matrice con lo shift.
Il risultato viene inserito nell'array di stato.
Vengono mischiate le colonne e si fa uno xor con le righe mixate.

Per la generazione della chiave.
L'algoritmo prende come input 4 parole da 16 byte ciascuna e produce un array lineare da 44 parole.

#### Stream cipher (cifratura a flusso)

Cifra byte continuamente.
Genera delle sequenze di chiavi che cambiano continuamente.
La complessità risiede nell'algoritmo per generare le chiavi.

L'input è una chiave e un byte che voglio cifrare.
La sequenza è equivalente a una sequenza di numeri pseudo-casuali.
La cifratura avviene solo mediante uno xor.

**RC4**
Dimensione variabile della chiave.
Algoritmo estremamente veloce.

Tre fasi
1. Inizializzazione
2. Permutazione
3. Generatore di stream

**Inizializzazione**
Si prende una chiave usata per inizializzare un vettore di stato di 256 byte.
Il vettore contiene le permutazione dei bit della chiave e per riempire il vettore viene fatto un for in cui si prende un elemento della chiave in cui si 

**Permutazione vettore S**
Si usa il vettore T generato dalla chiave.
Inverto gli elementi del vettore S
(vedi codice nelle slides)

---
### Modalità di cifratura

#### Electronic codebook (ECB) mode

E' il modo più semplice per cifrare.
Ogni blocco è cifrato utilizzando la stessa chiave.

E' vulnerabile perché se ho un testo lungo, perché si possono avere dei plaintext ripetuti.

#### Cipher block chaining mode

Introduzione dell'entropia. 
Messaggio suddiviso in n blocchi e ogni blocco viene cifrato con la stessa chiave, ma vado a modificare l'input dell'algoritmo di cifratura.
Non cifro mai il plaintext così com'è, ma lo metto in xor con un vettore di inizializzazione.

Nella decifratura prendo il primo blocco cifrato e lo metto in xor con il vettore di inizializzazione

**Vettore di inizializzazione**
Ha una dimensione pari a quella del blocco. 



Il problema principale del ECB è che si potrebbero propagarsi degli errori nel plaintext.
Se viene introdotto un errore in un blocco, si propagherà nel blocco cifrato.

Nel CBC l'errore si propaga in tutto il plaintext.

#### Counter mode

L'idea è di utilizzare la chiave per la cifratura + un contatore.
Poi, si fa lo xor tra la parte cifrata e il blocco del plaintext.


#### Cipher feedback mode

Registro a scorrimento che viene inizializzato con un vettore di inizializzazione.

---
#### Criptoanalisi

E' il processo che serve per scoprire la chiave o il plaintext.

**Attacco di ciphertext**
- Attacco di forza bruta: si provano tutte le possibili chiavi
- Analisi del testo cifrato: si deve avere un'idea del tipo di plaintext (lingua, estensione del file,...)

