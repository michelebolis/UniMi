P-invarianti sono invarianti sui posti, delle caratteristiche sulle marcature
Un vettore $h$ di dimensione |P| è un P-invariante SE e SOLO SE 
$$\forall m' \in R(P/T, m), hm=hm'$$
$hC = 0$ si passa da una proprietà dinamica a una tecnica di analisi statica che trova un sottoinsieme dei P-invarianti
DIM
$hm = hm'$
OSS dato che $m'$ è raggiungibile da $m$, allora esiste una sequenza s t.c. $m+C_S  = m'$
$hm = h(m+C_S)$ 
$hm = hm + hC_S$
$hC_S= 0$
$hC=0$

Copertura di P-invarianti
Una combinazione lineare di P-invarianti è un P-invariante
$h_1, h_2$ P-invarianti => $\forall \alpha, \beta \in R, \alpha h_1+\beta h_2$ è un P-invariante
Un P-invariante che ha tutti i pesi >= 0, è detta `P-invariante semi-positivo`
SE un posto ha un peso positivo in un P-invariante semi-positivo, allora quel posto è `limitato`

Una rete di Petri si dice copribile/ricopribile da P-invarianti SE per ogni posto esiste almeno un P-invariante semi-positivo in quel posto
Esisterà una combinazione lineare di P-invarianti che copre ogni posto quindi la rete è conservativa rispetto a questi pesi, quindi limitata

Esempio
![[Pasted image 20240131104947.png|500]]
