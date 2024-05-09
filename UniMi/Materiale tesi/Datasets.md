- Pole Dataset [https://github.com/neo4j-graph-examples/pole/tree/main]
- Patients 1k edition [https://synthea.mitre.org/downloads]
	- buono per il funzionamento del modello health su description
- Tweet [https://github.com/neo4j-graph-examples/twitter-v2]
	- buono per il funzionamento del modello identification su text (del tweet)
- Tweet trolls [https://github.com/neo4j-graph-examples/twitter-trolls]
	- NON va bene perchè ha tweet in russo/tedesco

Modelli NER Medical
- Custom
![[Pasted image 20240506101043.png]]
- MedSpacy https://github.com/medspacy/medspacy (currently in BETA)
- med7 [https://github.com/kormilitzin/med7?tab=readme-ov-file] (only drugs) ALL FalsePositive
![[Pasted image 20240506105509.png]]
- scispacy https://github.com/allenai/scispacy
![[Pasted image 20240507093711.png]]

es
![[Pasted image 20240507093431.png]]

usando un faker non sto rilevando che è una cosa sensibile ma mettendo un * si, sono protetto a livello di inferenze 
inserisco cover stories
Soppressione con * anche quando rilevo come keyword
parlare di generalizzaione anche con gerarchie (citarlo va bene anche se non implementato)

perche non faccio la ner anche sui valori delle keyword pericolose? spreco di tempo tanto ho gia una conoscenza di base del contesto data dalle keyword
separazione contesti sanitizzazione ner o con keyword

