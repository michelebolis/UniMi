Router non convenzionale (MPLS) differenze:
- le informazioni di routing popolano anche la Label switching table
- l'IP header e l'IP payload vengono trasformati in un MPLS pacchetto. Questo avviene tramite [[tunneling]], incapsulando quindi il pacchetto IP
- labeling: assegnamento della label al pacchetto
- Gestisco le code in base all'etichetta

Il ruoter ragiona solo in base alla porta di ingresso - etichettaRilevata - etichettaNuova - porta di uscita. Ci sarà una tabella per ogni porta

![[Pasted image 20231219131850.png|400]]
