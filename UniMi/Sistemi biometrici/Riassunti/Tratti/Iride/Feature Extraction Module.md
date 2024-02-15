La grande variabilità delle immagini dell'iride, fanno fallire la maggior parte degli approccio di filtraggio visti per le impronte digitali. Approcci come segmentazione, binarizzazione non funzioneranno.

Dougman invece propone il seguente approccio :
Cercare nell'immagine ( estrazione di un massimo), I centri dei contorni di variazioni di grigio di forma circolare ( l'integrale lungo un cammino circolare di derivata radiale).

Esiste una formula che prende il nome di operatore integro differenziale di Dougman :
- G ( r ) = Rappresenta il pre filtraggio dell'immagine. SI tratta di un filtro gaussiano passa basso di raggio teta. Si eliminano dalla ricerca i cerchi dei piccoli riflessi iù piccoli di una certa soglia teta.
- I(x,y ) rappresenta l'immagine raw dell'iride
- L'operatore nel modulo si comporta complessivamente come un filtro di circular detection, ossia un riconoscitore di bordi circolari, esso produce valori alti quando incontra un cerchio vicino al perimetro di esplorazione circolare in x0, y0 di raggio r.

È possibile modificare l'operatore integro differenziale per le iridi, andando cosi a trovare le palpebre. Le palpebre vengono viste come una parte di parabola, il cammino di integrazione diventa una parabola e non più un cerco. 

Estrazione delle ciglia :
Le ciglia si possono individuare, secondo delle conoscenze note a priori :
- Le ciglia devono  partire dalla posizione individuata delle palpebre  ( partenza fissa)
- Le ciglia risultano sempre più scure rispetto all' iride
- La loro dimensione minore ( larghezza) è facilmente stimabile

È importante individuare ogni parte dell'immagine che non sia iride per non inserire in enroll una informazione errata.