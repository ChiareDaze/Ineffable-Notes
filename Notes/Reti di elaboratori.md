### Reti

>[!info]
>Le reti vengono utilizzate attraverso dispositivi chiamati *nodi*. 
>Questi nodi sono collegati tramite *link*. Quando un nodo ospita un'applicazione, viene definito *host*. In caso contrario, si parla di *router* o *switch*.

![[Pasted image 20250227201733.png|400]]

#### Sistemi terminali e dispositivi di interconnessione

Una rete è composta da due principali categorie di dispositivi:
- *Sistemi terminali*: dispositivi che si scambiano informazioni.
- *Dispositivi di interconnessione*: dispositivi che gestiscono la trasmissione dei dati tra i vari nodi.

**Sistemi Terminali**
Possono essere di due tipi:
- *Host*: dispositivi di proprietà degli utenti, come laptop, smartphone e tablet, dedicati all'esecuzione di applicazioni.
- *Server*: computer ad alte prestazioni che forniscono servizi a più applicazioni utente, gestiti da amministratori di sistema.

**Dispositivi di interconnessione** 
Rigenerano/modificano ill segnale che ricevono e si distinguono in:
- *Router*: collegano una rete ad altre reti
- *Switch*: collegano più sistemi terminali all'interno di una rete locale, inoltrando i dati ai dispositivi destinati
- *Modem*: rigenerano i segnali e modificano la codifica dei dati

#### Collegamenti

I dispositivi di rete vengono collegati utilizzando collegamenti che possono essere:

**Cablati**

![[Pasted image 20250227202349.png|250]]

I collegamenti cablati utilizzano mezzi fisici, come il *rame* o la *fibra ottica*, in cui il segnale viaggia attraverso un cavo fisico.

**Wireless**

![[Pasted image 20250227202419.png|275]]

I collegamenti wireless non utilizzano cavi fisici, ma si basano su onde elettromagnetiche o segnali satellitari che viaggiano nell'aria. 
Questi collegamenti sono influenzati dall'ambiente di propagazione, come riflessioni, ostacoli e interferenze.

#### Mezzi trasmissivi cablati

- *Bit*: l'unità di trasmissione dei dati che viaggia da un sistema terminale all'altro, passando attraverso una serie di dispositivi trasmittenti e ricevitori
- *Mezzo fisico*: il materiale che connette il trasmettitore e il ricevitore

**Fibra ottica**
E' un mezzo sottile e flessibile che trasmette impulsi di luce. 
Questo tipo di collegamento ha un'alta frequenza di trasmissione che può variare da 10 a 100 Gbps ed è immune alle interferenze elettromagnetiche, con un basso tasso di errore.

#### Wireless

I collegamenti wireless utilizzano onde elettromagnetiche per trasmettere segnali attraverso l'aria. 
Sebbene non richiedano l'installazione di cavi fisici, sono influenzati dall'ambiente di propagazione che può causare riflessioni, ostruzioni o interferenze.

>[!info] Classificazione delle reti
>- *PAN* (personal area network):  rete molto piccola (Bluetooth)
>- *LAN* (local area network): rete utilizzata nelle aziende, basata su wifi e ethernet
>- *MAN* (metropolitan area network): si estendono a livello cittadino
>- *WAN* (wide area network): si estendono a livello nazionale
>- *Internet*: la rete che copre tutto il pianeta

**LAN**

Una LAN è una rete privata che collega i sistemi terminali all'interno di un singolo edificio. Ogni dispositivo in una LAN ha un indirizzo IP univoco che lo identifica.

- LAN con cavo condiviso: 
	- Composta da un cavo dove è possibile collegare ogni nodo della rete (*rete broadcast*: quando un nodo trasmette, tutti gli altri lo ricevono).
	- Solo il destinatario elabora il pacchetto, tutti gli altri lo ignorano
	- La comunicazione avviene in modo sequenziale, un dispositivo per volta

![[Pasted image 20250227202859.png|400]]

- LAN con switch (tipologia a stella):
	- Ogni dispositivo in rete è direttamente collegato allo switch
	- Lo switch identifica l'indirizzo di destinazione e invia il pacchetto solo al destinatario, riducendo il traffico nella rete e permettendo a più dispositivi di comunicare contemporaneamente

![[Pasted image 20250227202922.png|400]]


**WAN**

Una WAN copre un'area geografica estesa, come una città, una nazione o una regione, e connette vari dispositivi di rete, come router, switch e modem. 
Di solito è gestita da un Internet Service Provider (ISP).

*Wan punto-punto*

![[Pasted image 20250227203004.png|400]]

Collega due mezzi tramite un mezzo trasmissivo (wireless o cavo)

*Wan a commutazione*

![[Pasted image 20250227203059.png|350]]

WAN più grandi che ha più di due punti di terminazione, viene utilizzata nelle dorsali di internet.

**Internetwork composta da due LAN e una WAN punto-punto**

Un'internetwork è una combinazione di LAN e WAN collegate tra loro. 
Ad esempio, un'azienda con uffici in due città può affittare una WAN punto-punto per connettere le due LAN, creando una internetwork. 
I router sono utilizzati per instradare i pacchetti tra le LAN.

![[Pasted image 20250227203355.png|500]]


*Rete del GARR*
Il GARR è una WAN nazionale che collega centri culturali, come università e biblioteche. 
Si tratta di un'infrastruttura in fibra ottica che si estende per circa 15.000 km, utilizzando le tecnologie di commutazione più avanzate.

#### Commutazione (switching)

Una internetwork è una rete composta da dispositivi (come switch e router) che scambiano informazioni tra loro. 
Esistono due principali modalità di commutazione:

**Reti a commutazione di circuito**

Tra destinatario e trasmittente viene stabilito un collegamento (*circuito*) che viene usato per l'intera comunicazione finché non è terminata, come succede per esempio con il sistema telefonico.

![[Pasted image 20250227204135.png|400]]

Tra i due host ci sono diversi possibili percorsi. Vengono riservate le risorse lungo il percorso e ogni dato seguirà quel percorso fino alla fine della comunicazione.

>[!write] Esempio
>
>![[Pasted image 20250227204713.png|400]]
>
>La linea tra due switch può gestire contemporaneamente quattro canali voce (condivisa tra tutte le coppie di apparecchi telefonici)
>
>- Quando tutte e 4 persone da un lato comunicano con le altre 4 persone dall'altro lato si avrà che la capacità della linea è completamente utilizzata.
>
>- Quando solo una persona da un lato è collegata con una persona dall'altro lato, viene utilizzato solo 1/4 della capacità

In questo caso, le risorse di rete, come l'ampiezza di banda, vengono suddivise in "pezzi" assegnando una porzione per ogni comunicazione. 
Se una comunicazione non è attiva, la risorsa rimane inutilizzata.

**Reti a commutazione di pacchetto**

Nella commutazione di pacchetto, i dati vengono suddivisi in pacchetti di dimensione fissa. 
Ogni pacchetto è indipendente dagli altri e viene inviato attraverso il percorso migliore disponibile in ogni momento. 
Non vengono riservate risorse per la comunicazione e i pacchetti possono seguire percorsi diversi e arrivare a destinazione in ordine diverso.

![[Pasted image 20250227225206.png|400]]

#### Internet

Internet è una rete a commutazione di pacchetto.

![[Pasted image 20250227225556.png|400]]

Quando due dispositivi comunicano, non c'è alcun ritardo per i pacchetti.
Tuttavia, se più dispositivi sono in comunicazione e la capacità della rete non è sufficiente per gestire tutti i pacchetti in arrivo, i pacchetti possono subire ritardi. 
Ogni pacchetto può essere memorizzato in una coda dai router.

Concettualmente, Internet ha tre livelli:
1. *Dorsali*: la rete principale di Internet
2. *Rete del provider*: la rete che collega i provider locali alla dorsale
3. *Rete privata*: la rete dell'utente finale, che si collega a Internet tramite un ISP

![[Pasted image 20250227225745.png|400]]

#### Accesso a Internet

Per accedere a Internet, un utente deve essere fisicamente collegato a un ISP, di solito tramite una WAN punto-punto. Il collegamento che connette l'utente al primo router di Internet è chiamato rete di accesso.

>[!info] Tipologie di Accesso
>- *Accesso tramite rete telefonica*: utilizzando tecnologie come DSL o dial-up
>- *Accesso tramite reti wireless*: come Wi-Fi o rete cellulare
>- *Accesso diretto*: tramite un collegamento fisico, come un cavo Ethernet

##### Accesso via rete telefonica

![[Pasted image 20250228113317.png|500]]

E' possibile collegarsi  a Internet utilizzando la linea telefonica tra la sede del dispositivo e la centrale telefonica con una WAN punto-punto.

**Servizio dial-up**
Viene inserito un modem (modulatore-demodulatore) nella linea telefonica, che converte i dati digitali in analogici e viceversa.
I problemi più grandi legati a questo tipo di rete sono la lentezza e l'impossibilità di parlare e navigare contemporaneamente.

**Servizio DSL (digital subscriber line)**
Questa tecnologia supporta velocità più elevate sulla linea telefonica e divide il collegamento tra abitazione e ISP in tre bande di frequenza non sovrapposte, permette navigazione e telefonate nello stesso momento.

**Accesso tramite Ethernet**
Ci si collega col proprio terminale direttamente allo switch tramite cavo, lo switch è poi collegato ad un router che a sua volta è connesso ai router della dorsale.

**Accesso Wireless**
Ci colleghiamo tramite WiFi all’access point locale collegate ai vari router, ha ovviamente un raggio d’azione limitato. Oppure possiamo utilizzare la rete cellulare che si basa sugli access point della compagnia telefonica, hanno raggi di azioni molto più elevati rispetto ai classici accesso point WiFi.

---

Un pacchetto (un blocco di dati generati da un host) dovrà passare in diversi ISP.
Uno dei problemi principali è trovare il percorso che il pacchetto dovrà trovare dalla sorgente al destinatario (*routing*).
### Capacità e prestazioni delle reti

Velocità significa quanto la rete riesce a trasmettere velocemente i dati.

> [!info]
> Il concetto di velocità di una rete comprende molti fattori:
>- Ampiezza di banda
>- bitrate
>- throughput
>- ritardi
>- perdita di pacchetti

**Bandwidth o ampiezza di banda**

Con questo termine, si intendono due concetti legati tra loro.

- *Caratterizzazione del mezzo trasmissivo*: misura la larghezza dell’intervallo di frequenze utilizzate nel sistema trasmissivo (*Hz*). Più è ampia, più è la quantità di informazione che posso trasmettere.

- *Caratterizzazione di un collegamento*: misura la quantità di bit al secondo che un link garantisce di trasmettere (*bps*)

Il bit rate è la quantità di bit al secondo che un link può trasmettere (immettere sul canale).
Il bit rate dipende dalla banda ed è proporzionale a essa

>[!write] Esempio
>Il rate di un link Fast Ethernet è di 100 Mbps, ovvero tale rete
>può inviare al massimo 100 Mbps

**Throughput**

Indica quanto effettivamente la rete è in grado di inviare i dati.
E' misurato come il rate (*bps*),  ma tipicamente è `<=` al rate, questo perché il rate è la misura della potenziale velocità di un link.

>[!write] Esempio
>Una strada è progettata per far transitare 1000 auto al minuto da un punto all’altro. Se c’è traffico, tale cifra può essere ridotta a 100. Il rate è 1000 auto al minuto, il throughput 100 auto al minuto

Come facciamo a misurare il throughput end-to-end (dalla sorgete alla destinazione)?

Dato che $R_{s}<R_{c}$ il throughput è definito da $R_{s}$.

In generale il throughput è dato dal minimo dei throughput dei collegamenti che formano il percorso.

![[Pasted image 20250308181255.png|400]]

#### Latenze e perdite di pacchetti

>[!info] Definizione
>La latenza è il tempo che un pacchetto impiega ad arrivare a destinazione dal momento in cui il primo bit parte dalla sorgente.

Nella commutazione di pacchetto, i pacchetti si accumulano nei buffer dei router.
Se il tasso di arrivo dei pacchetti sul collegamento è maggiore rispetto al rate del collegamento,  i pacchetti si accoderanno in attesa del loro turno e quindi si genera un ritardo. 
Se nel buffer non c’è più spazio per altri pacchetti, allora questi verranno scartati.

![[Pasted image 20250308181814.png|400]]

Esistono 4 tipi di cause di ritardo dei pacchetti:

- Ritardo di elaborazione
- Ritardo di accodamento
- Ritardo di trasmissione
- Ritardo di propagazione

**Ritardo di elaborazione**
Ogni pacchetto viene processato controllando eventuali errori sui bit e in caso, vengono scartati.
Infine, viene determinato il canale di uscita.

**Ritardo di accodamento**
Equivale all'attesa di trasmissione nella coda di input e nella coda di output del router.
Varia in base al livello di congestione del router e da pacchetto a pacchetto.

**Ritardo di trasmissione**
Indica il tempo richiesto per immettere tutti i bit del pacchetto sul collegamento.

Supponiamo che il primo bit venga trasmesso al tempo $t_{1}$ e l'ultimo al tempo $t_{2}$. Il ritardo di trasmissione sarà $t_{1}-t_{2}$.

Possiamo calcolarlo anche in questo modo:

$$
\begin{align}
&R =\text { rate del collegamento (in bps) } \\
&L=\text { rate del collegamento (in bps) }\\
&\text {Ritardo di trasmissione}= \frac{L}{R}\\
\end{align}
$$

**Ritardo di propagazione**
Tempo che impiega un bit per propagarsi sul canale (viaggiare da un punto $A$ a un punto $B$).
Lo calcoliamo come:

$$
\begin{align}
&d = \text {Distanza da percorrere (lunghezza del canale) } \\
&s = \text {Velocità di propagazione (velocità di propagazione dei bit)}\\
&\text {Ritardo di propagazione } = \frac{d}{s}\\
\end{align}
$$

>[!info] Osservazione
>![[Pasted image 20250308183826.png|100]]
> La velocità di propagazione corrisponde alla velocità della luce ($2 \cdot 10^{ 8 } m/s$)

#### Ritardo di nodo

Il ritardo quindi è dato da:
$$
d_{nodal}=d_{proc}+d_{queue}+d_{trans}+d_{prop}
$$
Dove:

- $d_{trans}$​ è il ritardo di trasmissione che è significativo sui collegamenti a bassa velocità
- $d_{prop}$ è il ritardo di propagazione che va da pochi microsecondi a centinaia di millisecondi
- $d_{proc}$​ è il ritardo di elaborazione, in genere pochi microsecondi o meno
- $d_{queue}$ è il ritardo di accodamento che dipende dalla congestione della rete in quel momento

#### Perdita dei pacchetti

Se una coda (detta anche buffer) ha capacità finita, quando il pacchetto trova la coda piena, viene scartato (quindi va perso).
Il pacchetto perso può essere ritrasmesso dal nodo precedente, dal sistema terminale che lo ha generato o non essere ritrasmesso affatto

#### Ritardi e percorsi in Internet

**Traceroute o tracert**
E' un programma diagnostico che fornisce una misura del ritardo dalla sorgente a tutti i router lungo il percorso Internet punto-punto verso la destinazione.
Invia gruppi di tre pacchetti (ogni gruppo con un tempo di vita incrementale) che raggiungeranno il router sul percorso verso la destinazione.
Il router restituirà i pacchetti al mittente e calcolerà l’intervallo tra trasmissione e risposta.

L'output presenta 6 colonne:
1. Il numero di router sulla rotta
2. Nome del router
3. Indirizzo del router
4. tempo di andata e ritorno 1°pacchetto
5. tempo di andata e ritorno 2°pacchetto
6. tempo di andata e ritorno 3°pacchetto

Il round trip time include i 4 ritardi e può succedere (in caso di congestione) che i pacchetti prendano percorsi diversi.
Se la sorgente non riceve risposta da un router intermedio (o ne riceve meno di 3) allora pone un asterisco al posto del tempo RTT.

#### Prodotto rate * ritardo

Indica il numero massimo di bit che possono riempire il collegamento.
Supponiamo di avere un link da $1 \text { bps}$ e un ritardo di $5 \text { secondi}$ contemporaneamente sul link:

![[Pasted image 20250308185026.png|500]]

Il primo bit entra dopo un secondo e dopo 5 secondi sarà arrivato alla fine.
In questi 5 secondi saranno entrati altri bit tutti, a differenza di un secondo per via del bitrate, e si saranno mossi tutti ogni secondo.

Possiamo pensare al link come un tubo in cui la sezione trasversale indica il rate e la lunghezza il ritardo.
Possiamo, quindi, vedere il volume come prodotto tra rate e ritardo:

![[Pasted image 20250308185044.png|500]]

---
### Stack protocollare

Non è sufficiente collegare router e cavi per usare la reti, infatti hardware e software devono interagire.

>[!info] Protocollo
>Un protocollo definisce le regole che il mittente e il destinatario, così come
>tutti i sistemi intermedi coinvolti, devono rispettare per essere in grado di
>comunicare.

#### Strutturazione a livelli

La strutturazione dei protocolli in livelli permette di suddividere compiti complessi in parti più semplici e gestibili.

**Modularizzazione e indipendenza dei livelli**
Ogni livello può essere visto come un modulo che funge da "black box", in cui ci si concentra solo sugli ingressi e sulle uscite, senza preoccuparsi di come i dati vengano effettivamente trasformati al suo interno.

Se due dispositivi producono lo stesso output dato lo stesso input, possono essere considerati equivalenti. Questo significa che le macchine possono provenire da fornitori diversi senza compromettere il funzionamento del sistema.

Inoltre, c'è una chiara separazione tra i servizi e la loro implementazione: ogni livello sfrutta i servizi offerti dal livello inferiore e offre, a sua volta, servizi al livello superiore, indipendentemente dal modo in cui questi servizi sono implementati.

#### Stack protocollare TCP/IP e gerarchia dei protocolli

Il modello TCP/IP è una famiglia di protocolli utilizzata su Internet, strutturata come una gerarchia di moduli che interagiscono tra loro, ognuno dei quali offre funzionalità specifiche.

Il termine "*gerarchia*" indica che ogni protocollo di livello superiore si basa sui servizi forniti dai protocolli di livello inferiore.

Oggi il modello TCP/IP è generalmente descritto come composto da cinque livelli:
- *Applicazione*: rappresenta il livello più vicino all'utente, dove operano le applicazioni di rete (come HTTP, SMTP, FTP, DNS). Qui i pacchetti sono chiamati **messaggi**.
- *Trasporto*: si occupa di trasferire i messaggi tra il client e il server di un'applicazione. Usa protocolli come TCP (affidabile) e UDP (non affidabile). I pacchetti in questo livello sono chiamati **segmenti**.
- *Rete*: gestisce l'instradamento dei segmenti dalla sorgente alla destinazione. I pacchetti sono chiamati **datagrammi**.
- *Link (collegamento)*: si occupa della trasmissione dei datagrammi da un nodo all'altro lungo il percorso (ad esempio, Ethernet, Wi-Fi, PPP). I pacchetti in questo livello sono chiamati **frame**.
- *Fisico*: si occupa del trasferimento dei singoli bit lungo il canale di comunicazione.

**Dove si trova lo stack protocollare?**
In qualsiasi dispositivo connesso alla rete. I router implementano solo una parte dello stack protocollare.

![[Pasted image 20250316201625.png|500]]

La rete, quindi, è organizzata in *layer* messi l’uno sopra l'altro, con lo scopo di offrire servizi agli strati superiori nascondendo i dettagli implementativi.
Un layer $N$ di un computer quindi deve essere in comunicazione con il layer $N$ di un altro computer, ma non direttamente fra loro due. Infatti, dovranno passare fra gli altri layer. 
Il come comunicano viene definito dai *protocolli*.

Le entità che formano questi strati prendono il nome di *peer*. Quindi,  per esempio, due layer di *collegamento* formano un peer.

>[!info] Differenza tra servizi e protocolli
>*Servizio*: insieme di primitive che uno strato offre a quello superiore, definisce quindi quali operazioni si possono usare ma non il come ovvero l’implementazione.
>
>*Protocollo*: è un insieme di regole che controllano il formato e significato
>dei pacchetti o in generale i messaggi che vengono scambiati all’interno dello strato

#### Incapsulamento e decapsulamento

Quando un pacchetto parte dal livello applicazione e scende verso il basso, viene *incapsulato*.
Quindi viene inserito in un "contenitore" con delle informazioni aggiuntive.
Il router è il dispositivo che effettua sia incapsulamento che decapsulamento dato che è collegato a due link.

Aggiungendo questi header permettiamo ad ogni livello di riconoscere su quali pacchetti devono agire.

![[Pasted image 20250311145241.png|600]]

I nomi che diamo ai pacchetti nei vari livelli dipendono quindi dall’header presente:
- Messaggio: nessuna intestazione
- Segmento o datagramma utente: header trasporto + messaggio
- Datagramma: header rete + segmento
- Frame: header collegamento + datagramma

Quando il frame viaggia attraverso la rete e arriva all'host di destinazione, andrà a decapsulare il frame a ogni livello.

#### Multiplexing e demultiplexing

Dato che lo stack protocollare TCP/IP prevede più protocolli nello stesso livello, è necessario eseguire il multiplexing alla sorgente e il demultiplexing alla destinazione

- Multiplexing: un protocollo può incapsulare (uno alla volta) i pacchetti ottenuti da più protocolli del livello superiore
- Demultiplexing: un protocollo può decapsulare e consegnare i pacchetti a più protocolli del livello superiore

E' necessario un campo nel proprio header per identificare a quale protocollo appartengano i pacchetti incapsulati

#### Vantaggi e svantaggi della modularità 

Tra i vantaggi del modello, troviamo la modularità, che garantisce una maggiore facilità nel design e nella gestione del sistema, permettendo anche di modificare un modulo senza influenzare gli altri.

Tuttavia, uno degli svantaggi è che, in alcuni casi, potrebbe essere necessario scambiare informazioni tra livelli non adiacenti. In questi casi, si verrebbe a violare il principio della stratificazione, che prevede che i livelli comunichino solo con quelli immediatamente superiori o inferiori.

### Modello OSI

L'ISO (International Organization for Standardization) ha definito il modello *OSI* come modello alternativo al TCP/IP.
E' composto da 7 livelli:

![[Pasted image 20250316203056.png|300]]

Fondamentalmente aggiunge due livelli al modello TCP/IP tra il livello applicazione e trasporto (livello *presentazione* e *sessione*).

Il modello OSI non è mai stato implementato perché:
- Molte infrastrutture usavano già il modello TCP/IP e fare un cambio avrebbe comportato troppi costi.
- Per alcuni livelli è stata fornita poca documentazione e quindi non sono mai stati creati software appositi
- Non furono mai state dimostrate delle prestazioni così migliori da convincere le aziende a sostituire il TCP/IP

---
### Livello applicazione

Qui, la comunicazione è fornita per mezzo di una connessione logica: questo significa che i livelli applicazione nei due lati della comunicazione agiscono come se esistesse un collegamento diretto attraverso il quale poter inviare e ricevere messaggi.

### Web e  HTTP

Il www (*World Wide Web*) è un'applicazione nata dalla necessità di scambio e condivisione di informazioni tra ricercatori universitari di varie nazioni.

Opera su richiesta (on demand) ed è facile rendere informazioni disponibili.
Ad oggi ci sono diversi browser e motori di ricerca per la ricerca di informazioni.

Da un lato abbiamo il browser (web client).
Nel momento in cui cerchiamo un sito, parte la richiesta alla pagina web e arriva al web server.
Dal web server ci arriva la pagina web che stiamo cercando.

Componenti applicazione web:
- Web client: interfaccia con l'utente
- Web server (ex. Apache)
- HTML: linguaggio standard per pagine web
- HTTP: protocollo per la comunicazione tra client e server Web

![[Pasted image 20250316203743.png|450]]

#### HTTP

>[!info] Terminologia
>Una pagina web è:
>- costituita da oggetti (immagini, file html. ecc...)
>- formata da un file base html che include diversi oggetti referenziati
>
>Inoltre, ogni oggetto è referenziato da un URL (uniform resource locator)

Gli *URL* sono composti da 3 parti:
1. Il protocollo
2. Nome della macchina in cui è situata la pagina
3. Il percorso del file che indica la pagina, il nome del file e la posizione nel filesystem

![[Pasted image 20250316204036.png|500]]

**Documenti web**
Ci sono 3 categorie:
- *Statico*: contenuto predeterminato memorizzato sul server
- *Dinamico*: creato dal web server alla recezione della richiesta
- *Attivo*: contiene script o programmi che verranno eseguiti nel browser (ovvero lato client)

**HTTP**
Quindi, HTTP si basa sul modello Client/Server. Il protocollo definisce in che modo i client devono richiedere le pagine e come i server devono trasferirle ai client.

*Lato Client*
- Il browser determina dall’URL host e nome del file
- Esegue la connessione TCP alla porta 80 (standard)
- Invia una richiesta per il file
- Riceve il file
- Chiude la connessione
- Visualizza il file

*Lato Server*
- Accetta la connessione TCP dal client
- Riceve il nome del file richiesto
- Recupera il file dal disco
- Invia il file al client
- Chiude la connessione

#### Connessioni HTTP

**Connessioni non persistenti**
Un solo oggetto viene trasmesso su una connessione TCP. Ciascuna coppia richiesta/risposta viene inviata su una inviata su una connessione TCP separata. Prima di inviare una richiesta al server è necessario stabilire una connessione.

**Connessioni persistenti**
Modalità di default. Più oggetti possono essere trasmessi su una singola connessione TCP tra client e server. La connessione viene chiusa quando rimane inattiva per un lasso di tempo (timeout) configurabile.

#### Schema del tempo di risposta

Per calcolare il tempo di risposta in queste connessione definiamo il concetto di *RTT*.

>[!info] RTT (Round Trip Time)
>E' il tempo che impiega un pacchetto per raggiungere il server, partendo dal client, e tornare indietro.
>
>Inoltre, include i ritardi di propagazione, accodamento e di elaborazione del pacchetto.

Il tempo di risposta è dato da:
- Un RTT per inizializzare la connessione TCP
- Un RTT per la richiesta HTTP e i primi byte della risposta
- Tempo di trasmissione del file
- Quindi in totale: $2RTT+\text { tempo trasmissione }$

Se utilizziamo connessioni persistenti abbiamo un RTT per aprire la pagina RTT per ogni richiesta.
E' molto più veloce, ma le connessioni sono sequenziali.
#### Formato dei messaggi in una richiesta HTTP

![[Pasted image 20250316204813.png]]

**Esempio**
Vediamo un esempio:

```
GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/4.0
Accept-language:fr
```

1. La prima riga è *riga di richiesta* dove vengono inseriti i comandi GET-POST-HEAD
2. Le successive sono *righe di intestazione*
3. A fine messaggio troviamo *carriage return e un *life feed*

![[Pasted image 20250316204955.png|600]]

#### Upload dell'input di un form

*Metodo POST*: la pagina web spesso include un form per l'input. La pagina web spesso include un form per l’input dell’utente. L’input arriva al server nel corpo dell’entità.

*Metodo GET*: come alternativa al metodo POST, possiamo usare il GET inserendo i dati del form nell’URL richiesto

![[Pasted image 20250313145015.png|500]]

#### Formato dei messaggi di risposta

![[Pasted image 20250316205207.png]]

In questo caso i nomi diventano:
1. La prima riga prende il nome di *riga di stato*
2. Troviamo sempre le *righe di intestazione*
3. Possiamo trovare altri dati come ad esempio gli oggetti richiesti

**Esempio**

```
HTTP/1.1 200 OK
Connection close
Date: Thu, 06 Aug 1998 12:00:15 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Mon, 22 Jun 1998 ...
Content-Lenght: 6821
Content-Type: text/html
---
(altri dati)
```

![[Pasted image 20250316205300.png]]


#### Codici di stato

- *200 okay*: richiesta accettata
- *301 moved permanently*: L’oggetto richiesto è stato trasferito; la nuova posizione è specificata nell’intestazione Location: della risposta
- *400 Bad Request*: Il messaggio di richiesta non è stato compreso dal server
- *404 Not Found*: Il documento richiesto non si trova su questo server
- *505 HTTP Version Not Supported*: Il server non ha la versione di protocollo HTTP

In generale la prima cifra del numero indica che tipo è il codice:
- *1xx*: messaggi di Informazione
- *2xx*: successo
- *3xx*: reindirizzamento
- *4xx*: client Error
- *5xx*: server Error
#### Cookie

![[WhatsApp Image 2025-03-17 at 16.48.01_60ad9cce.jpg|130]]

HTTP è un protocollo senza stato (*stateless*), se un client fa più richieste a uno stesso server, non mantiene informazioni sulle richieste fatte. 
I protocolli che mantengono lo stato sono molto complessi dato che si deve memorizzare tutto ciò che fa il client. In caso di errore, le viste sullo stato di client e server potrebbero essere contrastanti.

In molti casi il server ha bisogno di ricordarsi degli utenti (es. per offrire contenuti personalizzati in base alle preferenze di ogni utente).
Per questo, sono stati introdotti i **cookie** con lo scopo di creare una sessione di richieste e risposta HTTP "con stato".

**Sessione**
Ha un tempo di vita relativamente corto e sia il client che il server possono interromperla.

##### Interazione utente-server con i cookie 

Servono quattro componenti:

1. Una riga di intestazione che viene inserita nei messaggi di risposta HTTP
2. Una riga di intestazione che viene inserita nei messaggi di richiesta HTTP
3. Un file cookie mantenuto sul sistema terminale dell'utente e gestito dal browser dell'utente
4. Un data base sul server

Il server mantiene tutte le informazioni riguardanti il client su un file e gli assegna un identificatore di sessione (*SID*), composto da una stringa di numeri.

Ad ogni richiesta il browser consulta il file del cookie, estrae quello che necessario per quel sito web e lo inserisce in ogni richiesta HTTP. 
Infine, il server può riconoscerlo e mostrare dei contenuti personalizzati.

##### Durata di un cookie

Il server cancella il cookie inviando al client di intestazione `Set-Cookie` nel messaggio con `Max-Age = 0`.

#### Caching

Server per migliorare le prestazioni dell'applicazione web.

Il server proxy ha una memoria per mantenere copie della pagine visitate.
Il browser può essere configurato per inviare le richieste dell’utente alla cache
Il browser trasmette tutte le richieste HTTP alla cache

#### Server proxy

Mantiene copie delle pagine visitate.
Il browser può essere configurato per inviare le richieste dell’utente alla cache
Il browser trasmette tutte le richieste HTTP alla cache
- oggetto presente nella cache: la cache fornisce l’oggetto
- altrimenti la cache richiede l’oggetto al server d’origine e poi lo inoltra al client

---

### DNS

#### Identificazione degli host

Host internet hanno nomi (hostname) che sono facili da ricordare ma forniscono poca informazione sulla collocazione degli host all'interno di internet.

Il DNS prende in input il nome di una macchina e ci dice qual è l'indirizzo IP. Mantiene il mapping tra indirizzo IP e nome.

Il DNS deve mantenere le informazioni e recuperarle velocemente.
Organizza le informazioni in modo gerarchico in modo da poterle recuperare facilmente.
Viene utilizzato da tutte le applicazioni.
Utilizza il servizio di trasporto UDP e indirizza la porta 53.

>[!info] Aliasing
>Il DNS permette di associare un nome più semplice da ricordare a un come complesso.

I siti con molto traffico vengono replicati su più server e ciascuno di questi gira su un sistema terminale diverso e presenta un indirizzo IP diverso.

#### Può essere centralizzato?

No, perché se avesse anche un singolo punto di fallimento, crasherebbe il server DNS e quini internet stesso.
......

#### Gerarchia del DNS

Per fare una ricerca in tempi rapidi, si raggruppano le coppie (IP e nomehost) in base al dominio.
Ci sono tre classi di server DNS organizzati in una gerarchia:
- root
- Top-level domain
- Authoritative
Ci sono poi i server DNS locali con cui interagiscono direttamente le applicazioni
---

### Protocollo FTP

Permette di trasferire file da una macchina remota o di inviarvi file.
Il comando per accedervi è

```
ftp NomeHost
```

Per il trasferimento si isa

```
ftp > get dsvdsvcs
```

Quando l'utente fornisce il nome dell'host remoto, il processo client FTP stabilisce una connessione TCP 

- Connessione controllo: persistente e dura tutto il tempo in cui noi siamo connessi
- Connessione dati: si occupa del trasferimento di file

#### Caratteristiche di FTP

FTP ha una connessione di controllo *out of band*
Il server FTP mantiene lo stato.

#### Connessione dati

Quando il server riceve un comando per trasferire un file, apre una connessione dati TCP sulla porta 20 con il client.

Dopo il trasferimento di un file, il server chiude la connessione

#### Posta elettronica

Nelle altre applicazioni, quando inviamo un messaggio, attendiamo una risposta.
Quando mandiamo una email, per esempio, non viene tornato nessun messaggio. Non abbiamo la certezza che il destinatario abbia letto subito il messaggio.

La caratteristica è che è un'app *asincrona*. Manda un messaggio, ma non sa quando il destinatario leggerà il messaggio.
L'email parte da un utente mittente a un utente destinatario.
Al livello di struttura abbiamo il user agent usato per scrivere e inviare un messaggio o leggerlo.
Il message transfer agent è usato per trasferire il messaggio attraverso la rete
Il message access agent: viene usato per leggere la mail in arrivo

**User agent**

E' il programma che utilizziamo per comporre e leggere le email.
I messaggi in uscita e in arrivo sono memorizzati nel server. Il messaggio viene passato al mail transfer agent.

**Message transfer agent**
vedi slide

**SMTP**
Usa TCP per trasferire on modo affidabile i messaggi di posta elettronica dal cliente al server, utilizzando la porta 25.

Ha tre fasi nel momento in cui viene inviata una mail:
- handshaking: i server si "mettono d'accordo"
- trasferimento di messaggi
- chiusura

L'interazione comando/risposta
- comandi: testo ASCII
- risposta: codice di stato ed espressione

#### Scambio di messaggi

Il client SMTP fa stabilire una connessione sulla porta 25 verso il server SMTP
Se il server è inattivo i client riprova più tardi
Se è attivo, viene stabilita una connessione.
vedi slide


#### Confronto HTTP e FTP

vengono utilizzati per trasferire file da un host all'altro.
HTTP: gli utenti scaricano i file e inizializzano una connessione TCP
FTP: spedisce il file e inizializza la connessione TCP

HTTP: ciascun oggetto è incapsulato nel suo messaggio di risposta
FTP: più oggetti vengono trasmessi in un unico messaggio.

#### Protocollo MIME

Utilizzando quando si devono inviare messaggi in formato non ASCII
vedi slide

#### Protocollo POP 3
Permette al client ricevente la posta di aprire una connessione TCP verso il server di posta sulla porta 110.
Quando la connessione è stabilita, si procede in 3 fasi:
- Autorizzazione
- Transazione
- Aggiornamento

 