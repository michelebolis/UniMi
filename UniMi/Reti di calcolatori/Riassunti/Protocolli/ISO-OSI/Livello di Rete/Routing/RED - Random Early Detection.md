Usato con le `code best-efford`, cerca di `prevenire` l'insorgenza del problema di traffico a burst
Un router normalmente scarta i pacchetti se la coda è piena
Con TCP ogni volta che un pacchetto è perso, la sorgente lo rileva e dimezza il suo rate per nuovi pacchetti. Questo pero causa un riempimento dello code e una perdita di pacchetti 

Con RED quando un pacchetto arriva e la coda è piena, un pacchetto che è nella coda viene selezionato randomicamente e scartato. In questo modo un numero ridotto di diversi applicativi è coinvolto e viene migliorato l'utilizzo di banda

Vengono prese due soglie
- `MIN threshold`
- `MAX threshold`
- Viene definita continuamente una `AvrLEN`
$L_{AVG} = \alpha^{L_{OLD}} + (1-\alpha)*L_{CURRENT}$
con $0.5 < \alpha < 0.8$

Casi:
- SE AvrLEN < MinTH: il nuovo pacchetto entra nella coda
- SE AvrLEN < MaxTH: il nuovo pacchetto è scartato
- SE MaxTH < AvrLEN < MinTH: un pacchetto nella coda viene randomicamente selezione, scartato e il nuovo pacchetto entra nella coda
