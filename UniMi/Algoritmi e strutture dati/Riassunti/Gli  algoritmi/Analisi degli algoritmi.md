Sintesi di algoritmo: avendo un problema progetto un algoritmo che lo risolva

Analisi degli algoritmi: una volta che ho ottenuto l'algoritmo devo verificare la quantità di risorse utilizzate
- Correttezza: dato un algoritmo A e un problema P, dimostrare che A risolve P
- efficienza: verificare quante risorse utilizza

Come fare l'analisi:
- Faccio girare il programma --> valutazione a posteriori (testing). Limiti: possibili istanza infinite non ho sicurezza sul risultato e non è facile individuare i casi critici. In ogni caso ho un costo di codifica del mio programma
- Valutazione a priori facendo una stima in fase di progettazione. Ci permette di capire la soluzione che appare migliore magari tra una serie di soluzioni possibili.

[[Confronto tra funzioni]]
[[Analisi degli algoritmi - Es]]

$A <- B*C$ //in diversi contesti ho complessità diverse moltiplicazione lineare vs moltiplicazione matrici

Modello di calcolo dipende dall'architettura, influenza le operazioni di base
- Primo modello di calcolo: macchina di Turing
![[Pasted image 20240329094827.png|300]]
- Macchina ad accesso diretto: differenza sta nella memoria ad accesso diretto, se conosco il registro su cui devo leggere il tempo con cui accedo è indifferente rispetto alla sua posizione
![[Pasted image 20240329094843.png|300]]

Istruzioni:
- Di accesso alla memoria: load e store
- Aritmetico-logiche: +, *, -, /
- Confronto: <, >, =, …
- Salto

Queste operazioni assumiamo avere un tempo costante quindi $O(1)$ su tipi di dimensione fissata (primitivi)
Il modello non è realistico per la dimensione illimitate delle celle di memoria e del numero illimitato per il numero di celle di memoria

[[Analisi degli algoritmi - Criteri di costo]]
[[Analisi degli algoritmi - Complessita Introduzione]]
[[Analisi ammortizzata]]