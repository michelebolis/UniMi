Situazione: una classe richiede un numero molto grande di parametri alcuni obbligatori e altri facoltativi

- Costruttori telescopici: si realizza un costruttore completo che richiede tutti i parametri e una serie di costruttori secondari

Svantaggi: il numero di costruttori cresce esponenzialmente e problemi con parametri opzionali dello stesso tipo

-  JavaBeans: costruttore che prende in input solamente i parametri obbligatori prevedendo poi dei setter per quelli facoltativi

Svantaggi: l'oggetto non puo essere immutabile e questo pattern prevede che esista un oggetto non ancora costruito completamente

- Builder pattern
![[Pasted image 20240203091229.png|400]]

Data una classe da costruire MyClass. rendo privato il suo costruttore il quale prenderà in input un'istanza di una classe Builder, classe statica pubblica e interna a MyClass.

La classe Builder esporra un costruttore con solo i parametri obbligatori e una serie di setter per i parametri opzionali. Il metodo build() restituirà un istanza di MyClass inizializzata con i parametri obbligatori e opzionali

Vantaggi: 
- rendendo privato il costruttore MyClass ci si assicura che le sue istanza siano costruite unicamente tramite Builder
- i setter, ritornando un Builder, permettono una concatenazione di setter
- risolve problemi legati alla concorrenza infatti il metodo build() restituisce l'istanza già completa

```java
MyClass inst = (new MyClass.Builder(mandatoryField).withOptionalField1(optionalField1)).build();

```