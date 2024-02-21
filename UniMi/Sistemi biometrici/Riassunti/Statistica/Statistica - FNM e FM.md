Supponiamo di poter variare la soglia s del sistema e fissarla ad un `valore T in mezzo fra il picco degli impostori e quello dei genuini`.
![[Pasted image 20231106100430.png]]
- Possiamo notare che `un certo gruppo di persone dei genuini non sarà riconosciuto dal sistema`, in quanto sono sotto alla soglia prestabilità. Daranno quindi luogo ad errori di `False Non Matching - FNM`.
	`False not matching raiting` con soglia T -> $FNMR(T) = FNM(T) / totale genuini$
	
	Il numero totale di persone appartenente al gruppo dei genuini (sotto la soglia T) FNR, deve essere calcolato con un integrale della porzione di curva dei genuini fino alla soglia T
- Al contrario `parte degli impostori saranno riconosciuti dal sistema`, in quanto hanno un valore di matching sopra la soglia. Daranno vita ad errori di `False Match - FM`
	`False matching raiting` con soglia T -> $FMR(T) = FM(T) / totale impostori$

Il funzionamento di un sistema biometrico dal punto di vista degli errori commessi è principalmente descritto dai `tassi FMR(T) e FNMR(T)` descritti per tutti i valori della soglia.  Tali valori inoltre sono in funzione della soglia scelta T.

L'andamento del sistema può essere descritto dalla `funzione DET` (Decision Error Tradeoff), mostra come variano i valori di FNMR (y)  e FMR (x) al variare del parametro T.  Esprime `quanti genuini non sono riusciti ad entrare nel sistema`.
La curva Det non rappresenta nessuna distribuzione.