Una riga per ogni vertice e una colonna per ogni arco
Per i grafi non orientati è una matrice bool
$Spazio = \Theta(n*m)$
SE numero di archi basso potrebbe essere utile MA nel caso contrario è molto inefficiente

Per i grafi orientati uso -1, 0, 1
-1 SE arco entrante
1 SE arco uscente
0 ALTRIMENTI

$Spazio = \Theta(n*m)$

es
![[Pasted image 20240401145619.png|300]]