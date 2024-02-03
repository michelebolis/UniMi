E' necessario generare gli $n$ gettoni in maniera atomica e bisogna consumare gli $n$ gettoni in maniera atomica

Esempio
Generazione: si sfrutta un collegamento bidirezionale da un posto creato e considerato globale collegato a tutte le transizioni (tranne a quello di cui voglio eliminare il costo). In questo modo ho un meccanismo di lock
![[Pasted image 20240131092009.png|400]]
Consumo: approccio simile alla generazione 
![[Pasted image 20240131092040.png|400]]
