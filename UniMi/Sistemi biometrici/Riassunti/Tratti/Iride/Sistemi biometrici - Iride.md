Introduzione
Come agisce un `algoritmo di riconoscimento`:
- Da una foto del volto si cerca di selezionare solo l'occhio
- Vengono tagliate le palpebre.
- Viene presa la pupilla e il diametro esterno
- Vengono tolte ciglia e riflessi
- L'iride viene selezionata tramite un canale ad infrarossi
- L'immagine rotonda dell'occhio viene stesa rendendola rettangolare.
	A questo punto viene generato l'iris CODE, si va a vedere le differenze di toni di grigio tramite un algoritmo, le quali generano una stringa, generando un pattern dell'iride.

Le lenti ottiche, lenti a contatto, non permettono il riconoscimento dell'iride.

L'iride insieme al volto costituisce un super tratto biometrico. Permette di tracciare una persona nel tempo attraverso una foto. Per questo motivo devono essere opportune leggi sulla privacy.


Perche utilizzare l'iride come tratto di riconoscimento rispetto ad altri?
- Viene considerato come il `tratto biometrico più accurato in assoluto dopo il DNA`.
- Oltre ad essere molto accurato, l'iride, presenta delle `numerose caratteristiche molto stabili nel tempo`. Inizia a crearsi dal terzo mese nel feto, processo completo al 7 mese ma stabili dal secondo anno in poi.
- Il tratto biometrico corrisponde ad un organi interno, generalmente sempre protetto e presente largamente in tutta la popolazione.
- Tuttavia anche se è il tratto biometrico più accurato è anche quello `meno gradito`, a causa della sua percepita invasività.
- Sistema piuttosto `complesso e costoso ma difficile da frodare`. Tutta via esistono sistemi di acquisizione e matching del tratto molto veloce, inoltre l'acquisizione avviene senza contatto.

Svantaggi nell'utilizzo dell'iride come tratto biometrico :
- `Difficile acquisire un target in movimento`
- L'iride è piatta ma è dietro ad una superfice curva e bagnata la cornea
- Una buona parte dell'iride è `nascosta da ciglie e palpebre`
- Il pattern dell'iride si `deforma elasticamente con la variazione della dimensione` della pupilla
- Invecchiando possono apparire delle pigmentazioni non presenti precedentemente
- L'utente deve essere collaborativo e stare esattamente ad una predeterminata distanza dal sensore
- `Le immagini possono essere di bassa qualità e provocano errori` di "failure to enroll"
- In recenti testi si arriva circa al 7% di scansioni fallite dovute a particolari condizioni dell'iride.

[[Iride - Composizione]]

Esattamente come le impronte digitali, `non esistono due iridi uguali`.
Durante la formazione dell'iride si hanno delle componenti casuali che produco un pattern di righe, tagli, pieghe ( le feature iridee) assolutamente unico e distinguibile.

`Anche i gemelli omozigoti hanno iridi diversi`.

Notare inoltre come l'occhio per proteggersi dalla luce sia in grado di chiudersi più velocemente di quanto impieghi per aprirsi. 

[[Iride - Sensori]]

Struttura dei moduli secondo Dougam
![[Pasted image 20231115093102.png|400]]
[[IRISCODE]]

[[Modulo quality Checker]]
[[Feature Extraction Module]]

[[Iride - Algoritmi di matching]]
[[Iride - Exploits]]