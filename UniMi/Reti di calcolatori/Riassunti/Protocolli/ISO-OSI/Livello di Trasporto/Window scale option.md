Il campo window size nell'header è di 16 bit, permettendo una dimensione massima di $2^{16}$.
Tuttavia per avere una dimensione maggiore, si utilizza la window scale option (inclusa nel segmento SYN)
Formato

| Campo      | Dimensione | Descrizione                      |
| ---------- | ---------- | -------------------------------- |
| NOP option | 8 bit      | con kind=1, è usato come padding per raggiungere i 32 byte |
| kind = 3   |            |                                  |
| length = 3 |            |                                  |
| Shift count           |            | il window size è ottenuto moltiplicando per $2^n$ con $n$ il valore nello shift count. es shift count = 14 (il suo max), $65 535 * 2^{14}$                                 |