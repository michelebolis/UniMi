Vantaggi:
- `Tratto spesso nascosto` (difficile da copiare)
- Non si conoscono attacchi realistici su questo tratto
- Esposto lateralmente e non funzionano i sistemi classici. Solo alcuni algoritmi di face detection capaci di lavorare con volti ruotati possono essere utilizzati.
- Implementabile su molti device
- E’ un tratto che può essere usato con i sistemi multimodali che funziona quando gli altri smettono. L'orecchio si può controllare in situazioni non standard.
Svantaggi :
- `No standard ISO`
- Occlusioni, tuttavia è molto semplice spostare i capelli per avere un area di acquisizione con il 100% dell'area scoperta.
- Non sempre applicabile

Lo studio dell'orecchio è ancora un dibattito oggi:
- Lo studio dell'orecchio (impronte in CSI)
	`Ancora oggi è presente in letteratura il dibattito se questa possa essere una prova impugnabile in tribunale al pari di un impronta o la prova del DNA`.
- I sistemi basati sull'orecchio (immagini 2D) esistono e mostrano tatti di errore EER che vanno dal 6% (anni fa), fino ad alcuni sistemi recenti EER 4%. Tuttavia tale risultati non sono frutto di competizioni indipendenti.
`Le scansioni possono avvenire sia in 2D che in 3D`.
Abbiamo una perfetta separazione tra individui diversi (inter classe), anche per i gemelli

La separazione intraclasse dipende da i seguenti fattori:
- Occlusioni
- Cambio di posa
- Varianza di scala
- Illuminazione
- Rumore
- Bassa risoluzione

Estrazione di feature :
- EIGEN EARS (come autofacce)
- `Distanze dal centro dei punti principali dell'orecchio`, non sempre è automatizzabile
- Confronto fra 2 template, estrazione contorni tramite `Gabor Filter`

`Non esistono comparazioni su larga scala indipendenti per tutti i sistemi commerciali. EER 4% - 6%`

Esempi di sistemi commerciali:
HELIX, si tratta di un sistema biometrico multipiattaforma per l'orecchio. Può essere integrato con la maggior parte delle camera ad oggi esistenti ( smarthpone, videocamere di sorveglianza, webcam, body cam della polizia).

Ad esempio la versione smartphone, sblocca il cellulare utilizzando la telecamera interna del cellulare per scansionare l'orecchio.