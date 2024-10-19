L'idea è quella di nascondere i dettagli di implementazione di un oggetto rendendo accessibili solo le informazioni all'esterno. 
Si ottiene attraverso l'utilizzo dei modificatori di accesso `private`, `protected` e `public` che consentono di controllare il livello di visibilità degli elementi all'intermo della classe.

### Come funziona?

Gli attributi di una classe vengono dichiarati come `private` in modo che possano essere accessibili solo all'interno della classe stessa. Questo impedisce agli oggetti esterni di accedere direttamente ai dati dell'oggetto, evitando così manipolazioni indesiderate.

Per consentire l’accesso ai dati incapsulati, vengono definiti dei metodi pubblici, chiamati getter e setter. I **getter** permettono di leggere il valore di un attributo, mentre i **setter** permettono di modificarlo. Questi metodi agiscono come interfaccia tra l’oggetto e il mondo esterno, garantendo il controllo sull’accesso e la modifica dei dati.

I metodi di una classe vengono dichiarati come `private`, `protected` o `public` a seconda del livello di visibilità desiderato. I metodi `private` sono accessibili solo all’interno della classe, mentre i metodi `public` possono essere chiamati da qualsiasi parte del codice. I metodi `protected` sono accessibili all’interno della classe e nelle sue sottoclassi.

### Quali sono i vantaggi

1. Rende il codice più modulare e facile da mantenere
2. I dati dell'oggetto sono protetti da eventuali modifiche accidentali o non autorizzate
3. Facilita il riutilizzo del codice perché gli oggetti possono essere utilizzati senza conoscere i dettagli di implementazione
4. Rende più semplice apportare modifiche all'impelentazione di un oggetto senza influenzare il codice che lo utilizza

#### Esempio persona


```java
package Persona;  
public class Persona  
{  
    private String nome;  
    private int eta;  
  
    public Persona (String nome, int eta)  
    {  
        this.nome = nome;  
        this.eta = eta;  
    }  
    public void setNome(String nome)  
    {  
        this.nome = nome;  
    }  
  
    public void setEta(int eta)  
    {  
        this.eta = eta;  
    }  
  
    public String getNome()  
    {  
        return nome;  
    }  
  
    public int getEta()  
    {  
        return eta;  
    }  
  
    @Override  
    public String toString()  
    {  
        //return "nome: " + nome + " eta': "+ eta;
        return String.format("nome: %s eta': %d", nome, eta);  
    }  
}
```

