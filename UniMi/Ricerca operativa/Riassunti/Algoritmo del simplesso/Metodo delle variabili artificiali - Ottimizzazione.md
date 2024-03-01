Per evitare di dover eseguire $m$ passi di pivot per espellere dalla base le $m$ variabili artificiali, partendo da un problema in forma alle disuguaglianze, riscrivo in modo che il termine noto $b$ sia $\geq 0$.
Posso usare le variabili di slack o surplus come variabili artificiali

Per i vincoli di $\leq$: introduco variabili di slack positive
Per i vincoli di $\geq$: introduco variabili di slack negative
![[Pasted image 20240301105705.png]]
Le variabili di slack $\hat{x}_i$ per i vincoli $i \in I_1$ soddisfano gia la prima condizione per la forma canonica

Sia $h \in I_2$ l'indice del vincolo col massimo valore del termine noto.
$$h = argmax_{i \in I_2}\{b_i\}$$
Sottraendo ogni riga $i \in I_2 \backslash \{h\}$ dalla riga $h$, si ottengono vincoli equivalenti con termine noto non negativo e variabile $\hat{x}_i$ con coefficiente unitario

Bisognerà introdurre variabili artificiali per il vincolo $h$ e per i vincoli in $I_3$