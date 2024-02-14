Introduzione
Considerato il tratto biometrico più accurato, tuttavia viene anche percepito come il tratto più invasivo.

Più differenze trovo in un tratto biometrico, più esso è forte.
L'iride presenta numerose caratteristiche stabili nel tempo, di conseguenza è molto forte. Rende una persona riconoscibile negli anni.

Tuttavia creare un sistema di riconoscimento è costoso ma difficile da ingannare

Può essere rilevato tramite sensori più o meno costosi :
- In ambito professionale sono utilizzate i CDD oppure ottiche speciali.

Un sistema di riconoscimento dell'iride possiede una serie di algoritmi che devono :
- Trovare l'occhio nel viso .
- Scattare e confrontare più frame per verificare se l'iride è viva, non sto cercando di frodare il sistema .
- Selezionare la parte utile.
- Eliminare i riflessi e le ciglia .
- Compensare le deformazioni dell'iride le quali possono presentarsi in condizioni di luce differente. Viene tolto tutto quello che non è biometrico.

Identificare l'iride è un operazione molto difficile.

Come agisce un algoritmo di riconoscimento :
- Da una foto del volto si cerca di selezionare solo l'occhio
- Vengono tagliate le palpebre.
- Viene presa la pupilla e il diametro esterno
- Vengono tolte ciglia e riflessi
- L'iride viene selezionata tramite un canale ad infrarossi
- L'immagine rotonda dell'occhio viene stesa rendendola rettangolare.
	A questo punto viene generato l'iris CODE, si va a vedere le differenze di toni di grigio tramite un algoritmo, le quali generano una stringa, generando un pattern dell'iride.

Le lenti ottiche, lenti a contatto, non permettono il riconoscimento dell'iride.

L'iride insieme al volto costituisce un super tratto biometrico. Permette di tracciare una persona nel tempo attraverso una foto. Per questo motivo devono essere opportune leggi sulla privacy.


Perche utilizzare l'iride come tratto di riconoscimento rispetto ad altri ?
- Viene considerato come il tratto biometrico più accurato in assoluto dopo il DNA.
- Oltre ad essere molto accurato, l'iride, presenta delle  numerose caratteristiche molto stabili nel tempo. Inizia a crearsi dal terzo mese nel feto, processo completo al 7 mese ma stabili dal secondo anno in poi.
- Il tratto biometrico corrisponde ad un organi interno, generalmente sempre protetto e presente largamente in tutta la popolazione.
- Tuttavia anche se è il tratto biometrico più accurato è anche quello meno gradito, a causa della sua percepita invasività.
- Sistema piuttosto complesso e costoso ma difficile da frodare. Tutta via esistono sistemi di acquisizione e matching del tratto molto veloce, inoltre l'acquisizione avviene senza contatto.

Svantaggi nell'utilizzo dell'iride come tratto biometrico :
- Difficile acquisire un target in movimento
- L'iride è piatta ma è dietro ad una superfice curva e bagnata la cornea
- Una buona parte dell'iride è nascosta da ciglie e palpebre
- Il pattern dell'iride si deforma elasticamente con la variazione della dimensione della pupilla
- Invecchiando possono apparire delle pigmentazioni non presenti precedentemente
- L'utente deve essere collaborativo e stare esattamente ad una predeterminata distanza dal sensore
- Le immagini possono essere di bassa qualità e provocano errori di "failure to enroll"
- In recenti testi si arriva circa al 7% di scansioni fallite dovute a particolari condizioni dell'iride.

Composizione dell'iride
L'iride è la parte colorata, ovvero la membrana piatta che sta tra la cornea e il cristallino
![[Pasted image 20231115092901.png]]
Controlla il livello di intensità luminosa che deve entrare nell'occhio ( funziona come il diaframma di una macchina fotografica).
Al centro dell'iride è situata la pupilla.

Composizione dell'iride :
L'iride è una membrana ricca di fibre muscolari è in gradi di dilatarsi e contrarsi in modo da variare il diametro della pupilla :
- Il muscolo che contrae è sul bordo della pupilla è agisce quando c'è troppo luce
- I muscoli che dilatano sono radiali dentro l'iride e agiscono quando la luce è troppo flebile.
![[Pasted image 20231115092923.png]]
- Sclera = La parte bianca esterna
- Congiuntiva = La superficie esterna della sclera
- Cornea = struttura trasparente a forma di cupola posizionata nella parte anteriore al centro delle sclera e della congiuntiva.
- Coroide = Tessuto posizionato dietro la sclera, è ricco di vasi sanguinei che riforniscono la retina di ossigeno e sostanze nutritive. Nella parte anteriore la coroide si ispessice formando il corpo ciliare. Nella sezione anteriore del corpo ciliare si diparte un area circolare di fibre muscolari, l'iride.
- Corpo cristallino = situato dietro la pupilla. Si tratta di una lente elastica trasparente, le cui contrazioni muscolari ne permettono l'inspessimento o il restringimento, in modo che l'occhio possa mettere a fuoco oggetti posti a distanze diverse.
- Umore acqueo = lo spazio tra la lente e la cornea è riempito con un liquido

L'iride è una membrana mediamente larga 12 mm e spessa 0.3 mm, inoltre presenta una struttura stratificata :
- Strato epiteliale interno : = ricco di pigmento assume un colore molto scuro e da la tonalità al colore principale dell'iride.
- Stroma = strato ricco di vasi sanguigni che alimentano l'iride di pigmento. Per effetti difrattivi l'occhio prende il colore di questo strato, se contiene invece pochi pigmenti all'esterno si vede il colore dell'epitelio ( occhio scuro o nero)

Esattamente come le impronte digitali, non esistono due iridi uguali.
Durante la formazione dell'iride si hanno delle componenti casuali che produco un pattern di righe, tagli, pieghe ( le feature iridee) assolutamente unico e distinguibile.

Anche i gemelli omozigoti hanno iridi diversi.

Notare inoltre come l'occhio per proteggersi dalla luce sia in grado di chiudersi più velocemente di quanto impieghi per aprirsi. 

[[Iride - Sensori]]

Struttura dei moduli secondo Dougam
![[Pasted image 20231115093102.png]]
[[IRISCODE]]

[[Modulo quality Checker]]
[[Feature Extraction Module]]


[[Iride - Algoritmi di matching]]