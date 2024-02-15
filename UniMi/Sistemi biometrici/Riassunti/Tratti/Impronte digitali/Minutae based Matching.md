Minutae based Matching
Minutae base tecniche, per prima cosa vanno a trovare le coordinate dei minutae points  ( biforcazioni e terminazioni dei ridge) nelle due impronte, permettendo così di comparale. Per effettuare una corretta comparazione dei minutiae points occore eseguire le seguenti operazioni preliminari :
- Allineamento delle rotazioni
- Allineamento della scala
- Allineamento delle traslazioni
- Riduzione della distorsione elastica
![[Pasted image 20231106105555.png|400]]

Il problema del matching delle impronte è sostanzialmente un problema di point pattern matching.
Verranno dunque comparati due set di punti ( minutae), un set proveniente dal sample della impronta in input, l'altro set dal template presente sul db.

I punti minutiae possono essere rappresentati in una matrice :
$M = (m_1, m_2, ..., m_n)^T$

Dove ogni $m_i$, è il seguente set di valori
$m_i = (X, Y, \phi, T_i)$
- X e T sono le coordinate dell'i-esimo punto minutae
- $\phi$ è l'angolo di orientamento
-  T è invece il tipo di minutiae ( biforcazione o terminazione di un ridge)

Vantaggi di questa tecnica :
- Invariante alle traslazioni, rotazioni e cambiamento di scala dell'immagine
- Molto accurato

Svantaggi di questa tecnica :
- L'estrazione delle minutiae richiede dei sample ad alta qualità
- Non robusto alle trasformazioni non -lineari ( deformazioni)
- Non utilizza informazioni riguardante l'analisi globale dell'impronta ( texture, ecc..)