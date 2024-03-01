[[Teoria della dualità]]

Osservazione
Dato che i coefficienti di $P$ e $D$ sono gli stessi, entrambi i problemi di coppia primale-duale si possono rappresentare sullo stesso tableau

Esempio
![[Pasted image 20240301095705.png]]

Tableau ristretto
![[Pasted image 20240301095935.png]]


Data questa osservazione, è possibile lavorare sul tableau del problema primale, eseguendo su di esso gli stessi passi di pivot che l'algoritmo del simplesso eseguirebbe se lavorasse sul tableau del problema duale
L'algoritmo risultante è l'algoritmo del simplesso duale
Simplesso primale: conserva l'ammissibilità e persegue l'ottimalità
Simplesso duale: conserva l'ottimalità e persegue l'ammissibilità
Nell'algoritmo del simplesso duale le regole di scelta del pivot sono duali:
- la riga del pivot viene scelta prima della colonna: il suo termine noto deve essere negativo (vincolo violato)
- il pivot deve essere negativo
- la colonna del pivot viene scelta minimizzando il valore assoluto del rapporto tra il coefficiente di costo ridotto ed il candidato pivot

L'algoritmo del simplesso duale è  utile quando la base è inammissibile e super-ottima
E' una tipica situazione che si verifica negli algoritmi "cutting planes", che vengono usati per risolvere rilassamenti continui di problemi di PL intera o binaria

[[Algoritmo del simplesso duale - Esempio]]