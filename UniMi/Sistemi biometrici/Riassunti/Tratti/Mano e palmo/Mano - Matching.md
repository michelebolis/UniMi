Passi per il matching
- `Peg Removal`: conoscendo la posizione fissa dei `pioli` è facile sottrarli alle immagini per avere a disposizione solo la mano.
- `Estrazione dei contorni`: si usa un `algoritmo a soglia adattiva per segmentare l'immagine` e trovare il contorno esterno della mano.
- `Estrazione delle dita ed allineamento`: le 5 dita vengono estratte dal profilo ed allineate separatamente a partire da posizioni standard. Questo rende il matching maggiormente veloce.

- Matching:
	- `Le curve delle due mani da confrontare gia allineate sul riferimento vengono trasformate in gruppi di punti`
	- Il matching lavora individuando `coppie di punti e misurando la loro distanza`. La loro distanza media è chiamata `mean alignment error MAE`
	- `Se il MAE è minore di una soglia prefissata l'utente è considerato un genuino altrimenti come impostore`

`Eigenfingers`: in modo assolutamente simile al metodo delle autofacce da un database di immagini di mani, è possibile `ricostruire le dita ed il palmo`.

Ad oggi non si ha notizia di comparazioni indipendenti dal produttore di algoritmi e sistemi biometrici basati sulla mano, simili a quelli per il volto ( FRVT) ecc…

Un test governativo (INPASS Evaluation),  ha rilevato le seguenti performance :
- FTE = 2% ( failure to enroll)
- FNMR = 1,5 % FMR = 1,5 %
- ERR = dal 3 al 1.5 %  punto della curva det in cui FNMR = FMR riassuma dal punto di vista generale l'andamento di un sistema biometrico.