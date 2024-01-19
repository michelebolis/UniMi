- `Sottodimensionamento`: mi porta a ritrasmettere pacchetti in realtà già ricevuti dal destinatario
- `Sovradimensionamento`: perdo troppo tempo ad aspettare nel caso di ACK perso o di frame non arrivato 

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche $t_{xACK}$ e il $t_{pACK}$.
OSS $t_p$ e $t_{pACK}$ sono uguali, perche è lo stesso canale e la stessa distanza 
$t_{xACK}$ vogliamo che si minimizzi: per far ciò minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere per un tempo minimo calcolato come: $t_x + 2*t_p$

Il tempo T del clock dovrà essere maggiore di $t_x + 2* t_p$