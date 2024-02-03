Due transizioni $t_1$ e $t_2$ sono in conflitto
- `Strutturale` SE e SOLO SE $pre(t_1) \cap pre(t_2) \neq \emptyset$, quindi hanno `posti in ingresso in comune`
- `Effettivo` in una marcatura M SE e SOLO SE 
$$M[t_1 > \wedge \text{ }M[t_2 > $$$$\exists p \in pre(t_1) \cap pre(t_2),\text{ }M(p) < W(<p, t_1>) + W(<p, t_2>)$$
$t_1$ e $t_2$ sono abilitate in $M$ e esiste un posto $p$ in ingresso a entrambe le transizioni che non ha abbastanza token per farle scattare entrambe

![[Pasted image 20231212154844.png|500]]
