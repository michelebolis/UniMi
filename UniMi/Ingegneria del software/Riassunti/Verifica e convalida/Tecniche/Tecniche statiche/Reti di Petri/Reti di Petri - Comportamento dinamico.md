$t \in T$ è abilitata in una marcatura $M$ SE e SOLO SE $\forall p \in pre(t), M(p) \geq W(<p,t>)$

Per ogni elemento collegato in ingresso a $t$ esiste un numero di gettoni maggiore del peso dell’arco che collega $p$ a $t$
`Località dell'analisi`: non si sta quindi ragionando su tutti i posti della rete, ma solo su quelli collegati in ingresso a $t$

Lo scatto di una transazione $t$ in una marcatura $M$ produce una nuova marcatura $M'$
Lo scatto di $t$ in $M$ produce $M'$: $M[t>M'$ t.c.:
- Per ogni identificatore $p$ appartenente al `preset ma non al postset` della transizione $t$, il numero di gettoni della nuova marcatura $M′$ sarà uguale al numero di gettoni della marcatura precedente $M$ meno il peso dell’arco che collega $p$ a $t$
$$\forall p \in pre(t) \backslash post(t) \text{, } M'(p)=M(p)-W(<p,t>)$$
- Per ogni identificatore $p$ appartenente al `postset ma non al preset` della transizione $t$, il numero di gettoni della nuova marcatura $M′$ sarà uguale al numero di gettoni della marcatura precedente $M$ più il peso dell’arco che collega $t$ a $p$
$$\forall p \in post(t) \backslash pre(t)\text{, } M'(p)=M(p)+W(<t,p>)$$
- Per ogni identificatore $p$ appartenente `sia al preset sia al postset` della transizione $t$, il numero di gettoni della nuova marcatura $M′$ sarà uguale al numero di gettoni della marcatura precedente $M$ meno il peso dell’arco che collega $p$ a $t$ più il peso dell’arco che collega $t$ a $p$;
$$\forall p \in post(t) \cap pre(t)\text{, } M'(p)=M(p)-W(<p,t>)+W(<t,p>)$$
- Per ogni identificatore $p$ appartenente all’`insieme dei posti meno l’unione tra preset e postset` di $p$ la marcatura non cambia.
$$\forall p \in P - (pre(t) \cup post(t)), M'(p) = M(p)$$

Regola abilitazioni: $\forall p \in pre(t), M(p) \geq W(<p,t>)$
