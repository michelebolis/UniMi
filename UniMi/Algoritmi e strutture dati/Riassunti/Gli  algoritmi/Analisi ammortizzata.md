Caso: incrementare un contatore di n bit
Costo come i bit da ispezionare
Caso peggiore contatore composto da soli 1 --> li devo ispezionare tutti quindi costo n
Potremmo verderlo come un array che a come entry 0 il bit meno significativo

```
ALGORITMO incrementoContatore(Array v[0…n-1])
i <- 0
WHILE i<n AND v[i] = 1 DO
	v[i] <- 0
	i <- i+1
IF i<n THEN v[i] <- 1
```

Caso peggiore: ispeziono n bit --> $\Theta(n)$
$k$ incrementi successivi --> $O(k*n)$
Queste non sono operazioni indipendenti ma dipendono dalle operazioni precedenti
Costo peggiore viene ammortizzato nei tempi successivi
Il bit in posizione i cambia ogni $2i$ incrementi

$$T(n, k)= k + \lfloor \frac{k}{2} \rfloor + \lfloor \frac{k}{2^2} \rfloor + … + \lfloor \frac{k}{2^{n-1}} \rfloor$$
$$= \sum_{i=0}^{n-1}{\lfloor\frac{k}{2^i} \rfloor} \leq \sum_{i=0}^{n-1} \frac{k}{2^i} = k*\sum_{i=0}^{n-1} \frac{1}{2^i} \leq k*\sum_{i=0}^{\inf} (\frac{1}{2})^i = k* \frac{1}{(1- \frac{1}{2})} = 2k$$

In media: $T_{a,n} (k)= \frac{T(n, k)}{k} = \frac{2k}{k} = 2$
$T_{a,n}$ è il costo/tempo ammortizzato

ATT nel quick sort non avevo una dipendenza quindi consideravo in media il tempo mentre qui ho una dipendenza
Analisi ammortizzata quando sequenza di operazioni in cui ho una dipendenza tra i risultati