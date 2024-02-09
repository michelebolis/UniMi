Situazione: `evitare che una classe che implementa una classe astratta, usi un metodo aggiunto alla classe astratta successivamente, prevedendo comportamenti diversi per diverse istanze`

Possibili soluzioni
- Override: viola Liskov Principle
- Definisco delle interfacce: in cui non do l'implementazione del metodo problematico. MA cosi devo aggiungerne un implementazione per le altre classi
- Delegation: delego qualcun altro dallo svolgere un compito. 

Principi Dependency Inversion e Open Close: `identificare gli aspetti della applicazione che cambiano e separarli da ciò che rimane fisso`

- `template pattern`: SE ho una classe astratta che non implementa per es sort e poi n classi concrete che implementano il sort

- `Delegation strategy`: definisce una famiglia di algoritmi e li rende attraverso l'encapsulation tra di loro intercambiabili 

`L'ereditarietà è sostituita dalla composizione`.
Il client conosce la strategia astratta (interfaccia) che poi viene implementata in diversi modi
Si usa quando `il client non è interessato da quale strategia viene utilizzata`. La differenziazione è a livello di istanza, NON di classe

I comportamenti da diversificare sono definiti in interfacce con classi concrete che implementano ogni diverso comportamento.

![[Pasted image 20231109091133.png]]

es sort di Collections usa un Comparable che è una strategia non fissa, ma che viene implementata in modi diversi

![[Pasted image 20231109090922.png|500]]