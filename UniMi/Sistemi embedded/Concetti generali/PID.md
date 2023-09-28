E' un modello di controllo e per PID si intende Proporzionale-Integrativa-Derivativa ovvero:

* **Proporzionale**: la distanza assoluta dallo stato desiderato utilizzando lo stato attuale per valutare quanto sia distante dall'obiettivo.
* **Integrativa**: la storia dell'evoluzione dello stato del sistema calcolata in una finestra temporale (es media dell'errore).
* **Derivativa**: la velocità di variazione dello stato dall'obiettivo.

Una volta calcolati i valori vanno stabiliti dei coefficienti per pesare la funzione P*(distanza) + I*(media errore) + D*(velocità variazione - può corrispondere alla distanza). È importate avere una funzione che definisca l'errore. Nel caso del motore e(t)= RegimeDesiderato - GiriMotore
esempio:
Ipotizzando che vogliamo un motore che vada ad un regime di 1400 giri

Istante Regime Errore
 t-3:  1170 230
 t-2:  1200 200
 t-1:  1250 150
  t:  1300 100

P: (1400 - 1300) = 100
I: (230 + 200 + 150 + 100)/4 = 170
D: (1400 - 1300) = 100
pesando P=I=D=0.5 otteniamo 0.5*100 + 0.5*170 + 0.5*100 = 50+85+50 = 185

Potremmo usare 185 come valore da aggiungere alla tensione data al motore. Dovremmo calcolaro cosa accadrebbe ora al tempo t+1 dopo la modifica e nel caso aggiustate i pesi attribuiti a P,I,D.
Se mal calcolata si richierebbe di non raggiungere mai l'obiettivo (se correzione troppo debole) o oscillare intorno l'obiettivo (se correzione troppo forte).