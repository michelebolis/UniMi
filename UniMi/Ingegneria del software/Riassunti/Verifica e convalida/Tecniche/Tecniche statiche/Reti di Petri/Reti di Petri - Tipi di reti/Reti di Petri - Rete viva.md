Una transizione $t$ in una marcatura $M$ si dice `viva`
- di `grado 0` o `morta` SE non è abilitata in M e in nessuna delle marcature raggiungibili da M
$$\forall M' \in R(P/T, M), \neg M'[t>$$
- di `grado 1`: SE esiste almeno una marcatura raggiungibile da M in cui $t$ è abilitata
$$\exists M' \in R(P/T, M), M'[t>$$
- di `grado 2`: SE per ogni numero $k$ grande a piacere esiste almeno una sequenza ammissibile da M in cui la transizione $t$ scatta $k$ volte
$$\forall k \in N, M[..t..t^1..t^{k-1},t^k>$$
- di `grado 3`: SE esiste almeno una sequenza ammissibile da $M$ in cui la transizione $t$ scatta infinite volte, cioè non la riuscirò mai a farla diventare morta (MA NON vuol dire che è sempre abilitata)
- di `grado 4` o `viva`: SE in qualunque marcatura raggiungibile da M, $t$ non è morta

`Una rete è viva SE tutte le sue transizioni sono vive`

Esempio
$T_0$ è di grado 0, $T_1$ è di grado 1, $T_3$ è di grado 3, $T_4$ è di grado 4
Notare che $T_2$ è di grado 2 perché è vero che all’infinito posso generare gettoni in $p_2$, ma dal momento che scatta $t_1$ si perde questa possibilità, permettendo a $t_2$ di scattare tante volte quanti sono i gettoni in $p_2$
![[Pasted image 20240131085401.png|300]]