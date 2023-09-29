OCaml
Tutto è una funzione, QUINDI non ha side effects (la maggior parte dei linguaggi funzionali puri), non ha stato

Dato quell'input ho SEMPRE quell'output

Per mettere insieme le funzioni, posso usarle come argomento per altre funzioni

Uso la ricorsione invece del while e del for

Processare dati organizzati in un insieme

Riduciamo gli errori in quanto l'errore non si puo propagare piu di troppo non essendoci stato

Obiettivo: modellare ogni cosa come una funzione matematica

Astrazione per definire la funzione

Applicazione chiamo la funzione

TUTTE le espressione lamfa sono composte da variabili, costanti, lamda stesso e la parentizzazione

SE x è una variabile o una costante, allora x è una lamda expression

SE x è una variabile e M è una lamda expression, ALLORA lamdaxM è una lamda expression

Applicazione a sinistra

MNP = (MN)P

Lamdax.xy

Ocaml è fortemente typato ma posso in realta anche ometterli

let è una funzione che assegna

I 2 ;; sono il comando per dire esegui

Le funzioni se non ritornano nulla è unit

NomeFunzione argomento

succ -1 // MA -1 è una funzione e poi 1 QUINDI sto dando a succ come argomento una funzione int -> int cioè l operazione -

Un nuovo binding (riuso di un nome) nasconde la prima volta che ho usato quel nome

Composizione di funzione

Let compose f g x

Let compose (f, g) x

Hanno tipi diversi

* rappresenta la tupla, le parentesi sono fonte di errore

La prima

If non si usano, ma il pattern matching su una qualsiasi espressione

Catchall si dovrebbe sempre mettere con un _