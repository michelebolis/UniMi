Introduzione
Di solito si lavora su tre viste:
- Palmare
- Dorsale
- Laterale

Approcci per il riconoscimento :
- Misura delle lunghezze
- Confronto delle immagini e delle parti
- Studio delle linee

Caratteristiche del tratto biometrico :
- Tratto biometrico moto ben accettato dagli utenti perché `poco invasivo`
- Presente fin dal 1979 sul mercato (tecnologia matura)
- Offre un `discreto livello di accuratezza`, senza dover chiedere all'utente sample molto critici perla privacy come l'iride o l'impronta.
- Offre la possibilità di `funzionare in modo multimodale`, controllando più aspetti come immagini, misure, pattern delle vene.
- Diffusione sul mercato buona :
	- Impronte (44%)
	- Face (19%)
	- Geometria della mano(9%)
	- Iride(7)
	- Voce(4)
	- Firma(2)
	- Multimodali(4)
- `L'utente deve essere collaborativo`
- Dalla mano sono estraibili circa `90 features`:
	- Misura delle lunghezze degli elementi
	- Confronto delle immagini
	- Immagine termica per pattern vene
	- Studio delle linee della pelle

Sono `sistemi veloci`, adatti per essere affiancati a tornelli, porte e cancelli. Vengono utilizzati principalmente per il controllo degli accessi.
Sono sistemi impiegati anche per applicazioni del tipo "`time and attandance`" cioè per il controllo delle presenze sui luoghi di lavoro.

La geometria della mano è il tratto biometrico preferito dal garante della privacy.
Vantaggi:
- Tecnologia consolidata
- `Sensore robusto`
- `Dimensioni del template molto ridotte`
- Minore impatto sulla privacy degli utenti
Svantaggi :
- Costo circa sui 1000 dollari
- Dimensione e peso notevoli
- Sensibilità a forte luce diurna

[[Mano - Sensori]]
[[Mano - Matching]]


Riconoscimento del palmo
![[Pasted image 20240214092622.png|300]]

`Touch-Based` system:
- Maggiore accuratezza
- Si lasciano impronte sul device
- Compatibili con classici sistemi di impronte
- Minore usabilità
`Touchless`:
- Minore o uguale accuratezza
- Non si lasciano impronte sul device
- Maggiore usabilità
- Parziale compatibilità con i sistemi classici.

Si tratta di sistemi biometrici che lavorano sul palmo della mano, hanno un `raggio d'azione che parte dall'inzio del polso e arriva fino alle dita`. Diverse feature estraibili con diversa risoluzione:
- Feature geometriche
- Linee principali
- Delta points
- Minutiae
- Level3 features

| Risoluzione | Livello feauture estraibili | Descrizione |
| ---- | ---- | ---- |
| 300 | Livello 1 | Linee del palmo |
| 500 | Livello 2 | Minutiae |
| 1000 | Livello 3 | Pori |

`Tra 300-500 dpi è la tipica zona d'azione del palm ricognition`.

`I moduli di matching sono ad HOC in base alle features estratte vanno da semplici metriche euclidee fino a funzioni complesse con deep learning`.

![[Pasted image 20240214092720.png|400]]

[[Palmo 2D]]
[[Palmo 3D]]