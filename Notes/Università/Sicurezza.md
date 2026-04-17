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

E' il metodo convenzionale di cifratura. Si compone di 5 elementi fondamentali:
- *Plaintext*: il testo in chiaro da dare all'algoritmo
- *Encryption algorithm*: algoritmi che effettua sostituzioni e trasformazioni al plaintext
- *Secret key*: chiave data in input all'algoritmo, da cui dipendono tutte le operazioni effettuate nell'algoritmo
- *Ciphertext*: il testo di output dell'algoritmo. Utilizzando chiavi diverse per ogni testo, si ottengono risultati diversi
- *Decryption algorithm*: l'algoritmo di cifratura inverso. Dato il ciphertext e la chiave, deve dare in output il plaintext

#### Sistemi crittografici

Meccanismi che utilizzano algoritmi, chiavi e protocolli per proteggere la confidenzialità, l'integrità, l'autenticità e la non-ripudiabilità.

Sono classificati su *3 dimensioni*

**Operazioni per la cifratura del plaintext**
- *Sostituzione*: vengono presi un insieme di byte e rimpiazzati con altri
- *Trasposizione*: i byte del testo vengono mischiati tra loro

Queste operazioni sono indipendenti dalla chiave e vengono ripetute un certo numeri di volte (*round*) sul testo.
Quando vengono effettuate, è importante non perdere informazione. Perciò, le operazioni devono essere invertibili.

**Tipologia di chiavi**
- Simmetrica
- Asimmetrica

**Gestione del plaintext**
- *Blocco*: i blocchi vengono processati uno alla volta. Da un blocco in input otteniamo un blocco in output
- *Stream*: l'input viene continuamente processato. Ogni elemento ne produce uno in output

#### Block cipher

I meccanismi di cifratura simmetrici a blocchi consistono in una serie di *round*. Ogni round è composto da *sostituzioni* e *permutazioni* basai su una chiave.

Una delle strutture più famose è la *Struttura di Feistel*, utilizzata anche nell'algoritmo DES.

>[!info] Idea
>- All'interno di ogni round vengono effettuate le stesse operazioni
>- A partire da una chiave, a ogni round, vengono generate chiavi diverse

![[20260311-164842.jpg|500]]

Per progettare una struttura di cifrario a blocchi dobbiamo considerare diverse parametri:
- *Block size*: se il blocco è grande si ha più sicurezza, ma meno velocità nelle operazioni. Un trade-off ottimale è 128-bit
- *Key Size*: più è grande e più è alta la sicurezza, però si riduce la velocità delle operazioni. Il trade-off ottimale è tra i 128 e 256 bit
- *Numero di round*: all'aumentare del numero di round, aumenta la sicurezza. Il trade-off ottimale è di 16 round
- *Algoritmo di generazione delle sotto-chiavi*: più è complesso, più è difficile fare criptoanalisi
- *Funzione utilizzata nei round*: più è complesso, più è difficile fare criptoanalisi
- *Velocità dell'algoritmo di cifratura/decifratura*

L'algoritmo deve essere facile da analizzare, perché serve a individuare meglio le vulnerabilità. Tuttavia, le componenti dell'algoritmo devono essere tali da impedire la criptoanalisi, anche se si è a conoscenza delle componenti stesse.

>[!note] Criptoanalisi
>Processo utilizzato per cercare di scoprire il testo in chiaro o la chiave, sfruttando soltanto la conoscenza dell’algoritmo di cifratura. Conoscendo quest’ultimo e i suoi punti deboli, si cerca di risalire al testo in chiaro

#### Data Encryption Standard (DES)

In questo algoritmo, il processo di cifratura è composto da:
- *Block cipher* con blocchi da 64 bit e chiavi da 56 bit
- Una variante della struttura di Feistel composta da 16 round
- Una chiave a 56 bit da cui vengono generate delle sotto-chiavi

Il processo di decifratura è l'inverso della cifratura. Prende il input il ciphertext e usa le sotto-chiavi in ordine inverso (per esempio, la sotto-chiave $K_{16}$ viene usata per la prima iterazione, $K_{15}$ sulla seconda iterazione,..., $K_{1}$ sulla sedicesima iterazione).

#### 3DES

E' un'evoluzione del DES e presenta le seguenti caratteristiche:
- Estende la chiave fino a 168 bit, suddividendola in tre chiavi da 56 bit
- La cifratura avviene in modo sequenziale utilizzando le tre chiavi (applicando, quindi, il DES tre volte)
- Per la decifratura, si utilizza l'algoritmo inverso

![[Pasted image 20260313120220.png|500]]

Definiamo:
- $E$ la funzione di decifratura
- $D$ la funzione di decifratura
- $K$ la chiave
- $C$ il ciphertext
- $P$ il plaintext

$$
C = E(K_{3}, D(K_{2}, E(K_{1}, P)))
$$
$$
P = D(K_{1}, E(K_{2}, D(K_{3},C)))
$$

#### Advanced Encryption Standard (AES)

Utilizza blocchi da 128 bit e chiavi da 128, 192, 256 bit.
Prende in input un blocco da 128 bit, rappresentato come una matrice di byte.
Durante l'esecuzione dell'algoritmo, il blocco viene copiato nello *state array* che viene modificato a ogni stage di cifratura o decifratura.
Dopo l'ultimo stage l'array viene copiato in una matrice di output.
Anche la chiave è rappresentata come una matrice, che viene estesa in un array di words. Ogni word è composta da 4 bytes e l'array in totale contiene 44 words e all'aumentare dei bit della chiave, aumentano anche le words nell'array.

![[Pasted image 20260316112411.png|300]]

Da notare che l'ordine segue le colonne. Quindi, i primi 4 bytes del plaintext occuperanno la prima colonna della matrice.

Caratteristiche dell'AES:
- Non segue l'architettuare di Feistel
- La chiave iniziale viene estesa in un array di 44 words da 32 bit di cui 4 words (128 bit) costituiscono una chiave utilizzabile in un round
- Presenta 4 stages: 1 di permutazione e 3 sostituzioni
	- *Substitute bytes*: utilizza delle tabelle per fare sostituzioni byte a byte
	- *Shift rows*: permutazione effettuata sulle righe
	- *Mix Columns*: sostituzione che altera ogni byte in una colonna smistandoli sulle restanti colonne
	- *Add round key*: una xor del blocco corrente con la chiave del round corrente

![[Pasted image 20260316122109.png|400]]

La cifratura inizia con una *Add Round Key* seguita da 9 round contenenti tutti gli stage, seguiti infine da un round di tre stage.

![[Pasted image 20260319112230.png|500]]

Solo lo stage *Add Round Key* utilizza la chiave, perciò, viene svolto all'inizio e alla fine della cifratura. Tutti gli altri stage, invece, servono a "creare confusione" nei dati, ma sono invertibili anche senza conoscere la chiave 

L'algoritmo di decifratura utilizza le funzioni inverse degli stage. Per la round key, viene utilizzata la chiave estesa in ordine inverso e messa in XOR.

**1. Substitute Bytes**

![[Pasted image 20260319113750.png|500]]

E' una sostituzione byte a byte del blocco attraverso una tabella. Esiste anche una matrice per la decifratura e dovrà essere progettata per avere poca correlazione tra in input e di output.
Inoltre, non deve essere possibile definire una relazione matematica per capire l'output dall'input.

![[Pasted image 20260319114050.png|500]]

I primi 4 bit vengono usati per la coordinata $x$, mentre gli ultimi 4 per la coordinata $y$.
Per esempio, il byte con rappresentazione esadecimale 95 verrà tradotto in $2A$, cioè il byte presente in $(9,5)$. 

A questo punto, il risultato viene salvato nello state array per poi passare all'operazione successiva.

**2. Shift Rows**

![[Pasted image 20260319114505.png|500]]

- La prima riga non viene modificata
- La seconda viene spostata di un byte a sinistra
- La seconda viene spostata di 2 byte a sinistra
- La seconda viene spostata di 3 byte a sinistra

Gli shift sono circolari, quindi gli elementi che arrivano al limite sinistro, "sbucano" all'estremità destra (tipo effetto Pac-Man).
Questa operazione si assicura che i 4 byte di una colonna vengano smistati in 4 colonne diverse.

A questo punto, il risultato viene salvato nello state array per poi passare all'operazione successiva.

**3. Mix Column**

![[Pasted image 20260319121400.png|500]]

Vengono presi in input i 4 byte di una colonna e si ottengono nuovi 4 byte in output. Durante questa operazione non ci deve essere perdita di informazioni.

A questo punto, il risultato viene salvato nuovamente nello state array per poi passare all'operazione successiva.

**Add Round Key**

![[Pasted image 20260319121705.png|500]]

- Prende in input la chiave composta da 4 words (16 byte - 128 bit)
- Restituisce in output un vettore da 44 words (156 byte), sufficienti per garantire il numero di chiavi necessario per tutti i round

Le prime 4 words vengono utilizzate per il primo add round key, e le restanti 40, nei 40 successivi 10 round.
All'aumentare della lunghezza della chiave, aumentano anche i round.

Prima viene copiata la chiave nelle prime 4 words dell'array esteso, poi, il resto viene riempito con 4 words alla volta, dove `word[i]` dipende da `word[i-1]` e `word[i-4]`.

Esistono diversi algoritmi *finite-field* per generare la chiave estesa.

![[Pasted image 20260319144102.png|400]]

#### Stream cipher (cifratura a flusso)

L'idea è quella di cifrare byte continuamente.
La complessità risiede nell'algoritmo per generare le chiavi, infatti, genera delle sequenze di chiavi che cambiano continuamente.

L'input è una chiave e un byte che voglio cifrare.
La sequenza è equivalente a una sequenza di numeri pseudo-casuali.
La cifratura avviene solo mediante una XOR.

>[!note] Seed
>Viene utilizzato lo stesso concetto dei seed per i generatori di numeri. Se utilizziamo lo stesso seed otteniamo in output la stessa sequenza di numeri

#### RC4

Utilizza una chiave di lunghezza variabile da 1 a 256 bytes che viene usata per inizializzare lo *state array* $S$ di 256 byte.
In ogni momento dell'algoritmo avremo che $S$ contiene una permutazione di tutti i numeri a 8 bit, cioè di tutti i numeri da 0 a 255.
Per la cifratura e decifratura, un byte $k$ viene generato da $S$ selezionando una delle 255 entries. Per ogni valore $k$ selezionato, viene effettuata una nuova permutazione dei valori di $S$.

Si compone di tre fasi:
1. Inizializzazione
2. Permutazione e swap
3. Generazione di stream

**Inizializzazione**
Viene inizializzato $S$ con tutti i valori da 0 a 255 tale che `S[0] = 0, S[1] = 2,...,S[255] = 255`.
Viene inizializzato un altro vettore $T$, se la lunghezza della chiave $K$ è 256 bytes, allora $K$ viene trasferita in $T$. Altrimenti, per una chiave di lunghezza $n$ bytes, i primi $n$ bytes di $K$ vengono copiati nel vettore $T$ e $K$ verrà ricopiata tante volte quanto necessario per riempire tutto $T$.

```
for i = 0 to 355 do
	S[i] = i;
	T[i] = K[i mod keylen];
```

![[20260322-162751.jpg|500]]

**Permutazione e Swap**
Per effettuare la permutazione si utilizza la seguente formula:
$$
j = (j+S[i]+T[i]) \space \space \space (mod \space 256)
$$
Il nuovo valore dell'indice $j$ è calcolato sommando il valore precedente di $j$, il valore corrente dello stato $S[i]$ e il byte corrispondente della chiave estesa $T[i]$.
L'operazione $mod \space 256$ garantisce la chiusura nell'intervallo degli indici validi per il vettore $S$ (cioè, assicura che il valore di $j$ non superi mai il valore 255).

Viene eseguito uno scambio dei valori: il valore all'indice $i$ viene scambiato con quello all'indice $j$.
$$
S[i] \leftrightarrow S[j]
$$
```
j = 0;
for i = 0 to 255 do
	j = (j + S[i] + T[i]) mod 255;
	Swap(S[i], S[j]);
```

![[20260322-162751 1.jpg|500]]

**Generazione di stream**

Dopo aver inizializzato il vettore $S$, la chiave in input non viene più utilizzata. La generazione degli stream consiste nell'iterare su $S$. Ogni elemento $S[i]$ viene scambiato con un altro elemento di $S$ basandosi sulla configurazione di $S$. 
Se raggiungiamo l’elemento in posizione 255 torniamo a 0.

```
i, j = 0;
while(true)
	i = (i + 1) mod 256;
	j = (j + S[i], S[j]) mod 256;
	Swap(S[i], S[j]);
	t = (S[i] + S[j]) mod 256;
	k = s[t];
```

![[IMG_0342.jpg|500]]

Per la cifratura viene calcola la XOR tra il valore $k$ con il byte successivo del plaintext.
Per decifrare, si calcola la XOR tra il valore $k$ e il byte successivo del cyphertext.

---
### Modalità di cifratura

Gli algoritmi a chiave simmetrica e a blocchi processano un blocco alla volta. Quando il testo è molto lungo è necessario spezzarlo in più blocchi.

![[Pasted image 20260326151236.png|500]]

#### Electronic codebook mode (ECB)

E' il modo più semplice per cifrare. Infatti, se i blocchi hanno dimensione $b$ bit, allora verranno processati $b$ bit alla volta cifrandoli sempre con la stessa chiave.
Per messaggi molto lunghi questa tecnica non è molto sicura. Le ripetizioni hanno la stessa cifratura, oppure sui messaggi molto strutturati è possibile effettuare la criptoanalisi (es. ogni pagina inizia con gli stessi header, allora si hanno già delle combinazioni da poter sfruttare).

#### Cipher block chaining mode (CBC)

In questa modalità di cifratura a blocchi, l'input dell'algoritmo è uno XOR del blocco contenente il plaintext corrente e il precedente blocco cifrato, utilizzando la stessa chiave.



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

---
### Secure Hash Algorithm

#### SHA-2

Il messaggio in chiaro ha una sua lunghezza l che va portata a una lunghezza di 1024 bit attraverso l'utilizzo di un buffer.
128 bit verranno presi dalla lunghezza del messaggio, se c'è altro spazio libero viene utilizzato un pudding per arrivare 896 bit.
Il messaggio viene suddiviso in blocchi ogni blocco viene dato in input a una funzione che fa 80 round.
L'out della funzione viene sommato all'hash dell'out della funzione del blocco successivo (vedi immagine per appunti)

La funzione prende altri valori in input. Dal messaggio vengono estratte delle parole a 64 bit che derivano dal blocco di cui stiamo calcolando l'hash.

FAAAHHH

All'interno di ogni round ci sono degli shift circolari e operatori and or not e xor.
All'ottantesimo round c'è una somma tra FAAHH

#### SHA-3

FAAAHH

#### HMAC key hashing for message authentication

Obiettivi:
- Poter utilizzare funzioni hash esistenti
- Permette di rimpiazzare FAHH
- Non FAAHH
- Gestisce le chiavi in modo semplice

- Il messaggio viene diviso in blocchi
- Prendere una funzione hash e la utilizza due volte
	- la prima volta sul messaggio originale
	- la seconda sull'hash del messaggio originale
- La chiave deve avere la stessa lunghezza di ogni blocco
	- se troppo lunga, viene tagliata
	- altrimenti viene messo del pudding
- La chiave viene messa in xor con dei parametri dati di default (*ipad*).
	- l'ipad FAAAHHH

---
### Cifratura a chiave pubblica

#### RSA

Requisiti:
- E' possibile trovare dei valori FAAAH

---
### Autenticazione

La base della sicurezza dei computer è controllare gli accessi.
Per autorizzare qualcuno a fare delle azioni, bisogna capire se quel qualcuno e chi dice di essere

Il soggetto può essere un umano o un non human identity (processo)

Dopo aver identificato il soggetto, bisogna autenticarlo

L'identità è una cosa nota e predicibile.
L'autenticazione non deve essere noto e non deve essere facile risalire all'identità

Meccanismi di autenticazione
- qualcosa che sai (password)
- qualcosa che l'utente è (biometrica)
- qualcosa che l'utente ha (token)

**Autenticazione con password**
Il più utilizzato ma introduce delle problematiche:
- autenticare il soggetto per qualsiasi azione e per un certo periodo
- se un attaccante riesce a ottenere la password dell'utente, potrà accedere al sistema
	- La contromisura è cambiare la password
- perdita di una password: sarà impossibile ritrovare quella password esatta, poiché le chiavi sono memorizzate sul sistema attraverso un hash

>[!info] Step che permettono a un attaccante di scoprire una pw
>- nessuna password
>- stesso nome dello User ID
>- derivato dello user ID
>- parole comuni come "password", "qwerty", "1234"
>- combinazioni varie delle parole comuni
>- forza bruta

Maggiore è il numero di tentativi, maggiore è la robustezza di una pw

>[!info] attacco a dizionario
>Molti siti pubblicano dei dizionari di frasi, nomi di personaggi, miti, parole cinesi...
>Esistono delle utility che cercano di scoprire se le password di un utente sonodsbhiifudhsbhiudsu

I sistemi operativi non salvano le pw in modo chiaro, ma utilizzano l'hash o la crittografia

Gli User ID sono scritte in una tabella.
FAAHH


**Come si riduce il rischio di un attacco?**
Il meccanismo è il SALT
Il salt è un campo extra  diverso per ogni utente.

L'utente definisce la pw che viene concatenata a sale e nome utente.
Dopodiché si calcola l'hash del valore ottenuto.

**Password cracking**
- Attacco a dizionario
- Attacco a rainbow table

#### Autenticazione biometrica

Problematiche:
- dato che il match deve essere veloce, non è molto accurato
- intrusiva
- una compromissione al database dei template, blocca il meccanismo

#### Autenticazione basata sui token

**Token attivi**
Possono avere qualche variabilità e interagiscono con una banda magnetica di trasmissioni radio

**Token statici**
Hanno sempre lo stesso valore
La maggiore debolezza è lo *skimming* (il token viene memorizzato)

La dinamicità permette maggiore sicurezza


#### Federate identity management

Vengono uniti sistemi di autenticazione separati.
C'è un identity manager che fa da proxy per tutti i sistemi a cui si vuole garantire un'autenticazione.

#### Single sign-on

Procedura che lavora per l'utente mantenendo i vari meccanismi separati
(vedi immagine slide)

Memorizza le credenziali per accedere

#### Multi factor authenticator

Ex. Autenticazione a due fattori.
La password viene associata a un token dinamico

#### Categorie di attacco

- Host attack
- Replay
- Client attack
- Trojan Horse
- Denial of service
- Eavesdropping

**Client attack**
L'attaccante non si impossessa delle credenziali, ma si pone in mezzo al client e all'host

- pw auth: L'unico modo di difesa è avere una password robusta
- token auth:
	- attacco: forza bruta
	- difesa: elevata entropia
- biometric auth
	- attacco: match falso
	- difesa: elevata entropia e limitare i tentativi

**Host attack**
Quando l'attaccante si vuole impossessare dei file con le pw, token o template biometrici

- ps
	- attacco: attacco a dizionario, forza bruta o furto
	- difesa: il file deve essere protetto all'interno del sistema
- token:
	- attacco: furto di passcode
	- difesa: stessa della pw
- biometrica:
	- attacco: furto del template
	- difesa: 
		- token statico: autenticazione del meccanismo per rilevare la caratteristica biometrica
		- token dinamico: protocollo challange-response

**Eavesdropping attack**
L'attaccante cerca di osservare l'utente

- pw
	- attacco: keylogging
	- difesa: uso consapevole, autenticazione multi fattore
- token:
	- attacco: furto, copia fisica
	- difesa: stessa della pw
- biometrica:
	- attacco: copia o imitazione
	- difesa
		- dinamica: bfdgi 
		- statica: fddfds

**Trojan Horse**
un'app malevola viene installata sul device
L'unica soluzione è autenticazione del client, del software e device

**Replay attack**
L'attaccante fa il replay delle informazioni
Le soluzioni sono i protocollo challange-response, autenticazione multi fattore e one time passcode

**Denial of service**
tentativo di disabilitare il servizio di autenticazione cercando di bloccare il servizio con tentativi di autenticazione

---

### Controllo degli accessi

#### Access policies

E' un insieme di decisioni che definiscono quando si possono fare particolari accessi a particolari istanze.

FAAAAHHHH

**Accesso basato sui ruoli**

Abbiamo utenti e ruoli.
Mappiamo utenti e ruoli. Ogni ruolo può operare in un certo mondo sugli utenti o sui ruoli stessi.

Modelli RBAC
Introdotte le gerarchie (tipico delle organizzazioni aziendali). 

---
### Errori nella programmazione

Errori tipici di chi scrive il codice per la sicurezza in un sistema.

A monte c'è un errore umano (distrazione) che può generare una fault.
La fault può dare luogo a una failure.

L'attaccante deve prima controllare se c'è un flaw da sfruttare per accedere al sistema.
#### Buffer overflow

Quando un programma cerca di inserire più dati rispetto a quanti ne può contenere.

L'effetto non è immediato
E' il primo passo per degli attacchi più complessi (aprire una shell)

>[!info] Dialer.exe
>Dialer era un programma Windows che accettava un numero e inoltrava le chiamate
>Non c'era un controllo, perché un numero da 100 numeri mandava in crash il programma.
>Si passò ad analizzare come il programma utilizzava la memoria.
>Il numero di telefono veniva scritto all'interno dello stack.

>[!note] Elementi
>- Program counter: cambiare il program counter causa il trasferimento del programma in esecuzione a un'altra istruzione nel code segment
>- Per il sistema i dati memorizzati sono solo dei stringhe binarie con un corrispettivo esadecimale

#### Incomplete mediation

Non si ha pieno controllo dei dati.
Errore di controllo dell'accesso.

---
### Malware

Il malware è un codice malevolo. A seconda del suo comportamento e dei danni assume diversi nomi.

**Tipi di Malware**
- Virus: un programma che può replicarsi e infettare programmi modificandoli
	- non possono replicarsi e attaccare se non c'è un programma (host) da infettare e che lo può eseguire
- Worm: programmi *standalone* non ha bisogno di un host che lo esegue
- Trojan Horse: programmi con funzionalità specifiche che possono modificare in modo malevolo oppure con funzionalità aggiunte
	- Ex. uno script di login che da le informazioni di login al resto del sistema

![[Pasted image 20260330141345.png|500]]

- Rabbit: codice che si replica senza limiti per esaurire le memorie del sistema
- Logic bomb: l'azione del virus si attiva allo scadere di un timer o dopo un certo evento
- Dropper: depositare dell'altro codice (per esempio depositare un malware)
- Script attack: eseguito quando si scarica dal web
- Spyware: Intercetta dati
- Ransomware: cifra o trasferisce dei file
- Trapdoor/backdoor: accede da remoto al sistema
- Rootkit: codice che accede a sezione con privilegi alti

#### Danno

- Disturbo: nulla di distruttivo
- Distruttivo: corruzione o eliminazione di file, software danneggiati
- Intenti commerciali o criminali: FAAAHH

#### Strategie per nascondere il malware

- Nascondere un file nelle directory di sistema
- Rimpiazzare un file non malevolo 
- Distribuire i file in varie directory
- Modifica dei registri di sistema in modo tale da essere sempre eseguito

+