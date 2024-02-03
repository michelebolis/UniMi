Model contiene lo stato condiviso, le view sono una serie di classi che costituiscono l'interfaccia con l'utente e infine i controller, uno pe rogni vista, sono classi che si occupano della logica dell'applicazione

| Passaggi                                                                                                                                   | Rappresentazione                     |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------ |
| L'utente interagisce con una vista che passe le chiamate al Controller che manipola il Model, che a sua volta chiama gli eventi dell Vista (politica pull) | ![[Pasted image 20231206102337.png]] |
Facendo riferimento ad altri patter, le view sono viste come Observer del Model e come Composite (in quanto GUI) mentre i Controller come Strategy

Utilizzo: GUI

Svantaggi: 
- dipendenza circolare rende complesso il testing
- le view e i controller dipendono dall'interfaccia
