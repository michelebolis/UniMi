La `design knowledge` è la conoscenza del design architetturale di un progetto
Questa conoscenza nasce da 
- nostra `memoria`: non è efficace perché nel tempo si erode
- `documenti` di design: se non viene aggiornato di pari passo con il codice rimane disallineato, risultando più dannoso che d’aiuto
- `piattaforme di discussione / issue management / version control`: le informazioni sono sparse in luoghi diversi e di conseguenza difficili da reperire e rimane il problema di mantenere aggiornate queste informazioni. 
- `Modelli specializzati` ([[UML Diagram]]) (model driven design): diagrammi UML si è cercato di sfruttare l’approccio _**generative programming**_, ovvero la generazione automatica del codice a partire da specificazioni di diagrammi. Con l’esperienza si è visto che non funziona.
- `codice`: è possibile capire il design ma è difficile rappresentare le ragioni della scelta


Per condividere tali scelte di design (il _know how_) è possibile sfruttare:
- `metodi`: con pratiche (come Agile) o addirittura l’object orientation stessa, che può essere un metodo astratto per condividere scelte di design.
- [[Design pattern]]: fondamentali per condividere scelte di design, sono utili anche per generare un vocabolario comune (sfruttiamo dei nomi riconosciuti da tutti per descrivere i ruoli dei componenti) e aiutano l’implementazione (i pattern hanno delle metodologie note per essere implementati). I pattern non si concentrano sulle prestazioni di un particolare sistema ma sulla generalità e la riusabilità di soluzioni a problemi comuni;
- `principi`: per esempio i principi del [[OO - Object Orientation]] o [[SOLID]].

Concetto di [[Stato]]