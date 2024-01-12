L'algoritmo del simplesso non da garanzia di terminare in un numero di iterazioni limitato da un polinomio MA è molto veloce 

L'algoritmo garantisce di terminare in un numero finito di passi, garantendo una di queste tre situazioni
- la soluzione corrente è ottima
- NON esiste una soluzione ammissibile
- NON esiste soluzione ottima finita

L'algoritmo del simplesso procede iterativamente da una soluzione di base ad una adiacente

Una volta posto in [[Forma canonica]] un problema di PL si puo rappresentare in una matrice, tableau.
E' una struttura dati fondamentale sulla quale opera l'algoritmo del simplesso

[[Pseudocodice algoritmo del simplesso]]

Router non convenzionale (MPLS) differenze:
- le informazioni di routing popolano anche la Label switching table
- l'IP header e l'IP payload vengono trasformati in un MPLS pacchetto. Questo avviene tramite [[Tunneling]], incapsulando quindi il pacchetto IP
- labeling: assegnamento della label al pacchetto
- Gestisco le code in base all'etichetta

Il ruoter ragiona solo in base alla porta di ingresso - etichettaRilevata - etichettaNuova - porta di uscita. Ci sarà una tabella per ogni porta

![[Pasted image 20231219131850.png|400]]
