- `Riusabilità` dei componenti. 
	I componenti che costruiamo per il nostro SW potrebbero essere riutilizzati in futuro, risparmiando cosi tempo in futuro, necessitando però di una maggiore adattabilità.
	Alcune volte non sono direttamente riutilizzabili ma devono essere adattati. 
	`McIlroy's Law` riuso riduce il tempo e incrementa la produttività e la qualità.
	Un esempio di fallimento di adattamento è quello del sistema di controllo dell'Ariane 5 che ha causato il fallimento del primo lancio del razzo.
- `Manutenibilità`: si intendono tutte le modifiche apportate ad un SW già rilasciato
	- `Riparabilità`: il SW è riparabile SE i suoi errori sono correggibili con una quantità ragionevole di lavoro
	- `Evolvibilità`: capacita del SW di estendere i propri requisiti. 
		Studi dimostrano che all'aumentare del tempo dalla release, l'Evolvibilità diminuisca.
		`M.Lehman's Laws` un sistema che è usato cambierà, quindi un sistema in evoluzione aumenterà la sua complessità a meno che il lavoro è fatto per ridurne.
	- `Perfettivibilità`: capacità di miglioramento del codice, dal punto di vista interno o esterno, senza cambiarne i requisiti, posso provare a fare cambiamenti volti a migliorare efficienza o usabilità. 