Situazione: [[Nullability]] nel `valore di ritorno`
Vogliamo creare un oggetto che corrisponda al `concetto "nessun valore" o "valore neutro"`
```java
public interface CardSource { 
	Card draw(); 
	boolean isEmpty(); 
	public static CardSource NULL = new CardSource() { 
		public boolean isEmpty() { return true; } 
		public Card draw() { 
			assert !isEmpty(); return null; 
		} 
	}; 
}
```

`NULL diventa un oggetto valido della classe di tipo anonimo che aderisce alla stessa interfaccia`
Serve ad evitare di dover trattare separatamente il caso == null, ma se proprio diventasse necessario si può sempre testare == CardSource.NULL

Un'alternativa è utilizzare gli `Optional`