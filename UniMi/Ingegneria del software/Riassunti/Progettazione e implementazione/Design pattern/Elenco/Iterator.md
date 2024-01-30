Gli iteratori permettono di `fornisce un modo di accedere agli elementi di un oggetto in maniera sequenziale senza esporne la rappresentazione`

Questo pattern consiste in una classe `ConcreteIterator` che abbia accesso alla rappresentazione interna del nostro oggetto e esponga i suoi elementi in modo sequenziale tramite i metodi `next()` e `hasNext()`; dovendo accedere alla rappresentazione, molto spesso tale iteratore si realizza come una _classe interna anonima_.

Oltre all'interfaccia Iterator vi è anche `Iterable` che permette l'utilizzo del foreach. 
Definisce un singolo metodo che restituisce un valore minore, uguale o maggiore a 0, a seconda del risultato del confronto.
Con il for each dico esplicitamente che non voglio fare il remove

![[Pasted image 20231101111104.png|500]]

```java
public interface Iterator<E> { 
	boolean hasNext(); 
	E next(); 
	default void remove() { 
		throw new UnsupportedOperationException("remove"); 
	} 
	/* aggiunta funzionale opzionale */ 
	default void forEachRemaining(Consumer<? super E> action) {
		Objects.requireNonNull(action); 
		while (hasNext()) action.accept(next()); 
	} 
}
```

NON posso fare iterable su due attributi 