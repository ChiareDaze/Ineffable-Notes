
Insieme delle misure e dei controllo che permettono di assicurare a un sistema informativo confidenzialità, integrità e disponibilità.

**Confidenzialità**
Preservare un accesso autorizzato a dati e sistemi
- Dei dati: i dati non devono essere inviati a chi non ha il diritto di riceverli
- Privacy: un individuo deve avere il controllo su chi può accedere a questi dati

**Integrità**
Proteggere il sistema da una modifica impropria del sistema. Significa anche garantire la *non-ripudiabilità* (essere in grado di capire chi ha fatto un'azione)
- Dei dati: I dati non devono essere compromessi
- Del sistema: es. integrità di un software che deve sempre svolgere ciò per cui è stato programmato

**Disponibilità**
Assicurarsi che sia possibile accedere in modo rapido alla informazioni e i dati erogati da un sistema. Riduzione degli accessi al sistema o servizi per accedere agli accessi
- Del sistema: sistema e dati devono essere sempre disponibili rispetto a quelli che sono i prerequisiti del sistema (es. riduzione di banda del sistema non garantisce la disponibilità del sistema)

Questi tre obiettivi sono stati integrati con altri due:
- **Accountability**: monitoraggio delle attività che vengono effettuate su un sistema. Essere in grado di tracciare il comportamento degli utenti che operano sul sistema. Tracciare il responsabile di azioni malevoli. 
- **Autenticità**: autenticità delle informazioni che provengono da una sorgente. Poter verificare l'origine dell'informazione e potermi fidare della veridicità dell'informazione. Garantirla significa verificare che un utente sia quello che dice di essere

Qualora si violassero le proprietà, ci sono impatti di 3 tipi:
- *Basso*: se l'effetto è limitato. Le funzionalità sono ridotte in modo percettibile ma non eccessivamente. Il danno che viene fatto all'asset è minore, la perdita finanziaria è bassa
- *Moderato*: effetto serio. Il danno che viene fatto all'asset è significativo, la perdita finanziaria è significativa 
- *Elevato*: effetto severo o catastrofico. Sono compromesse le funzionalità principali (es. attacco hacker in sapienza dioporco) 

>[!info] Esempi
>- Impatto basso: elenco di informazioni che viene divulgato. Compromissione di un pool anonimo online. 
>- Impatto moderato: compromissione di un forum. Perdere la disponibilità di un portale che dà informazioni agli studenti.
>- Impatto elevato: Compromissione di un sistema di un ospedale, cambiando le informazioni di un paziente.

### Sfide del cybersex (rivedi i punti)

1. La sicurezza può sembrare semplice, ma non lo è (no way)
2. Progettare un meccanismo/algoritmo che sia funzionale
3. Rimpiazzamento dei meccanismi di difesa devono avere un piazzamento logico (il cancello di casa, sta prima della porta)
4. Chi progetta un sistema deve cercare di eliminare tutte le possibili vulnerabilità del sistema
5. Fare un sistema che tenga conto di possibili attacchi
6. I meccanismi devono essere sempre aggiornati e monitorati (vedere cosa sta succedendo)

### Modello del cybersex

- Asset: ha un proprietario che gli da un valore e cerca di abbassare il rischio di minacce il più possibile con delle contromisure.
- Avversario: costituisce una minaccia. Colui che può abusare del sistema e quindi violare i tre obiettivi. Cerca le vulnerabilità del sistema e sfruttarle per un attacco.

**Vulnerabilità**
Procedura implementata nel modo scorretto che viene sfruttata dall'attaccante per bucare il sistema.

**Avversario**
Individuo o gruppo che attacca il sistema

**Attacco**
Ogni tipo di attività che ha un intento malevolo.

**Contromisure**
Tecniche per neutralizzare le minacce

**Rischio**
Misura il legame tra minacce e danno
$$
R = P \cdot R
$$
$R$ = Rischio
$P$ = Probabilità di minaccia

**Politiche di sicurezza**
Criteri per proteggere i servizi di sicurezza
Es. stabilire chi può accedere a un file

>[!info] Attacchi
>- Passivo: cercare di imparare o fare uso di informazioni prese dal sistema
>- Attivo: cercare di alterare il sistema
>- Insider: fatto da qualcuno che è all'interno del perimetro di sicurezza
>- Outsider:  fatto da qualcuno che è al di fuori del perimetro di sicurezza

### Minacce e attacchi

**Rilascio non autorizzato di informazioni**
- un insider rilascia informazioni a un'entità non autorizzata
- intercettazione: entità non autorizzata accede a dati sensibili
- interferenza
- intrusione

**Mascheramento**
Un'entità finge di essere qualcun altro
Include altre forme di attacco per ottenere le credenziali di accesso

**Attacchi di modifica del messaggio**
Modificare un messaggio legittimo per produrre un effetto indesiderato.

**Attacchi di denial of service**
Inibire le risorse di un servizio

---
### Contromisure

Obiettivo di minimizzare le minacce a un sistema.
Contromisure di carattere:
- Tecnico
- Funzionale: relative alla gestione della sicurezza

*Tecniche*
Controllo degli accessi per far si che solo le persone autorizzate possano accedere al sistema.

Identificazione e autenticazione per verificare l'entità

Protezione dei sistemi e della comunicazione (system e network security).

Integrità del sistema e delle informazioni

*Funzionali*
Consapevolezza e formazione
Controllo e responsabilizzazione: periodicamente devo verificare che siano rispettati processi e che le misure per la gestione della sicurezza siano funzionanti.
Certificazione, accreditamento e valutazione della sicurezza
Pianificazione dell'emenrgenza: piano per gestire un'emergenza
Manutenzione hardware e software
Protezione fisica e ambientale
Pianificazione delle attività relative alla sicurezza
Sicurezza del personale (se il personale deve accedere a sistemi classificati prima si deve fare uno screening della storia del personale)
Valutazione dei rischi che permette di stabilire le contromisure da applicare.
Acquisizione di sistemi e servizi

**Requisiti di sicurezza misti**
Gestione della configurazione
Risposta agli incidenti
Protezione dei dati

>[!info] Principi fondamentali della progettazione sicura dei sistemi
>- Facile da testare e aggiornare
>- Principio del fail-safe default: le decisioni devono essere basati sui permessi
>>[!warning] Differenza tra esclusione e permesso
>>vedi esempio a casa
>- Complete mediation: riferito al meccanismo di controllo degli accessi. 
>- Open design
>- Principio separazione dei privilegi

>[!info] Superficie di attacco
>Tutti i punti da cui un attaccante potrebbe entrare in un sistema.
>>[!examples] Esempi
>>- Porte aperte sul web e altri server
>>- Servizi disponibili all'interno di un firewall
>>- Interfacce che usano SQL
>>- Un dipendente che commette un errore o accede a dati sensibili

A seconda della superficie di attacco si mette in relazione la superficie di attacco al layering
Quando sa comincia a crescere di devono avere più livelli di sicurezza per proteggere il sistema.

**Alberi di attacco**
Struttura dati gerarchica che rappresenta un insieme di tecniche per sfruttare le vulnerabilità di sicurezza

**Assurance**
Con che grado di confidenza posso dire che la misura di sicurezza funziona.

---
### Crittografia

#### Cifratura a chiave simmetrica

Necessita di:
- Un forte algoritmo di cifratura
- Mittente e destinatario hanno copie di una chiave segreta

L'algoritmo prende in input una chiave. Ci sono due funzioni e una è l'inverso dell'altra.

Per attaccare un algoritmo a chiave simmetrica ci sono due metodi:
- Criptoanalisi: si basa sulla conoscenza dell'algoritmo
- Attacchi di forza bruta: si provano tutte le possibili chiavi

Advanced encryption standard
La dimensione del blocco è di 128 e le dimensioni delle chiavi potevano essere variabili.

vedi altre slide a casa

**Autenticazione**
- Con confidenzialità: il messaggio è sia cifrato che autenticato
- Senza confidenzialità: messaggio non cifrato

L'autenticazione e la cifratura sono due funzioni che vengono eseguite separatamente.

**Autenticazione del messaggio senza confidenzialità**
Una volta ottenuto il MAC lo concateno al messaggio e lo mando, chi lo riceve scorpora il messaggio dal MAC.

### Funzione Hash sicura

1. Deve essere applicabile a blocchi di qualsiasi dimensione
2. Il codice hash deve essere costante
3. Deve essere una funzione efficiente dal punto di vista computazionale
4. Deve essere *one way* o *resistente alla preimage* (significa che non deve essere invertibile)
5. Resistenza debole alle collisioni ($H(y)=H(x)$). Deve essere impossibile avere due valori che danno lo stesso hash. Proprietà intrinseca della funzione e la probabilità di collisione è minima
6. Anche modificando un byte di un messaggio, cambia il valore dell'hash. 

#### Public-key encryption structure

Ho un plaintext, ho un algoritmo di cifratura. I mittenti cifrano il messaggio con una chiave pubblica e il destinatario decifra il messaggio con una chiave privata.
