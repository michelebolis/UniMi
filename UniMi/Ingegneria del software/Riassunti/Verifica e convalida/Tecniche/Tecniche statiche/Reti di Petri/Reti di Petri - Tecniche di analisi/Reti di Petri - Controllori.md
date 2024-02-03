Si possono **modellare dei controllori** che forzano o limitano certi comportamenti del sistema
È possibile definire gli **stati** come situazioni che _si possono verificare_, e le **transizioni** come _eventi che si verificano_. Lo scopo è **controllare** che le transizioni possano svolgere certe operazioni, oppure no.

Esistono due **classi di problemi** che limitano la capacità espressiva dei controllori:
- **non tutte le transizioni sono osservabili**: il controllore non ne ha le capacità, oppure è un’attività troppo onerosa;
- l’osservazione di alcune situazioni ne **comporta il cambiamento**.

OSS NON tutto è controllabile 

Nel modello del **controllore a stati proibiti**, l’attività di _controllo_ si traduce formalmente in una **combinazione lineare** delle marcature che deve rimanere sotto una certa soglia.  
Si vincola quindi per un **sottoinsieme di posti** che la combinazione lineare di una marcatura M� con un **vettore dei pesi** L� sia minore o uguale (e non solo _uguale_ come nei P�-invarianti) di una soglia data:

$$LM \leq b$$
