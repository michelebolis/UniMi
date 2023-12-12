Nascono per descrivere sistemi concorrenti

Lo stato è una composizione di tanti di tanti stati parziali
Le transazioni sono state promosse a nodi

Una rete di Petri è una quintupla $[P, T;F,W,M_0]$ con:
- $P$ l'insieme dei posti
- $T$ l'insieme delle transizioni
- $F$ la relazione di flusso t.c. $F \subseteq (P \text{ x } T) \cup (T \text{ x } P)$
- $W$ la funzione peso t.c. $W: F -> N^+$
- $M_0$ la funzione marcatura iniziale t.c. $M_0: P -> N^+$

Definiamo
Il preset $pre(a) = \{d \in (P \cup T) | <d, a> \in F\}$
Il postset $post(a) = \{d \in (P \cup T) | <a, d> \in F\}$

$t \in T$ è abilitata in $M$ SE e SOLO SE $\forall p \in pre(t), M(p) \geq W(<p,t>)$

Lo scatto di una transazione $t$ in una marcatura $M$ produce una nuova marcatura $M'$
Lo scatto di $t$ in $M$ produce $M'$: $M[t>M'$

$\forall p \in pre(t) - post(t)$, $M'(p)=M(p)-W(<p,t>)$
$\forall p \in post(t) - pre(t)$, $M'(p)=M(p)+W(<t,p>)$
$\forall p \in post(t) \cap pre(t)$, $M'(p)=M(p)-W(<p,t>)+W(<p,t>)$
$\forall p \in P - (pre(t) \cup post(t)), M'(p) = M(p)$

ES evoluzione
![[Pasted image 20231212132345.png]]
![[Pasted image 20231212132446.png]]
![[Pasted image 20231212132459.png]]![[Pasted image 20231212132524.png]]

Caso di non determinismo

ES abilitazioni
![[Pasted image 20231212132707.png]]
![[Pasted image 20231212132724.png]]

Regola abilitazioni: $\forall p \in Pre(t), M(p) \geq W(<p,t>)$

Relazione di sequenza
Una transizione $t_1$ è in sequenza con una transizione $t_2$ in una marcatura $M$ SE e SOLO SE
$M[t_1 > \wedge \neg M[t_2 \wedge M[t_1t_2 >$
- $t_1$ è abilitata in $M$
- $t_2$ non è abilitata in $M$
- $t_2$ è abilitata nella marcatura $M'$ prodotta dallo scatto $M[t_1 > M'$

ES sequenza
![[Pasted image 20231212133154.png]]
$T_0$ è in sequenza con $T_1$
$T_0$ è in sequenza con $T_2$
$T_3$ è in sequenza con $T_2$

Relazione di conflitto
Due transizioni $t_1$ e $t_2$ sono in conflitto
- Strutturale SE e SOLO SE $pre(t_1) \cap pre(t_2) \neq \emptyset$
- Effettivo in una marcatura M SE e SOLO SE 
$$M[t_1 > \wedge \text{ }M[t_2 > \wedge\text{ } \exists p \in pre(t_1) \cap pre(t_2),\text{ }M(p) < W(<p, t_1>) + W(<p, t_2>)$$
$t_1$ e $t_2$ sono abilitate in $M$ e esiste un posto $p$ in ingresso a entrambe le transizioni che non ha abbastanza token per farle scattare entrambe

![[Pasted image 20231212154844.png]]

Relazione di concorrenza
Due transizioni $t_1$ e $t_2$ sono in concorrenza
- Strutturale SE e SOLO SE $pre(t_1) \cap pre(t_2) \neq \emptyset$
- Effettiva in una marcatura M SE e SOLO SE
$$M[t_1 > \wedge \text{ }M[t_2 > \wedge\text{ } \forall p \in pre(t_1) \cap pre(t_2),\text{ }M(p) \geq W(<p, t_1>) + W(<p, t_2>)$$
$t_1$ e $t_2$ sono abilitate in $M$ e tutti i posti in ingresso a entrambe le transizioni che hanno abbastanza token per farle scattare entrambe

![[Pasted image 20231212155127.png]]

Insieme di raggiungibilità
L'insieme di raggiungibilità di una rete, a partire da una marcatura $M$, è il piu piccolo insieme di marcature t.c.
$M \in R(P / T, M)$
$(M' \in R(P/T,\text{ }M) \wedge \exists t \in T,\text{ }M'[t > M'') \implies M'' \in R(P/T,\text{ }M)$