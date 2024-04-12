Il dominio di P è l'algebra di eventi $A$ (in corsivo)

$P : A --> R^+$
- $A = { E_1, E_2, … }$
- $\forall i, E_i \subseteq \Omega$
- $A$ puo essere finito o infinito
	- SE $\Omega$ finito, $A$ sarà finito

Proprieta su $A$
- $\Omega \in A$
- Chiusura rispetto al complemento: $\forall E, \text{ SE } E \in A --> \overline E \in A$
- Chiusura rispetto all'unione: $\forall E, F, \text{ SE } E \in A \wedge F \in A --> (E \cup F) \in A$
	- Chiusura dell'intersezione gia implicata grazie alle leggi di de morgan e alle due proprieta precedenti
		$A \cap B= \overline{\overline{((A \cap B)}} = \overline{\overline{(\overline A \cup \overline B)}}$

Da una parte verrebbe da mettere in A il piu possibile MA meno cose metto meglio è perche sarà piu facile associare le probabilita

SE $\Omega$ è finito, $|\Omega|=n$ ALLORA $A = 2^\Omega$ è l'insieme delle parti di omega
DIM
SE $\Omega$ finito, posso scriverlo in modo estensivo $\Omega= {e_1, …, e_n}$;
Prendendo un qualsiasi sottoinsieme di $\Omega$, $\forall E \subseteq \Omega$ quindi $E \in 2^\Omega$, $E$ sarà finito $e_{i1}, …, e_{ik} = \{e_{i1}\} \cup … \cup \{e_{ik}\}$
SE ogni evento singoletto $\in A$, allora $E \in A$ per la terza proprieta. Ragionevole tale ipotesi perche voglio calcolare la probabilita degli eventi dati da un solo esito

Si chiama algebra perche è definita in termini algebrici, in termini delle proprieta che possiede