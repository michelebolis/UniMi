Cammino da $x$ a $y$ con $x, y \in V$ è una sequenza di vertici $v_0, …, v_k \in V$ t.c. $v_0=x$, $v_k=y$ e $(v_{i-1}, v_i) \in E$ per $i=1, …, k$
Lunghezza del cammino= Numero archi(k)
Cammino semplice: non contiene vertici ripetuti

y è raggiungibile da x SE esiste cammino da x a y
OSS Raggiungibilità non è simmetrica nel grafo orientato

Lunghezza minimo di un cammino = 2
Lunghezza massima di un cammino = $n-1$

Un ciclo è un cammino da un vertice v a v
Un ciclo semplice è un ciclo in cui solo il vertice iniziale è ripetuto

Una catena tra $x$ e $y$, $(x, y \in V)$ è una sequenza di vertici $v_0, …, v_k \in V$ t.c.
$v_0=x, v_k=y$ e $(v_{i-1}, v_i) \in E$ oppure $(v_i, v_{i-1}) \in Є E$ per $i=1, …, k$
Un circuito è una catena chiusa, quindi SE $x=y$

Grafo connesso SE tra ogni coppia di vertici esista una catena
Grafo fortemente connesso SE tra ogni coppia di vertice esiste un cammino

Grafo non orientato: connesso=fortemente connesso

$G'=(V', E')$ è un sottografo di $G=(V, E)$ quando $V' \subseteq V$ e $E' \subseteq E \cap (V' \text{ x } V')$
$G'$ è il sottografo indotto da $V'$ quando $E' \subseteq E \cap (V' \text{ x } V')$
//insieme di vertici e prendo tutti gli archi che incidono su quei vertici

Una componente fortemente connessa in un grafo è un sottografo indotto fortemente connesso massimale
Un grafo non orientato è una componente fortemente connessa
OSS Anche un solo vertice è una componente fortemente connessa

Circuito Hamiltoniano è un circuito che passa per ogni vertice del grafo UNA e UNA SOLA volta
Questo è un problema difficile

Circuito Euleriano è un circuito che passa per ogni arco UNA e UNA SOLA volta
Vertici di grado dispari --> non posso uscire
$\exists$ circuito euleriano SE E SOLO SE $\forall v, S(v)$ è pari

Problema dei ponti di Konigberg: attraversare tutti i ponti una volta tornando al punto di partenza
Non è un grafo perché ho piu volte degli archi uguali --> multigrafi
Basta introdurre vertici fittizi