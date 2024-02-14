Panoramica delle tecniche :
![[Pasted image 20231106104720.png]]
- Metodi di binarizzazione :
I metodi di binarizzazione portano una immagine in toni di grigio in un immagine in bianco e nero dove sono evidenziati i ridge.
- I metodi classici di binarizzazione a soglia globale e a soglia locale nel caso delle impronte non funzionano in modo robusto.
- Funziona in modo robusto per le impronte la binarizzazione adattativa

- Thinning :
L'operazione di thinnig corrisponde a ridurre progressivamente le linee di un immagine binarizzata fino allo spessore di 1 pixel ( scheletro dell'immagine)

L'algoritmo deve anche (se possibile) riempire i buchi nei ridge per non creare profili di questo tipi :
![[Pasted image 20231106104751.png]]
- Identificare una minuzia
Esaminando l'intorno di ogni punto lungo un ridge di una immagine scheletrizzata è immediato trovare se siamo su fine riga o una biforcazione.

Basterà contare le intersezioni lungo il perimetro della matrice 3\*3 attorno al punto :
- Una intersezione fine riga
- Due intersezioni -> ridge passante
- Tre intersezioni biforcazione.

Il perimetro della matrice è quello al difuori del bordo del quadrato evidenziato.
![[Pasted image 20231106104914.png]]
Se le intersezioni sono maggiori di 3 occorre esaminare meglio i casi per stabilire se siamo in casi particolari.

- Metodi di post processing
I moduli di post processing, hanno il compito di rimuovere le minutiae spurie introdotte dai moduli precedenti per errore.

L'errore che si può commettere è quello di togliere una minutia corretta commettendo quindi errori.

Esistono due categorie principali di post processing :
- Structural post processing  :
I moduli di structural post processing sono tipicamente basati su regole.
Controllano le caratteristiche dello scheletro adiacente alla minutia candidata.
Le regole maggiormente usate sono 8.
![[Pasted image 20231106104941.png]]

- Minutiae filtering gray scale
I moduli di post processing sono basati su toni di grigio, vengono analizzate le regioni dell'immagine a toni di grigio adiacenti alla minutae da tenere o scartare.

Si possono usare vari algoritmi per effettuare questo controllo ( reti neurali).