
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

#### .global main

- All'inzio del programma si deve scrivere `Global main`
	- Può essere accessibile a tutti i file

#### .data

- In questa sezione si elencano tutte le variabili che utilizzeremo nel `.text`

#### .text

- Vengono scritti tutti i comportamenti delle variabili (quello che devono svolgere)

##### Ex.
```js
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

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
.global main

.data

uno: .word 10
due: .word 5

.text
main:

lw $t0, uno
lw $t1, due

mul $t2, $t0, $t1 // fa il prodotto tra $t0 e $t1 e lo carica nel registro $t2

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

