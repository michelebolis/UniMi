`Input` (dati che cambiano): $A$, $b$, $c$
con 
- $A$ matrice dei coefficienti dei vincoli
- $b$ termini noti
- $c$ coefficienti della funzione obiettivo

`Output`: $B^*$, $x^*$, $z^*$
con
- $B^*$ la base ottima
- $x^*$ il valore delle variabili
- $z^*$ la soluzione ottima

Scopo: valutare l'intervallo nel quale può variare ogni coefficiente $c_j$ e $b_i$ SENZA che cambi la base ottima $B^*$
La base rimane ottima finche valgono le condizioni di ammissibilità e di ottimalità
- `Ammissibilità`: $x_B = B^{-1}b \geq 0$
- `Ottimalità`: $\bar{c}_N = c_N - c_BB^{-1}N \geq 0$

Le condizioni di ammissibilità dipendono solo da $b$
Le condizioni di ottimalità dipendono solo da $c$

- [[Analisi di sensitività - Variazione di un coefficiente c]]
- [[Analisi di sensitività - Variazione di un coefficiente b]]