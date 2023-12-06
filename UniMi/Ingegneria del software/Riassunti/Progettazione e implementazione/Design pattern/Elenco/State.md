Permette di modellare cambiamenti di comportamento al cambiare dello stato dell'oggetto
Viene partizionato il comportamento nelle varie classi di stato
Viene reso esplicito il passaggio di stato 

![[Pasted image 20231206093037.png]]

```java
public class Context { 
	private State state; 
	public void setState(@NotNull State s) { state = s; } 
	public void sampleOperation() { state.sampleOperation(this); } }
```

