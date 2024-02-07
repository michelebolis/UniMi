La semantica forte o debole viene associata alle singole transizioni invece che all'intera rete
- Le transizioni forti devono scattare entro il loro tempo massimo a meno che non vengano disabilitate prima
- Le transizioni deboli possono scattare entro il loro insieme di tempi di scatto

Con $W$ indico le transizioni deboli mentre tutte le altre sono considerate forti

Esempio analisi
![[Pasted image 20240131145913.png|500]]

Considerando tutte le transizioni come deboli, otterrei un diagramma temporale 
![[Pasted image 20240206100646.png|400]]
Ma la presenza di transizioni forti non ci permette di dire nulla dopo un certo tempo in quanto lo scatto di una transizione potrebbe disabilitarne altre
Le transizioni forti bloccano il nostro orizzonte temporale
![[Pasted image 20240206100807.png|400]]