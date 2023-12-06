Gli scenari sono descrizioni di come li sistema è usato in pratica
Vantaggi:
Sono utili nella raccolta dei requisiti in quanto semplici da scrivere e possono essere usati anche complementarmente a schede di descrizione dei requisiti

Fasi:
1. Identificazione degli attori
L'attore è un'entità ESTERNA al sistema che interagisce con esso (come fonte o destinatario)
es un utente, un altro sistema, una periferica HW
2. Identificazione degli uses cases
Partendo dalle funzionalità del sistema o partendo dagli attori (chiedendosi cosa fanno o vogliono)
4. Collegamenti tra attori e casi d'uso e tra casi d'uso
	- Tra use cases e attori
		- Uno use case DEVE essere associato ad almeno un attore
		- Un attore deve essere associato ad almeno uno use case
		- Esiste un attore detto `primario` che ha il compito di far partire lo use case
	- Tra use cases
		- include
		- extend
		![[Pasted image 20231206095229.png]]

Generalizzazione:
- Tra attori: permette di esplicitare relazione tra ruoli
- Tra use cases: simile a extends MA sostituisco alcune parti della descrizione mentre eredito le altre