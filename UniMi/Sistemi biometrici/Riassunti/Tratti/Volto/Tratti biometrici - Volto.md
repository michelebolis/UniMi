Introduzione
Si tratta del tratto biometrico meno intrusivo.
Viene utilizzato oggi nella normalità (face id per sbloccare il cellulare), dalle persone per riconoscersi, è molto apprezzato dagli utenti. Per  i seguenti motivi è molto diffuso.

`Il volto non è uno tra i tratti biometrici più performanti`
Il riconoscimento del volto avviene attraverso due approcci :
- `Trasformazione/EIGENFACES` : si crea una `base di immagini chiamate auto-facce`, che permette di `ricostruire un nuovo viso come una somma di immagini` contenute nella base.
	`Non si effettua mai un confronto volto a volto` per le differenze elencate nel punto sopra.

- `Attributi`: Si localizza il volto nell'immagine e si `misurano delle caratteristiche` come la distanza fra gli occhi, la lunghezza del naso, ecc.. Vengono misurati tratti salienti del viso.
	`È possibile distinguere dei gemelli omozigote con il riconoscimento del volto`. Ci sono delle variazioni del comportamento rilevate tramite delle reti neurali.


Il tratto biometrico del volto viene `impiegato sia per la verifica che per l'identificazione`, ma non solo. 
Molti degli algoritmi non servono solo per produrre sistemi biometrici, ma anche per:
- Riconoscimento facciale delle espressioni
- Riconoscimento del movimento delle labbra (anche per multimodalità e controllo anti-spofing)
- Applicazioni di computer grafica
- Creazioni di protesi

Quindi uso non solo `biometrics ma anche biometry`.

`Passive biometrics identification`: Normale telecamere da video sorveglianza + Surv-tool + face tracking + identification.

Vantaggi :
- Ottimo `compromesso fra accettabilità da parte dell'utente e prestazioni in accuratezza`.
- Dispositivi di Input facilmente posizionabili ed adatti a molte condizioni operative.
- Risultati direttamente verificabili da un operatore umano
- Permette l'`acquisizione non conseziente` (video-sorveglianza)

Svantaggi :
- `Alta variabilità intraclasse`
	- Un importante competizione indipendente fra algoritmi di FC (face recognition) ha evidenziato il `fortissimo impatto delle differenze di illuminazione e posa sulle performance`
	- Occlusioni
	- Sensori
	- `Variazioni dell'aspetto dell'individuo` (invecchiamento).  Le variazioni si verificano se consideriamo volti a distanza di decenni, se invece consideriamo un periodo di tempo limitato ( paio di anni) le variazioni sono limitate.
	- `Similitudini intraclasse per il volto`:
		- Gemelli
		- Fratelli, genitori ( enrollati distanti nel tempo)
		- Sosia: Il DNA contribuisce al 50%, tutta via questo non aiuta, aiuta invece la differenza di età, favorisce la distinzione.
- Possibile ingannare i sensori non dotati di meccanismi di anti-spofing
- Solo recentemente le accuratezze sono diventate interessanti per sistemi su larga scala.
- Tecnologia matura per i sensori, ma non per gli algoritmi che sono in continua evoluzione.

Fasi Principali, la catena di enroll/verifica o identificazione di solito consiste nei seguenti passaggi:
- `Face Detection` (trovare i volti nelle immagini)
- `Face segmentation` (separare il volto dallo sfondo)
- `Face tracking` (se in un video deve essere inseguito)
- `Face normalization` (crop e normalizzazione della immagine)
- `Feature extraction` (grafi, segmenti)
- `Matching`

Le tecniche di `deeplearning` (Convolutinal neural networks), hanno permesso ulteriori passi avanti nelle fasi di:
- Identificazione dei volti (anche in ambianti non controllati)
- Segmentazione del volto
- Matching

Oggi inoltre trovare un sosia è più facile che mai (attraverso i social)
Nel 2022 si sono analizzati i valori di score di 32 coppie di sosia trovate da Brunelle con 3 FR (Face recognition) in commercio :
![[Pasted image 20231115094037.png|300]]

[[Volto - Template standard]]


`VeriLook SDK`
Si tratta di un applicazione stand-alone di face recognition. Utilizzata principalmente in applicazioni web (come modulo).

Permette una `identificazione di tipo live-detection`, non solo di una faccia ma anche di facce multiple. Presenta una buona accuratezza e una velocità di matching (40.000 volti al secondo) molto alta sia in verifica ( 1:1) che in identificazione (1;N).

Inoltre i template delle facce, pesano solamente dai 4 ai 7 KB.
Permette inoltre:
- Riconoscimento delle emozioni
- Stima di età
- Tolleranza alla posizione della faccia

Dato che si tratta di un applicazione stand-alone, permette un `alta portabilità tra i vari sistemi operativi` (utilizzata in più di 1 milione di applicazioni)

La classificazione del volto è divisa in due categorie :
- [[Volto 2D]]
	- Immagine fissa
	- Video o tante immagini fisse
	- Colori
	- Toni di grigio
- [[Volto 3D]]
	- Scansione laser
	- Illuminazione controllata

[[Volto 2D vs 3D]]

[[Volto - Facial Fingerprinting]]