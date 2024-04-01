Grafo $G=(V, E)$
- $V$ insieme finito di nodi o vertici
- $E \subset V x V$ insieme di archi

Grafo
- Orientato/diretto
- Non orientato: SE E è simmetrica $(x, y) (y, x) = {x, y}$

$(x, y) \in E$ -> $(x, y)$ è incidente su $x$ e su $y$
Grafo non orientato: $x$ e $y$ sono adiacenti
Grafo orientato: $(x, y)$ esce da $x$ entra in $y$, $y$ è adiacente a $x$

es
![[Pasted image 20240401140158.png|300]]

I vicini di un $v \in V$ sono i vertici adiacenti a $v$
Il grado $\delta(v)$ di un vertice $v$ è il numero archi adiacenti su $v$
Grafo orientato:
- $\delta_{in}(v)$ grado in ingresso
- $\delta_{out}(v)$ grado in uscita
- $\delta(v)= \delta_{in}(v)+\delta_{out}(v)$

Considerando
- $|V|=n$
- $|E|=m$
Grafo non orientato = $\sum_{v \in V} \delta(v)= 2m$
Grafo orientato = $\sum_{v \in V} \delta_{out}(v)= m = \sum_{v \in V} \delta_{in}(v)$

[[Grafi - Definizioni]]
[[Albero - Definizione da Grafo]]

La cricca è un grafo non orientato completo
La cricca in un grafo è un sottografo completo

![[Pasted image 20240401145016.png]]

[[Grafi - Rappresentazioni]]
[[Grafi - Attraversamento]]

Grafi pesati con pesi sugli archi
$G= (V, E)$ grafo
$w: E -> R$ funzione peso

Problemi associati
- [[Albero ricoprente minimo - Kruscal]]
- [[Grafo - Algoritmo di Prim]]
- [[Grafi - Cammini minimi]]
- Commesso viaggiatore

es
Problema della colorazione
Colorazione $c: V -> Colori$ t.c. $(x, y) \in E$ ALLORA $c(x)\neq c(y)$
Obiettivo: minimizzare 
Soluzione ammissibile: vertici adiacenti hanno colori differenti
Soluzione ottima: soluzione ammissibile con minimo numero di colori