Quando la tabella viene riempita oltre la soglia stabilita viene creata una tabella piu grande (x2) in cui vengono trasferiti tutti gli elementi

Problemi:
- Serve una funzione hash per la nuova tabella
- Costo in termini di tempo

Di solito la funzione hash è parametrica rispetto alla dimensione m
Es $h_m(k)= f(k) \text{ MOD } m$ con f(k) una funzione hash che restituisce un int grande
SE $f$ è uniforme ALLORA anche $hm$ è uniforme

Analisi ammortizzata del tempo
Tabella di dimensione iniziale $m$
Fattore di carico massimo consentito $\alpha= \frac{1}{2}$
Rehashing effettuato ogni volta che si deve inserire in una tabella piena al 50%

| A            | $T_0$         | $T_1$ | …   | $T_k$         |
| ------------ | ------------- | ----- | --- | ------------- |
| dimensione   | $m$           | $2m$  |     | $2^k * m$     |
| max elemento | $\frac{m}{2}$ | $m$   |     | $2^{k-1} * m$ |

Per contenere $N$ chiavi serve una tabella $T_k$ con $k$ intero t.c.
$2^{k-2} m < N \leq 2^{k-1} m$
$\frac{N}{m} \leq 2^{k-1}$
$\log_2 \frac{N}{m + 1} \leq k$
$k< \log_2 N/m +2$

Numero Operazioni in piu per il rehashing
Passare da $T_i$ a $T_{i+1}$
Chiavi da trasferire: $\sum_{i=0}^{k-1} 2^{i-1} * m = m*\sum_{i=0}^{k-1} 2^*i-1* = \frac{m}{2} * \sum_{i=0}^k 2^i = \frac{m}{2} (2^{k} -1)$
$= \frac{m}{2} {2^{\log_2 \frac{N}{m} +2 -1}}$ //dato $k< \log_2 \frac{N}{m} +2$
$= \frac{m}{2} (2^2 \frac{N}{m} -1) = 2N -\frac{m}{2} < 2N$
Numero totale inserimenti per rehashing $<2N$
Numero totale di inserimenti reali $N$
TOT $3N$

In media ogni operazioni di inserimento usa tempo costante
Tempo totale sequenza di $N$ inserimenti con rehashing $O(N)$
Tempo ammortizzato $O(N) / N = O(1)$
SE ciascun inserimento costa $O(1)$ anche se si effettua rehashing il costo degli inserimenti rimane costante ammortizzato

Questo è un metodo molto veloce SE realizzato correttamente
Caso medio non dipende da $N$ ma $N/m$
La cancellazione è solo logica