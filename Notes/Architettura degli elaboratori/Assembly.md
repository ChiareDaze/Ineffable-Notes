> [!NOTE] Index
> 1. [[#Registri]]
> 2. [[#Sintassi per creare un programma in Assembly]]
> 3. [[#Caricare le variabili nei registri (lw)]]
> 4. [[#Spostare il valore in un altro registro (move)]]
> 5. [[#Somma tra interi (add e addi)]]
> 6. [[#Sottrazione tra interi (sub e subi)]]
> 7. [[#Syscall]]
> 8. [[#Operazioni con le stringhe]]
> 9. [[#Comandi `mult` e `mflo`]]

---
### Registri

>[!info] Cosa sono?
>Sono celle di memoria che contengono dei valori che verranno assegnati nel file di lavoro

#### Registri principali

>[!info] Quali sono?
>- `$zero` registro che contiene la costante 0
>	- Tutti i registri vengono inizializzati con lo stesso valore
>- `$v0` e `$a0` usati per le syscalls
>- Da `$t0` a `$t9` sono registri temporanei
>- `$s0` e `$s7` registri temporanei
>- `coproc1` e `coproc0` registri che contengono double e float

^6cabc1

---
### Sintassi per creare un programma in Assembly

#### .globl main

- All'inzio del programma si deve scrivere `Global main`
	- Può essere accessibile a tutti i file

#### .data

- In questa sezione si elencano tutte le variabili che utilizzeremo nel `.text`

#### .text

- Vengono scritti tutti i comportamenti delle variabili (quello che devono svolgere)

##### Ex.
```js
.globl main

.data

numero: .word 1 //rappresentato in 32 bit

.text
main:
```

- la variabile numero non si trova in nessun registro
---
#### Caricare le variabili nei registri (lw)

- Serve per caricare la variabile all'interno di un registro

```js
.globl main

.data

numero: .word 1 //rappresentato in 32 bit

.text
main:
lw $t0, numero
```

---
#### Spostare il valore in un altro registro (move)

- Possiamo spostare il valore in altri registri

```js
.globl main

.data

numero: .word 1 //rappresentato in 32 bit

.text
main:
lw $t0, numero
move $t1, $t0 //il valore di $t0 deve essere spostato nel resitro $t1
```

>[!warning] 
>Con `move` non sto spostando il valore, il registro `$t0` non si svuota ma sto copiando e incollando il valore nel registro `$t1`

---
#### Somma tra interi (add e addi)

###### Add

```js
add $t2, $t0, $zero //posso scrivere anche $0
```

- Il primo registro `$t2` è il registro di destinazione
- `$t0` e `$zero` sono gli addendi

###### Addi

- "add con i"
- La i sta per "immediato"

```js
addi $t3, $t0, 0
```

- In `$t3` carico la somma tra `$t0` e 0
- `addi` si usa quando si ha come terzo operando un numero

---
#### Sottrazione tra interi (sub e subi)

###### Sub

```js
sub $t2, $t0, $zero
```

- `$t2` è il registro di destinazione
- Esegue la somma tra `$t0` e `$zero`

###### Subi

```js
subi $t3, $t0, 5
```

- `$t2` è il registro di destinazione
- Esegue la somma tra `$t0` e  5
- Viene usato quando il terzo operando quando è un intero
##### Ex.

- Differenza tra due registri

```js
.globl main

.data

numero0: .word 10 
numero1: .word 5

.text
main:
lw $t0, numero0
lw $t1, numero1

sub $t2, $t0, $t1
```

- Esegue la differenza tra `$t0` e `$t1`
---
#### Sottrazione senza caricare un .data (li)

```js
.globl main

.data

numero0: .word 10 

.text
main:
lw $t0, numero0
li $t1, 5

sub $t2, $t0, $t1
```

- Carico nel registro `$t1` un qualcosa di immediato

---
### Syscall

>[!info] Cosa sono?
>Sono tutte quelle chiamate al sistema che vengono scritte per stampare una variabile, chiedere un valore e chiudere un programma

---
#### Stampare una variabile

```js
li $v0, 1 //ho intenzione di stampare un numero
move $a0, $t2 //il contenuto di $t2 va spostato in $a0
syscall
```

- Se vogliamo stampare un numero di deve passare al registro `$v0` il valore 1
- `$a0` è il registro che contiene il valore da stampare 
-  In questo caso il comando `syscall` equivale a dire `print()`
---
#### Chiudere un programma (li $v0, 10)

```js
li $v0, 10 //ho intenzione di terminare l'esecuzione del programma
syscall //chiude il programma
```

- Per chiudere il programma bisogna caricare il registro `$v0` il valore 10
- In questo caso il comando `syscall` chiude il programma

>[!warning]
>Bisogna sempre ricordarsi che di chiudere un programma

---
### Operazioni con le stringhe

```js
.globl main

.data

stringa: .asciiz "ciao" 

.text
main:

la $t0 stringa

li $v0, 4
move $a0, $t0
syscall

li $v0, 10
syscall
```

- `.asciiz` serve per definire la stringa
- Per stampare una stringa si deve caricare nel registro `$v0` il valore 4
#### Cosa cambia tra load word e load address?

- `lw` carica 1 parola (32 bit)
- `la` carica l'indirizzo della variabile

---
#### Stampare un character

- Il valore viene rappresentato in 8 bit

```js
.globl main

.data
char: .byte 'v'

.text
main:

la $t0, char // carico in $t0 il char

li $v0, 4 //voglio stampare il char
move $a0, char //sposto il char nel registro $a0
syscall //eseguo

//modo alternativo

li $v0, 4
la $a0, char
syscall

li $v0, 10
syscall
```

>[!info] Perché c'è `load address` invece di `move`?
>- Se si vuole usare il move bisogna prima caricare il carattere in un registro
>- Con `load address` ho caricato direttamente in `$a0` il valore char
>	- Questa operazione è più efficiente poiché la macchina dovrà fare un'operazione in meno

- Il programma stampa due v attaccate
- Se avessi voluto inserire uno spazio tra le due v dovrei scrivere:

```js
.globl main

.data
char: .byte 'v'
spazio: .asciiz "¥n"

.text
main:

la $t0, char // carico in $t0 il char
la $t1, spazio //caricp lo spazio in $t1

li $v0, 4
move $a0, spazio
syscall

li $v0, 4 //voglio stampare il char
move $a0, char //sposto il char nel registro $a0
syscall //eseguo

li $v0, 4
la $a0, char
syscall

li $v0, 10
syscall
```

---
#### Stampare un float

```js
.globl main

.data
PI: .float 3.14

.text
main:

li $v0, 2
lwc1 $f12, PI //carico PI in $f12
syscall

li $v0, 10
syscall
```

- Per stampare un float si deve caricare nel registro `$v0` il valore 2
- `$f12` svolge lo stesso ruolo di `$a0`
	- La differenza è che in `$a0` viene inserito tutto ciò che non è float o double
- `lwc` sta per load word coproc 

---
#### Operazioni con i double 

```js
.globl main

.data

n: .double 3.1
m: .double 2.12

.text
main:

ldc1 $f0, n
ldc1 $f2, m

li $v0,3
add.d $f12, $f2, $f0 //svolgo la somma tra $f2 e $f0 e poi sposto il risultato el registro $f12

li $v0, 10
syscall
```

- `ldc` è solo per i double
- `m` lo carico nel registro `$f2` poiché i double utilizzano 64 bit
- Per stampare un double si deve caricare nel registro `$v0` il valore 3
- Nel `add.d`, il .d specifica che è un double

---
### Comandi `mult` e `mflo`

#### `Mul` e `mult`

```js
.globl main

.data

uno: .word 10
due: .word 5

.text
main:

lw $t0, uno
lw $t1, due

mul $t2, $t0, $t1 // fa il prodotto tra $t0 e $t1 e lo carica nel registro $t2

//metodo alternativo con mult

mult $t0, $1 //esegue il prodotto e lo carica in $lo
mflo $t2 //"sposta" il prodotto da $lo a $t2

li $v0, 10
syscall
```

>[!info] Differenza tra `mul` e `mult`
>- `mul` prende tre registri (`$t2`, `$t0`, `$t1`)
>- `mult` moltiplicazione tra due registri
>	- il risultato viene caricato nel registro `$lo`
>	- per spostare il valore in un altro registro uso `mflo` (move from lo)

---
### Divisioni

#### `Div` e `divu`

```js
.globl main 

.data 

Uno: .word 10
Due: .word 2

.text
main:

lw $t0, Uno
lw $t1, Due

div $t2, $t0, $t1 //div esegue la divisione tra $t0 e $t1

li $v0, 1
move $a0, $t2
syscall

//metodo alternativo con divu

divu $t0, $t1
mflo $t2

li $v0, 10
syscall
```

>[!info] Cosa succede se la divisione con il resto?
>La parte intera viene caricata nel registro `$lo` e il resto viene caricato nel registro `$hi`

- Per spostare il resto in un registro si deve fare

```js
divu $t0, $t1
mflo $t2
mfhi $t3 //sposta il resto nel registro $t3
```

---
### Funzioni

```js
.globl main
.data

.text
main: //dichiarazione funzione main

li $t0, 1
li $t1, 2
li $t2, 3
li $t3, 6

Operazioni: //dichiarazione funzione Operazione

mul $s0, $t0, $t1 // moltiplica 1*2
div $s1, $t3, $t2 // divide 6/3
add $a2, $s0, $s1 // addiziona riga 12 + riga 14

StampaEtermina: // dichiarazione funzione StampaEtermina

li $v0, 1
move $a0, $s1
sys call

li $v0, 1
move $a0, $s2
syscall

li $v0, 10
syscall
```

#### Sto dividendo il programma in più parti
---

### Jump

#### Salto incondizionato che "salta" da una funzione all'altra

```js
.globl main
.data

.text
main: //dichiarazione funzione main

li $t0, 1
li $t1, 2
li $t2, 3
li $t3, 6

j stampaEtermina

Operazioni: //dichiarazione funzione Operazione

mul $s0, $t0, $t1 // moltiplica 1*2
div $s1, $t3, $t2 // divide 6/3
add $a2, $s0, $s1 // addiziona riga 12 + riga 14

stampaEtermina: // dichiarazione funzione StampaEtermina

li $v0, 1
move $a0, $s1
sys call

li $v0, 1
move $a0, $s2
syscall

li $v0, 10
syscall
```

>[!info]
>- La funzione a `j stampaEtermina` salta e va alla funzione `stampaEtermina`
>- La funzione a `j Operazioni` salta e va alla funzione `Operazione`

- Il programma:
1. Carica nei registri i valori dichiarati
2. Va a `stampaEtermina`
---
### Scorrimento vettore `word`

```js
.global main
.data

vettore: .word 1,2,3,4,5,6,7,8,9,10 //10 elementi: 10 word
N: .word 10 // len del vettore
capo: .asciiz "\n"

.text

main:

	li $t0, 0 //carico in $t0 il valore 0
	lw $t1, N // carico in $t1 la wword N
	la $t4, capo //carico in $t1 lo \n

	while: //funzione while
	bge $t0, $t1, end //quando l'indice è uguale o maggiore alla len del vettore il programma jumpa alla funzione end
	sll $t3, $t0, 2 //shifta di 2 moltiplicando $t0*2
	lw $t3 vettore ($t3) //carico il vettore[indice]

	li $v0, 1 
	move $a0, $t3
	syscall

	addi $t0, $t0, 1 //indice++

	j while //salto al loop

	end:
	li $v0, 0
	syscall
```

>[!info]
>- Il comando `bge` (branch if greater or equal then) è una condizione per il while
>	- Significa che il loop terminerà solo quando $t0 raggiungerà lo stesso valore di $t1 (esempio in python `while i <= N`)

>[!warning]
>- Quando faccio `lw $t3 vettore[indice]` non basta per incrementare l'indice
>- Devo incrementarlo con il comando `addi`

---

### Scorrimento vettore con puntatore

``` js
.global main
.data

vettore: .word 1,2,3,4,5,6,7,8,9,10
N: .word 10
capo: .asciiz "\n"

.text

main:
	la $t0, vettore //carico l'indirizzo del vettore
	lw $t1, N //carico la len del vettore
	sll $t1, $t1, 2 //faccio lo shift logico della len = 10*4 (offset)
	add $t1, $t1, $t0 //addizioniamo l'offset + indirizzo vettore
	la $t4, capo

	loop: 
	bge $t0, $t1, fine //confronto l'indirzzo del vettore e la len

	lw $t3, ($t0) //nel registro $t3 carico vettore[indice]

	li $v0, 4
	move $a0, $t4
	syscall

	addi $t0, $t0, 4 //incremento l'indice

	j loop

	fine:
	li $v0, 10
	syscall
```
---

### Jump and Link

```js
.global main
.data

vettore: .word 1,2,3,4,5,6,7,8,9,10
N: .word 10
capo: .asciiz "\n"

.text

main: 

la $t0, vettore
li $t1, 0
lw $t2, N
la $t3, capo

jal Funzione

li $v0, 10
syscall

Funzione:
		while:
		bge $t1, $t2, fine //condizione while
		sll $t4, $t1, 2 //shift del registro per andare all'indice successivo
		add $t4, $t0, $t4 //indirizzo vettore + offeset
		lw $t4, ($t4) //lettura del vettore[indice]

		li $v0, 1 
		move $a0, $t3
		syscall

		li $v0, 4 //creo spazio per avere una colonna di valori
		move $a0, $t3
		syscall

		addi $t1, $t1, 1 //incremento dell'indice

		j while

		fine:
		jr $ra
```

>[!info] Funzione `jal`
>- Oltre al jump c'è un collegamento
>- Memorizza il valore del program counter (indirizzo dell'istruzione successiva PC+4) nel registro `$ra`

#### Jump register

- Quando finisce l'iterazione non c'è più la semplice `syscall`, ma c'è `jr $ra`
- Devo saltare alla funzione che ho chiamato (vado alla riga dopo il `jal Funzione`)

>[!info]
>E' buona norma utilizzare il Jump and Link per rendere il programma ben strutturato

---

### Esercizio somma elementi di un vettore

```js
.globl main
.data

vettore: .word 1,2,3,4,5,6,7,8,9,10 //vettore
N: .word 10 //len del vettore
capo: .asciiz "\n"


.text

main: //funzione principale

la $t0, vettore //indirizzo del vettore in $t0
li $t1, 0 //indice
lw $t2, N //carico la len del vettore
la $t3, capo //carico lo \n

jal Funzione

li $v0, 1
move $a0, $t5
syscall

li $v0, 10
syscall

Funzione:
while: bge $t1, $t2, fine
	sll $t4, $t1, 2 //offset
	add $t4, $t4, $t0 //offset + indirizzo del vettore
	lw $t4, ($t4) //vettore[indice]
	
	add $t5, $t5, $t4 //sommo gli elementi del vettore e li inserisco in $t5
	
	addi $t1, $t1, 1 //incremento il contatore
	
	j while
	
	fine: jr $ra
```
---

### Esercizio somma elementi pari di un vettore

```js
.globl main

.data
vettore:.word 1,2,3,4,5,6,7,8,9,10 //vettore
N:.word 10
capo:.asciiz "-"

.text 
main:
	la $t0, vettore //carico il vettore in $t0
	li $t1, 0
	lw $t2, N 
	li $t4, 2 //divisore
	
	
	jal Funzione
	
	li $v0, 10 //chiude il programma
	syscall
	
Funzione:
		while:
			
			bge $t1, $t2, fine
			sll $t3, $t1, 2 //shift logico dell'indice per 4, offset
			add $t3, $t3, $t0 //somma tra vettore e offset
			lw $t3, ($t3) //vettore[indice]
			
			divu $t3, $t4 //divido il numero per 2 per vedere se è pari
			mfhi $t5 //carico il resto della divisione in $t5

			beq $t5,0, pari //condizione
			
			//se falso
			j incremento
			
			//se vero
			pari:
				li $v0, 1
				move $a0, $t3 //stampo il valore
				syscall
				j incremento
			
			incremento:
			addi $t1, $t1, 1			
			
			j while

		
		fine: 
			jr $ra

```
---

### Loop e salti condizionati

#### Condizioni

##### `beq` (branch if equal)

```js
beq $t0, $t1, fine
```

>[!info]
>Salta alla funzione `fine` se `$t0 == $t1`

##### `bge` (branch on greater or equal)

```js
bge $t0, $t1, fine
```

>[!info]
>Salta alla funzione `fine` quando `$t0 >= $t1`

##### `.eqv`

>[!info]
>Serve per rinominare i registri

```js
.eqv indice $t0 //rinomino $t0 con il nome "indice"
```

- Quando definisco le operazioni non scriverò `$t0` ma scriverò direttamente `indice`

```js
addi indice, indice, 1
```

- Si possono anche rinominare le funzioni

```js
.data
.eqv indice $t0
.eqv numero $t1
.eqv incremento addi indice, indice 1

.text
while: beq, indice, numero fine

	   incremento

	   j while
```
---

### Esercizio somma elementi indici pari e indici dispari

```js
.globl main


.data
vettore: .word 1,3,1,3,1,3,1,3,1,3 #vettore
N: .word 10 #len vettore
spazio: .asciiz "\n"


.text
main:

la $t0, vettore
li $t1, 0 #indice vettore
lw $t2, N
li $t3, 2
la $t9, spazio

jal Funzione

li $v0, 1
move $a0, $t6
syscall

li $v0, 4
move $a0, $t9
syscall

li $v0, 1
move $a0, $t7
syscall

li $v0, 10
syscall

Funzione:
		while:
			bge $t1, $t2, fine
			sll $t4, $t1, 2 #shift logico
			add $t4, $t4, $t0 #somma tra vettore e offset
			lw $t4, ($t4) #vettore[indice]
			
			divu $t1, $t3 #divido l'indice per 2
			mfhi $t5 #carico il resto in $t5
			
			bne $t5, $zero, dispari
			
			add $t6, $t6, $t4
			j incremento
			
			dispari:
				add $t7, $t7, $t4
			
			incremento:
				addi $t1, $t1, 1
				
			
			j while
		
		fine:
			jr $ra
```
---
### Matrici 

![[Pasted image 20240616130241.png|150]]

#### Definizione di una matrice

```js
matrice: .word 0:400
dim: .word 20 //lato della matrice
```

>[!info]
>- `0` significa che è inizializzata a 0
>- `400` significa che è una matrice quadrata 20x20

##### Ex. somma diagonali di una matrice

```js
.globl main

.data
matrice: .word 0:400 //matrice 20x20
dim: .word 20 //lato della matrice

.text
main:
move $t0, $0 //inizializzo coordinata x
move $t1, $0 //inizializzo coordinata y
move $t2, $0 //inizializzo somma iniziale
lw $t3, dim //carico il lato della matrice

cicloRighe: //scorre le righe
	bge $t1, $t3, fine
	ciclo colonne:
		bge $t0, $t3, nextRiga
		beq $t0, $t1, sommaDiagonali
		addi $t0, $t0, 1
		j ciclo colonne
		
		sommaDiagonali:
			add $t2, $t1, $t0
			sll $t0, $t0, 2 //PC + 4
			lw $t0, matrice($t0)


nextRiga:
	li $t0, 0 //azzera il contatore della coordinata x
	addi $t1, $t1, 1 //aggiorna il contatore delle righe
	j cicloRighe


fine:
	li $v0, 1
	move $a0, $t2
	syscall
	
	li $v0, 10 //chiude il programma
	syscall
```
---

## Scorrere un vettore al contrario (`in range (len(vettore), 0)`)

```js
.globl main

.data
vettore: .word 1,2,3,4,5,6,7,8,9,10 //vettore
N: .word 0 //dimensione vettore
capo: .asciiz "\n"

.text
main:
la $t0, vettore
li $t1, 9 //indice vettore
lw $t2, N
la $t3, capo

while:
	blt $t1, $t2, fine //controlla se $t1 < $t2
	
	sll $t4, $t1, 2
	add $t4, $t4, $t0
	lw $t4, ($t4)
		
stampa:
	subi $t1, $t1, 1
	li $v0, 1
	move $a0, $t4
	syscall
	
	li $v0, 4
	move $a0, $t3
	syscall
	
	
	j while

fine:
	li $v0, 10
	syscall

```
---

### Doppio scorrimento di un vettore

```js
.globl main

.data
vettore: .word 1,2,3,4,5,6,7,8,9,10 //vettore
N: .word 5 //stop while 1
M: .word 4 //stop while 2
capo: .asciiz "\n"

.text
main:
la $t0, vettore
li $t1, 0 //indice vettore che parte dall'inizio
lw $t2, N
la $t3, capo
lw $t5, M
li $t6, 9 //indice del vettore che parte dalla fine
move $s0, $0 //somma


while1: 
	bge $t1, $t2, fine
	while2:
		ble $t6, $t5, fine
		sll $t4, $t1, 2
		sll $t7, $t6, 2
		add $t4, $t4, $t0
		add $t7, $t7, $t0
		lw $t4, ($t4)
		lw $t7, ($t7)
		
	addizione:
		add $s0, $t4, $t7
		
		li $v0, 1
		move $a0, $s0
		syscall
		
		li $v0, 4
		move $a0, $t3
		syscall
		
		addi $t1, $t1, 1
		subi $t6, $t6, 1		
		j while1
		
fine:
	//bge $t5, $t6, while2 (?)
	li $v0, 10 //chiude il programma
	syscall


```