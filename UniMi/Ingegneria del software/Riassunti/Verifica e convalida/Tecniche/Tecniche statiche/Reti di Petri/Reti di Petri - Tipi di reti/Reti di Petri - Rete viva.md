Una transizione $t$ in una marcatura $M$ si dice viva
- di `grado 0` o `morta` SE non è abilitata in M e in nessuna delle marcature raggiungibili da M
$$\forall M' \in R(P/T, M), \neg M'[t>$$
- di `grado 1`: SE esiste almeno una marcatura raggiungibile da M in cui $t$ è abilitata
$$\exists M' \in R(P/T, M), M'[t>$$
- di `grado 2`: SE per ogni numero $k$ grande a piacere esiste almeno una sequenza ammissibile da M in cui la transizione $t$ scatta $k$ volte
$$\forall k \in N, M[..t..t^1..t^{k-1},t^k>$$
- di `grado 3`: SE esiste almeno una sequenza ammissibile da M in cui la transizione $t$ scatta infinite volte
- di `grado 4` o `viva`: SE in qualunque marcatura raggiungibile da M, $t$ non è morta

`Una rete è viva SE tutte le sue transizioni sono vive`

Esempio
![[Pasted image 20240131085401.png|400]]