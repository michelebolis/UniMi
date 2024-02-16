Riconoscimento della voce
Dividiamo lo studio della voce in due principali categorie :
- `Speech Recognition`: riconoscere `ciò che viene detto` (frasi, numeri, testi)
- `Speaker recognition`: riconoscere l'`identità` della persona che sta parlando.
- Si tratta di un `tratto biometrico ibrido tra biometria fisiologica e comportamentale`. Il tratto vocale viene composto dalla seguenti parti :
	- Parte fisiologica: pulsazioni glottali
	- Parte fisiologica/comportamentale: tratto della bocca.
- Il segnale audio deve soddisfare le seguenti caratteristiche:
	- Frequenza con una risposta di +/- 4 decibel nel range da 100 hz a 8hz
	- Rumore in sottofondo fino ad un massimo di 18.20 db
	- Sample rare raccomandato 11025 kHZ
	- `50KB - 100KB: dimensione sample`

Fino ad oggi il riconoscimento vocale avviene in 3 `modalità`:
- `Auditivo` (un esperto ascolta le tracce)
- `Semiautomatico` (un esperto controlla delle feature estratte dalla voce di due persone, ad esempio spettogrammi)
- `Riconoscimento completamente automatico`