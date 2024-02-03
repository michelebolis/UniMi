Permette di `modellare cambiamenti di comportamento al cambiare dello stato dell'oggetto` invece di utilizzare un if o switch
Si basa sul concetto di automa a stati finiti

L'interfaccia State raggruppa la definizione di tutte le azioni rappresentate da metodi mentre una classe concreta per ogni stato definisce che effetto hanno tali azioni 
Infine una classe context contiene un riferimento ad uno stato che rappresenta lo stato corrente e delega ad esso la risposta alle azioni.

Viene reso esplicito il passaggio di stato 

![[Pasted image 20231206093037.png]]

```java
public class Context { 
	private State state; 
	public void setState(@NotNull State s) { state = s; } 
	public void sampleOperation() { state.sampleOperation(this); } }
```

Chi ha la responsabilità di cambiare lo stato:
- gli State realizzano le transizioni, MA poiche setState richiede uno State, richiede che gli stati si conoscano tra di loro introducendo quindi una dipendenza tra stati
- il Context realizza le transizioni: il Context quindi richiama il metodo di State e ne intercetta il risultato decidendo se cambiare o meno lo stato. MA si ritornerebbe ad un approccio con if e switch, risultando fattibile quindi se ci sono poche transizioni