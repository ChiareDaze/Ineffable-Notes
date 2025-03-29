Se il codice prevede l'uso di tanti `if...else` si può optare per l'utilizzo di uno `switch`.

L'istruzione selezione uno dei tanti blocchi di codice da eseguire:

```java
switch (espressione)
{
	//codice
	break;

case y:
	//codice
	break;
default:
	//code block
}
```

### Esempio

```java
switch (k % 7)
{
	case 0:
		iniziaLaSettimana();
		break:

	case 1:
		faiLaSpesa();
		break;
	/*...*/
	case 5:
		relax();
		break;

	case 6:
		gitaDellaDomenica();
		break;
}
```

### Parola chiave `yield`

Viene utilizzata nelle espressioni switch per fornire un valore da restituire. Quindi, consente di uscire dallo switch restituendo un valore che diventa il valore dell'espressione switch.

```java
String number = switch (number)
{
	case 1:
		yield "one";

	case 2:
		yield "two";

	default:
		yield "Zero";
}
```

