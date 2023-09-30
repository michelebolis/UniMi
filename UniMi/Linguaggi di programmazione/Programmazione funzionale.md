### Caratteristiche
- Le ==funzioni sono classi di primo livello==: quindi invece di passare come argomento ad una funzione dei dati, posso passare un'altra funzione 
- Uso la ==ricorsione come struttura di controllo== invece del while e del for
- Focus sul ==list processing== o in generale dati organizzati in un insieme, sempre attraverso la ricorsione
- Dato che tutto è una funzione, QUINDI ==non ci sono side effects== (la maggior parte dei linguaggi funzionali puri), non ha stato

### __Conseguenze__
- Riduciamo gli errori in quanto l'errore non si puo propagare piu di troppo non essendoci stato
- E' piu facile dimostrare alcune proprietà del nostro SW in quanto dato quell'input ho SEMPRE quell'output

Obiettivo: modellare ogni cosa come una funzione matematica

### Costruttori:
- #Astrazione per definire la funzione
- #Applicazione per chiamare la funzione
Non essendoci stato, le variabili sono solo nomi.

#λ-Calculus Church and Kleene ∼1930
==λ-espressioni sono fatte da costanti, variabili, λ, . e parentesi==:
- SE x è una variabile o una costante, allora x è una λ expression
- SE x è una variabile e M è una λ expression, ALLORA λx.M è una λ expression
- SE M, N sono λ expression ALLORA (MN) è una λ expression

es 
- Astrazione λx.x+1
- Applicazione (λx.x+1)7

==Applicazione ha priorita a sinistra==
MNP = (MN)P

- [[OCaml]]