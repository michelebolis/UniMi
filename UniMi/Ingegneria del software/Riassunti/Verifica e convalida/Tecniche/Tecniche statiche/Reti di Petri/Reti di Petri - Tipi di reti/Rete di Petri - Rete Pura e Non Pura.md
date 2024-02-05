Una rete è detta `pura` SE $\forall t \in T, pre(t) \cap post(t) = 0$
SE una rete NON è pura, le regole di abilitazioni comprendono
- $\forall p \in pre(t), M(p) \geq W(<p,t>)$ (già presente)
- $\forall p \in post(t) \backslash pre(t), M(p) + W(<t,p>) \leq K(p)$
- $\forall p \in post(t) \cap pre(t), M(p) + W(<t,p>) - W(<p,t>) \leq K(p)$

![[Pasted image 20240131091238.png|400]]
