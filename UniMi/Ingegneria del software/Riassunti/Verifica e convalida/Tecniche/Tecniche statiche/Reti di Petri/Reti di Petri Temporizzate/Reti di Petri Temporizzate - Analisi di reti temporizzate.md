Analisi di raggiungibilità: enumerazione degli stati finiti raggiungibili
Problemi: 
- lo scatto di una transizione puo produrre infiniti stati che si differenziano tra loro per il tempo associato ai gettoni prodotti 
- la rete puo evolvere all'infinito

Non si può usare l'albero di copertura come nelle reti limitate

Nelle reti TB si attua una rappresentazione simbolica degli stati
Uno stato simbolico rappresenta un insieme di possibili stati con in comune lo stesso numero di gettoni in ogni posto/marcatura
Uno stato simbolico è una coppia $[\mu, C]$ dove
- $\mu$ è la marcatura simbolica che associa un multiset di identificatori simbolici ai posti
- C sono i vincoli, disequazioni che rappresentano le relazioni tra gli identificatori simbolici

Assumiamo che $tf_t$ sia un intervallo con estremi inclusi esprimibili mediante espressioni lineari funzioni dei tempi dei token in ingresso e di tempi assoluto
Con tmin_t il limite inferiore e tmax_t il limite superiore,
$$tf_t = \{X | X \geq tmin_t \wedge X \leq tmax_t\}$$
Esempio
![[Pasted image 20240131151610.png|600]]

![[Pasted image 20240131151651.png|500]]

Aggiornamento del constraint
Lo scatto simbolico di una transizione $t$ crea uno stato simbolico caratterizzato dal vincolo $C_n$
$$C_n = C_p \wedge t_n \geq maxT \wedge t_n \geq tmin \wedge t_n \leq tmax$$
$$\bigcap_{t_s} (tmax_s < tmin_s \vee tmax_s < maxT \vee tmax_s \geq t_n)$$

![[Pasted image 20240131152442.png|600]]

![[Pasted image 20240131152515.png|600]]

Non abbiamo una forma normale, quindi non possiamo confrontare stati per capire se li abbiamo gia visitati
Possiamo verificare proprieta entro un limite finito di tempo: bounded invariance e bounded liveness