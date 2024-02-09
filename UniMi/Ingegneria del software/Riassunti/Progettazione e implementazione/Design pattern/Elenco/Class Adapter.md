![[Pasted image 20231114162744.png]]
```java
public class Adapter extends Adaptee implements Target {
	@Override
	public void request(){
		this.oldRequest();
	}
}
```

Vantaggi
- E' un unico oggetto che puo essere usato contemporaneamente con le due interfacce diverse
- SE un metodo cambia, non devo fare nulla

Svantaggi: possibili problemi con ereditarietà multipla

Situazione in cui usarlo: `codice legacy` perche riesco ad avere un oggetto che puo essere visto come nuovo (perche implementa l interfaccia) e vecchio (perche estende la classe vecchia)