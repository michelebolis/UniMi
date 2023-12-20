Problema: errore/guasto in un link
![[photo_57693557043254888915_y.jpg|400]]
Con il ping periodico viene rilevato il guasto, assegnando un costo infinito (in realtà un valore intero massimo che indica infinito). L'informazione viene quindi propagata attraverso il DV
SE pero un altro nodo C propaga il DV prima che il nodo B mandi il DV con il costo infinito, allora viene rilevato che C riesca a raggiungere il nodo con un costo minore di infinito, e B cambia la sua entry creando un loop in cui il pacchetto rimbalza tra i due nodi (bouncing effect)
Quando ad D poi arriverà DV di B, D aumenterà il costo continuamente perché rileva che il costo da B alla destinazione è aumentato (count to infinity)

Questo limite del DV è generato dalla mancanza di sincronizzazione

In realtà il bouncing effect si fermerà prima dell'infinito grazie al raggiungimento del nodo da un altro nodo

Soluzione: Split Horizon 
Convenzione che prevede che ogni nodo quando propaga il proprio costo per una destinazione, propaga il costo reale su tutte le adiacenze che non intende usare per raggiungere la destinazione mentre infinito sulle adiacenze che intende utilizzare per raggiungere la destinazione 

![[photo_5769355704325488895_y.jpg]]