Per ogni iterazione dell'algoritmo del simplesso si sceglie una colonna, variabile entrante in base, che abbia costo ridotto negativo. Facendo entrare tale variabile la funzione obiettivo migliora (passi sempre miglioranti)

Ci possono essere diversi modi per effettuare tale scelta, quando ho piu colonne con costo ridotto negativo

Dobbiamo stare attenti ai casi degeneri che potrebbe causare dei cicli infiniti
La regola di scelta della colonna garantisce che l'algoritmo del simplesso raggiunge l'ottimalità
Diverse strategie
- colonna scelta casualmente tra quelle con costo ridotto negativo
- colonna col minimo coefficiente di costo ridotto
- colonna che produce il maggior miglioramento di z (passi di Pivot piu efficaci)
- la prima colonna con costo ridotto negativo (regola di Bland permette di NON generare mai cicli infiniti) 
La regola di scelta della colonna garantisce che l'algoritmo del simplesso raggiunga l'ottimalità

[[Test di illimitatezza]]