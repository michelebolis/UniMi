1. `Creazione e distruzione dei gettoni`

Distruggere i gettoni e i relativi simboli nel preset e generare i nuovi gettoni nel postset, identificati tutti dallo stesso nuovo identificatore simbolico

2. `Espansione dei vincoli`
Lo scatto simbolico di una transizione $t$ crea uno stato simbolico caratterizzato dal vincolo $C_n$
$$C_n = C_p \wedge t_n \geq maxT \wedge t_n \geq tmin \wedge t_n \leq tmax$$
$$\bigcap_{t_s} (tmax_s < tmin_s \vee tmax_s < maxT \vee tmax_s \geq t_n)$$
Significato:
- i vecchi vincoli devono continuare a valere ($C_P$)
- il nuovo timestamp deve avere il valore massimo nella rete per monotonicità del tempo ($t_n\geq maxT$)
- il nuovo timestamp deve essere compreso nell'intervallo dei possibili tempi di scatto della transizione ($t_n \geq tmin \wedge t_n \leq tmax$)
- il nuovo timestamp deve essere minore del massimo tempo di scatto di tutte le transizioni forti abilitate il cui intervallo di scatto in sia nullo 


![[Pasted image 20240131152442.png|600]]

![[Pasted image 20240131152515.png|600]]
