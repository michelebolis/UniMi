Una transizione può scattare solo in uno degli istanti identificati dalla sua funzione temporale
Una transizione non può scattare prima di essere stata abilitata
Una transizione DEVE scattare ad un suo possibile tempo di scatto a meno che non venga abilitata prima del proprio massimo tempo di scatto ammissibile

E' la semantica piu diffusa, utile per i sistemi deterministici tanto che è di defaultin molti modelli temporizzati (TPNs)

Una transizione abilitata DEVE scattare entro il suo massimo tempo di scatto, se non viene disabilitata prima da un altro scatto
Le sequenze di scatto che soddisfano gli assiomi 1, 2, 3, 4 e 5 sono dette sequenze ammissibili in semantica forte STS

Esempio
![[Pasted image 20240131144847.png|500]]
