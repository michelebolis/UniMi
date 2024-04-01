Struttura principale in cui rappresentiamo i vertici (array), in ciascun elemento ho una lista dei vertici adiacenti
In questo caso la rappresentazione degli archi è implicita nell'elemento del vertice
Tuttavia ogni arco viene rappresentato due volte
- Grafo non orientato
$\sum lunghezza liste = 2*m$
$Spazio= \Theta(n)+\Theta(m)$
- Grafo orientato
Archi rappresentati solo una volta, data la posizione x ottengo i vertici adiacenti
$\sum lunghezze liste = m$
$Spazio= \Theta(n+m)$

Vantaggi: semplice trovare vertici adiacenti, e quindi gli archi uscenti
Svantaggi: non posso trovare archi entranti in quello orientato

es
![[Pasted image 20240401145256.png|400]]
