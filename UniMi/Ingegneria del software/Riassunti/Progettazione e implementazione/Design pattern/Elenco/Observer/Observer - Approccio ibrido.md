Partiamo col dire che molto spesso nei casi reali gli approcci _push_ e _pull_ sono ibridati tra di loro: ad `update` viene passato sia il Subject che quella parte di stato utile a tutti gli Observer, mentre qualora gli serva qualcosa di più specifico essi se lo andranno a prendere con il getter.

Il vero problema di entrambi gli approcci è però quello delle dipendenze: nel caso _push_ dipendiamo dalla rappresentazione interna del Subject, mentre nel caso _pull_ dalla sua classe concreta. Poiché tale dipendenza non è facilmente eliminabile, piuttosto che lasciarla nascosta nel casting conviene **esplicitarla**:

- all’interno dell’Observer salvo l’istanza di Observable a cui mi sono sottoscritto, così al momento dell’`update` posso verificare direttamente che l’istanza sia quella al posto di fare un casting;
    
- creiamo una classe `State` e l’aggreghiamo sia nell’Observer che nell’Observable concreto in modo che essa nasconda la rappresentazione reale dello stato.
    

Otteniamo dunque un codice simile al seguente:

```java
public class State { /*rappresentazione interna dello stato */ }  
public class Observable {     
	private State stato;     
	private List<Observer> observers = new ArrayList<>();      
	
	public void addObserver(@NotNull Observer obs) { 
		observers.add(obs); 
	}     
	public void removeObserver(@NotNull Observer obs) { 
		observers.remove(obs); 
	}     
	public void notifyObservers() {         
		for (Observer obs: observers) update(this, stato);     
	} 
}  
public class Subject extends Observable {      
	public void setState(State nuovoStato) { ... }     
	public State getState() { return super.stato; }     
	/* Opzionale: altri metodi getter */ 
}  
public interface Observer {     
	public void update(Observable subject, Object stato); 
}  
public class ConcreteObserver {     
	private Observable mySubject;      
	@Override     
	public void update(Observable subject, Object stato) {       
		if (subject == mySubject) {  ... }     
	} 
}
```