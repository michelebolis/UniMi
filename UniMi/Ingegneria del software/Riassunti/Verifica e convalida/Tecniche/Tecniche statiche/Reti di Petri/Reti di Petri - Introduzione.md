Le reti di Petri pascono per descrivere sistemi concorrenti

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

Regola abilitazioni: $\forall p \in pre(t), M(p) \geq W(<p,t>)$

[[Reti di Petri - Esempio]]

[[Reti di Petri - Relazioni]]
[[Rete di Petri - Tipi di reti]]

Definiamo poi:
- [[Reti di Petri - Insieme di raggiungibilità|Insieme di raggiungibilità]]
- [[Reti di Petri - Archi inibitori|Archi inibitori]]
- [[Reti di Petri - Rappresentazione matriciale]]

[[Reti di Petri - Variazioni]]
[[Reti di Petri - Tecniche di analisi]]
[[Reti di Petri Temporizzate - Introduzione]]