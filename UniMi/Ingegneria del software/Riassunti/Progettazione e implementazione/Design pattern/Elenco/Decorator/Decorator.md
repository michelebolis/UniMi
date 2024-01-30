Scopo: `Aggiungere nuove funzionalità o caratteristiche dinamicamente`
[[Decorator - Antipattern]]

Il decorator pattern aggiunge nuove responsabilità tramite l'aggiunta di nuovi oggetti
[![](https://marcobuster.github.io/sweng/mdbook-plantuml-img/66d161eb9e65c5f8314ad9a2d89c3de5f13730a2.svg)](https://marcobuster.github.io/sweng/mdbook-plantuml-img/66d161eb9e65c5f8314ad9a2d89c3de5f13730a2.svg)

A prima vista lo schema UML ricorda molto quello del pattern Composite: abbiamo un’interfaccia _Component_ implementata sia da un _ConcreteComponent_, ovvero una base della pizza nel nostro esempio, sia da una **classe astratta Decorator**, la quale è poi estesa da una serie di _ConcreteDecorator_. 
A differenza del Composite, tuttavia, qui `ciascun Decorator aggrega una e una sola istanza di Component`: tali decoratori sono infatti dei `wrapper`, degli oggetti che _ricoprono_ altri per aumentarne dinamicamente le funzionalità.  
È importante notare che i Decorator ricevono come oggetto da ricoprire al momento della costruzione un _generico Component_, in quanto questo permette ai decoratori di decorare oggetti già decorati. Questo approccio “ricorsivo” permette di creare una catena di decoratori che definisca a runtime in modo semplice e pulito oggetti dotati di moltissime funzionalità aggiunte. 
`I decoratori esporranno infatti i metodi definiti dall’interfaccia delegando al Component contenuto l’esecuzione del comportamento principale e aggiungendo la propria funzionalità a posteriori`: in questo modo la “base” concreta eseguirà il proprio metodo che verrà successivamente arricchito dai decoratori in maniera del tutto trasparente al Client.

Vista la somiglianza, inoltre, `pattern Decorator e Composite sono facilmente combinabili`: si può per esempio immaginare di creare gruppi di oggetti decorati o decorare in un solo colpo gruppi di oggetti semplicemente facendo in modo che Composite, Decorator e classi concrete condividano la stessa interfaccia Component.

Al momento della costruzione un Decorator salva al proprio interno l’istanza del Component da decorare. Come sappiamo questo darebbe luogo ad un’_escaping reference_, ma in questo caso il comportamento è assolutamente voluto: dovendo decorare un oggetto è infatti sensato pensare che a quest’ultimo debba essere lasciata la possibilità di cambiare e che debba essere il decoratore ad adattarsi a tale cambiamento.

`Nella classe astratta Decorator viene inserita tutta la logica di composizione`, permettendo così di creare nuovi decoratori con estrema facilità. Spesso, inoltre, se i decoratori condividono una certa parte di funzionalità aggiunte queste vengono anch’esse estratte nella classe astratta creando invece un metodo vuoto protetto che i decoratori reimplementeranno per operare la loro funzionalità aggiuntiva.

Si noti come l’uso della visibilità `protected` renda l’override del metodo possibile anche al di fuori del package, aumentando così la facilità di aggiunta di nuovi decoratori.


Volendo vedere un esempio concreto di utilizzo di questo pattern è sufficiente guardare alla libreria standard di Java: in essa infatti gli `InputStream` sono realizzati seguendo tale schema.

[[Decorator - Esempio]]