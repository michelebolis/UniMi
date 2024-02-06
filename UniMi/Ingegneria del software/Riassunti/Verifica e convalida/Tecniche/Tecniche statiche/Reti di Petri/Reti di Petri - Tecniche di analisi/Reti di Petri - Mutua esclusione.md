Problema: accesso esclusivo ad una zona critica contesa tra piu soggetti
es non si possono avere in contemporanea gettoni in $P_1$ e in $P_3$
![[Pasted image 20240206090112.png|400]]

quindi matematicamente $P_1 + P_3 \leq 1$
La tecnica del `controllore a stati proibiti` aggiunge tanti posti di controllo quanti sono il numero di disequazioni
Quindi nel nostro esempio, $P_1 + P_3 + P_C = 1$

Per collegare $P_C$ alle diverse transizioni, aggiungiamo una riga, $C_C$, nella matrice di incidenza e la marcatura iniziale $M_{0C}$ alla marcatura iniziale del sistema $M_{0S}$
$$LM_S+M_C=b$$
Sia $[LI]$ la giustapposizione tra $L$ e la matrice identità $I$ e $M$ la giustapposizione di $M_S$ e $M_C$, allora
$$[LI]M = b$$
Ricordando la definizione di P-invariante, $hm=0$, forzando che $[LI]$ sia un'invariante
$$[LI]C = 0$$
$$LC_S+IC_S=0$$
$$C=-LC_S$$
Le righe da aggiungere al sistema $C_C$ sono quindi uguali a $-LC_S$ con 
- $C_S$ matrice di incidenza del sistema originario
- $L$ il vincolo fissato
- $C_C$ ottenibile con un calcolo matriciale