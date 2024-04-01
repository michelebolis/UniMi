Un problema di minimizzazione non lineare è convesso quando
- la funzione obiettivo è una funzione convessa
	- Una funzione è convessa SE e SOLO SE per ogni copia di punti x_1 e x_2 nel suo dominio e per $0 \leq \lambda \leq 1$
		$$f(\lambda x_1+(1-\lambda)x_2) \leq \lambda f(x_1)+(1-\lambda)f(x_2)$$
- la regione ammissibile è un insieme convesso
	-  Un insieme X è convesso SE e SOLO SE per ogni coppia di punti x_1 e x_2, tutte le loro combinazioni convesse appartengono all'insieme
		$$\forall x_1,x_2 \in X, \forall 0 \leq \lambda \leq 1, \lambda x_1 + (1-\lambda)x_2 \in X$$
		es![[Pasted image 20240328165627.png]]

Programmazione convessa
1. La regione ammissibile è convessa SE
	- TUTTI i vincoli di uguaglianza h(x) = 0 sono lineari
	- tutti i vincoli di disuguaglianza, riscritti come $g(x) \leq  0$ sono convessi
2. La funzione obiettivo da minimizzare deve essere convessa
SE entrambe le condizioni  sono soddisfatte, il problema è di programmazione convessa e ciò garantisce che 
- ottimalità locale implica quella globale
- SE esistono piu ottimi, essi formano un insieme convesso