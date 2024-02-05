Due transizioni $t_1$ e $t_2$ sono in `concorrenza`
- `Strutturale` SE e SOLO SE $pre(t_1) \cap pre(t_2) \neq \emptyset$
- `Effettiva` in una marcatura $M$ SE e SOLO SE
$$M[t_1 > \wedge \text{ }M[t_2 > \wedge$$$$ \forall p \in pre(t_1) \cap pre(t_2),\text{ }M(p) \geq W(<p, t_1>) + W(<p, t_2>)$$
$t_1$ e $t_2$ sono abilitate in $M$ e tutti i posti in ingresso a entrambe le transizioni che hanno abbastanza token per farle scattare entrambe

Non esiste alcun legame tra concorrenza strutturale ed effettiva, diversamente da quanto abbiamo visto in precedenza per le relazioni di conflitto

![[Pasted image 20231212155127.png|400]]
