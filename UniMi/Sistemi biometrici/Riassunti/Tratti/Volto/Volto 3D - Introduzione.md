I sistemi biometrici sul volto 3D attualmente disponibili sono in grado di gestire correttamente:
- Acquisizioni frontali
- Con espressione neutra

Altri studi sono attivi per fare riconoscimento a distanza (long-range 3D face recognition).
L'acquisizione 3D di un volto può svolgersi nei seguenti modi:
- `Scanner laser`
	Una lama di luce laser scandisce il volto del soggetto durante una ripresa video.
	Attraverso la geometria spaziale del sistema, si ricostruisce la superfice dalle "fettine" presenti in ogni frame filmato.
	Occhi chiusi
- `Luce strutturata`
	Si illumina il volto da riprendere, con un proiettore in grado di produrre una fascio di luce strutturata ed una/due telecamere.
	
	Con i sistemi code light, si proiettano in successione tanti pattern binari con bande sempre più fini. Il sistema ricostruisce la tridimensionalità usando la deformazione delle bande nell'immagine.
	
	Per aumentare l'area della superficie 3d acquisita si possono usare due tecniche:
	- Si usano due telecamere
	- Si producono due acquisizioni indipendenti "coded light". Ottenute due diverse code light si uniscono per ottenere un'unica superficie 3d.
- `Mediante viste`
	I sistemi chiamati 2,5d, riescono a riprodurre la superficie 3d del volto da tane immagini del volto prese da angoli diversi, usando una normale telecamera.
	Con un passaggio successivo, altri sistemi riescono a ricostruire un vero modello 3D del volto partendo dalle immagini 5D.
	
	N.B = i face modeler che applicano la faccia 2D su un modello 3D standard uguale per tutti non possono essere utilizzati per scopi biometrici. Ecco perché costano poco.
	Vengono utilizzati nel campo del 3D per prove e scelta di accessori.


Vantaggi del 3d :
- `Invarianza alla luce e all'ambiente` (usano luce IR propria), posa e makeup
- Sono maggiormente tolleranti rispetto a colori di sfondo, accessori, trucco del viso
- Invarianti rispetto a piccoli spostamenti angolari del volto
- La precisione di alcuni sistemi permette di distinguere due gemelli omozigoti.
- Capacità `realtime`
- `Bassi valori di FRR` ( false reject rate), anche se il false match rate è molto basso
- Dislocazione del sensore : Esistono in commercio dei sensori base di dimensioni ridotte che possono essere alloggiati in ogni situazione, muro, porta/cancello, sensore portatile.

Svantaggi del 3D:
- Costo dei sensori e dei sistemi maggiori
- Il soggetto deve essere collaborativo

Esempi di sistemi in commercio :
- RealSense D435 camera
Riconoscimento biometrico : 3D, colore, punti fiduciari.
Permette il riconoscimento delle emozioni e delle espressioni ( ottenuto combinando  il sensore con librerie come openCV).
- Face id di apple
- Macchina vision 3D + 2D ICAO
Si tratta di un sistema usato per enrollment, verification e identification di immagini facciali 3D e 2D.
Il sensore acquisisce simultaneamente il 3D e il 2D rispettando le specifiche ISO.