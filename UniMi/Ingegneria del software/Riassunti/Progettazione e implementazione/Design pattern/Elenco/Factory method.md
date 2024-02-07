Situazione: client non è interessato a che classe concreta viene creata
E' un pattern creazionale che definisce `un'interfaccia per creare un oggetto ma lascia alle sottoclassi la scelta di cosa creare`

| Pattern                              | ES                                   |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20231206093500.png]] | ![[Pasted image 20231206093511.png]] |
Viene definita una classe Creator dotata di metodi di fabbrica che restituisce un'istanza dell'interfaccia Product, lasciando al ConcreateCreator.

Vantaggi: si sfruttano al massimo polimorfismo e collegamento dinamico

[[Abstract Factory]]