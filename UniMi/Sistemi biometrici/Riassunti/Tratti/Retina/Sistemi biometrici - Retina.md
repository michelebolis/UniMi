`Riconoscimento` della retina
- `Pattern dei vasi` presenti sulla retina. La tessitura delle vene sulla retina è già completa al momento della nascita e rimane quasi completamente stabile per tutta la durata della vita.
- La `distribuzione sulla retina dei vasi` è principalmente casuale e assolutamente univoca.  Il pattern di vene parte dal nervo ottico, ma le successive diramazioni sono pressoché casuali.
- `Il sensore per la rilevazione della retine deve essere posizionato a breve distanza dall' occhio`.

Con metodi molto simili a quelle delle impronte digitale, vengono `estratte le minutiae` della retina e memorizzate in un template. Il pattern delle vene in alcune versione commerciali solitamente è un codice e barra circolare:
Retica, individua il centro del nervo ottico ed esegue delle `scansione dei toni di grigio lungo circonferenze concentriche`. Attraverso una `comparazione a soglia adattiva` è possibile convertire questo andamento in un insieme di bit (1 se l'intensità è sopra la soglia, 0 altrimenti).

![[Pasted image 20240214090929.png|300]]

Vantaggi :
- Molto efficiente
- Stabile
- Difficile da contraffare
- Difficilmente alterabile da fattori esterni
Svantaggi:
- Viene `rilevato dall'utente come intrusivo`
- Difficile da adattare nell'ambito commerciale
- Sentito come pericoloso per la vista
- `Elevato costo` dei sensori
- Non più sviluppata