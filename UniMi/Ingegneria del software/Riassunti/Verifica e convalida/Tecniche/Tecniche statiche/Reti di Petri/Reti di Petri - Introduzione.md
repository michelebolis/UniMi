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

Relazioni: sequenza
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

Relazioni: conflitto