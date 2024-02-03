Una possibile estensione delle reti di Petri consiste nel fissare un `massimo numero di token` ammissibili in un posto, `forzando cosi la limitatezza`
$t \in T$ è abilitata in $M$ SE e SOLO SE
- $\forall p \in pre(t), M(p) \geq W(<p,t>)$
- $\forall p \in post(t), M(p) + W(<t, p>) \leq K(p)$

[[Reti di Petri - Posto complementare]]