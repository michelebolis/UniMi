Fasi:
1. `Identificazione degli attori`
L'attore è un'entità ESTERNA al sistema che interagisce con esso (come fonte o destinatario)
es un utente, un altro sistema, una periferica HW (ruoli NON persone, )
2. `Identificazione degli uses cases`: partendo dalle funzionalità del sistema o partendo dagli attori (chiedendosi cosa fanno o vogliono)
3. Associazioni tra attori e casi d'uso e tra casi d'uso
	- `Convenzioni`:
		- Ogni attore DEVE almeno avere un'interazione con un caso d'uso (altrimenti sarebbe impossibilitato a interagire col sistema)
		- Ogni caso d'uso deve essere associato ad almeno un attore 
	- Associazione tra use cases
		- `Inclusione` (include): chi include conosce gli inclusi ma non viceversa. Usata per fattorizzare
		- `Estensione` (extend): per rappresentare casi eccezionali
		![[Pasted image 20231206095229.png|300]]
4. `Generalizzazione`:
	- Tra attori: permette di esplicitare relazione tra ruoli
	- Tra use cases: simile a extends MA sostituisco alcune parti della descrizione mentre eredito le altre (NO secondo principio di Liskov, infatti è deprecata in UML 2)