- Sottodimensionamento: mi porta a ritrasmettere pacchetti in realtà già ricevuti dal destinatario
- Sovradimensionamento: perdo troppo tempo ad aspettare nel caso di ACK perso o di frame non arrivato 

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche $T_{xACK}$ e il $T_{pACK}$.
OSS $T_p$ e $T_{pACK}$ sono uguali, perche è lo stesso canale e la stessa distanza 
$T_{xACK}$ vogliamo che si minimizzi: per far ciò minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere un tempo minimo calcolato come: $T_x + 2*T_p$

T dovrà essere maggiore di $T_x + 2* T_p$