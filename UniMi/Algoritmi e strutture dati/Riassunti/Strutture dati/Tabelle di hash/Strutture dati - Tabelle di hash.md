I dizionari sono una collezione di elementi ciascuno dei quali è identificato da una chiave

Operazioni fondamentali:
- Ricerca
- Inserimento
- Cancellazione

Implementazione:
- Array: capacita fissata inizialmente
- Alberi: strutture dinamiche che necessita di memoria aggiuntiva per i puntatori

| Operazioni    | Array ordinati   | Alberi binari di ricerca | Alberi AVL / 2-3 |
| ------------- | ---------------- | ------------------------ | ---------------- |
| Ricerca       | $\Theta(\log n)$ | $\Theta(n)$              | $\Theta(\log n)$ |
| Inserimento   | $\Theta(n)$      | $\Theta(n)$              | $\Theta(\log n)$ |
| Cancellazione | $\Theta(n)$      | $\Theta(n)$              | $\Theta(\log n)$ |

Il dizionario viene memorizzato in un array
La posizione di un elemento viene applicando una funzione hash alla chiave
chiave --> h --> posizione

Funzione hash $h: U --> \{0,..,m-1\}$ in cui $U$ è l universo delle chiavi mentre $\{0,..,m-1\}$ è lo spazio degli indici

Caso $U=\{0,…,m-1\}$ --> indice=chiave --> tempo ricerca, inserimento e cancellazione è $O(1)$

Es n matricole < 1 000 000
U={0…999 999}
Uso tabella con m=1 000 000
Uso h di identità
n < 200
$n / m = 200 / 1 000 000 = 0.02\%$
MA tabella potrebbe non stare in memoria centrale

[[Tabelle di hash - Fattore di carico]]

Funzioni hash perfette $h: U --> \{0,…,m-1\}$ è perfetta SE $u\neq v$ ALLORA $h(u)\neq h(v)$
È iniettiva
Funzione hash perfette --> grande spreco di memoria

Es n= 20 persone, come chiave uso cognome U=Stringhe
Iniziale 'A' -> 0, …, 'Z' -> 25 NON è perfetta

Nella pratica:
- Il numero di chiavi possibili, $|U|$, è molto piu grande del numeri di chiavi attese
- La dimensione della tabella viene scelta paragonabile al numero di chiavi attese
Es Cognomi <-> Stringhe, consideriamo U=Stringhe di 10 lettere |U|= 2610=1014

[[Tabelle di hash - Collisioni]]

Operazioni
```
Inserimento(elemento e, chiave k)
i <- 0
WHILE i<m AND v[c(k, i)] è occupata DO
	i <- i+1
IF i<m THEN v[c(k, i)] <- (e, k) //inserisci elemento
ELSE errore //tabella piena

Ricerca(chiave k) -> elemento
i <- 0
WHILE i<m AND  v[c(k, i)] è occupata AND v[c(k, i)].chiave!=k DO
	i <- i+1
IF i=m OR v[c(k, i)] è libera THEN RETURN null //non c è
ELSE RETURN v[c(k, i)].elemento
```

Cancellazione(chiave k) è solo una cancellazione logica

es 
![[Pasted image 20240401163106.png|400]]

I costi di ricerca, inserimento e cancellazione dipendono dal costo di scansione
Caso peggiore: $\Theta(n)$
Caso medio: se sparpaglia bene
Con $n$ numero chiavi presenti
$m$=dim tabella
$\alpha= \frac{n}{m}$ fattore di carico

| n° di passi        | Scansione lineare                       | Scansione quadratica / hashing doppio     |
| ------------------ | --------------------------------------- | ----------------------------------------- |
| Chiave trovata     | $\frac{1}{2} + \frac{1}{2(1-\alpha)}$   | $(-\frac{1}{\alpha}) * \log_e (1-\alpha)$ |
| Chiave non trovata | $\frac{1}{2} + \frac{1}{2(1-\alpha)^2}$ | $\frac{1}{(1-\alpha)}$                    |

SE $\lim _{\alpha->1} \frac{1}{(1-\alpha)} -> \infty$
Nella pratica si fissa come valore massimo di $\alpha$, $\frac{1}{2}$ o $\frac{3}{4}$
SE $\alpha$ supera il valore fissato si effettua rehashing

[[Tabelle di hash - Rehashing]]