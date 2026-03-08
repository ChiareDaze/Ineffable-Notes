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

#### Cifratura a chiave simmetrica

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

#### Public-key encryption structure

Ho un plaintext, ho un algoritmo di cifratura. I mittenti cifrano il messaggio con una chiave pubblica e il destinatario decifra il messaggio con una chiave privata.

---
### Firma digitale

**Chiave pubblica**
E l'inisieme degli algoritmi che permettono di garantire l'autenticità e la non ripudiabilità di un messaggio.
L'obiettivo è quello di creare un pacchetto di dati che si va ad aggiungere al messaggio.

Si calcola un tag con un hash function e si cifra il tag con la chiave provata del mittente e si allega al messaggio.
Chi riceve il messaggio va a verificare che l'integrità del messaggio non sia stata compromessa e che sia stato effettivamente il mittente a mandarlo.
La falla di questo schema è che qualcuno potrebbe ottenere la chiave dato che è pubblica e "spacciarsi" per il mittente.

L'idea è quella di introdurre il certificato a chiave pubblica.
vedi slide 7 del pdf

Passi per verificare e creare un messaggio
L'utente che vuole creare il messaggio genera le chiavi.
Prepara il certificato che include la chiave pubblica.
vedi slide 8-9

#### Chiave simmetrica

Digital envelop

La chiave pubblica viene usata per proteggere la chiave simmetrica.
Viene distribuito il messaggio + la chiave simmetrica utilizzata per cifrare il messaggio che verrà cifrata a sua volta con la chiave pubblica del destinatario.

**Numeri casuali**
Utilizzati negli algoritmi a chiave pubblica.
Caratteristiche di *casualità* e *non predicibilità*

La frequenza con cui un numero deve essere generato è uguale per tutti gli altri numeri.
Non deve essere possibile prevedere la sequenza di numeri generati.

**Non predicibilità**
Ogni numero è indipendente statisticamente dagli altri numeri nella sequenza

Dato che avere dei numeri casuali pure  è difficile, si vanno a generare dei numeri *pseudo-casuali* che sono delle sequenze che soddisfano statisticamente un random test.

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

**Generazione degli stream delle chiavi**
