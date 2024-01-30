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