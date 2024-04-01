Possiamo avere un numero arbitrario di figli --> numero arbitrario di sottoalberi
Ogni nodo, eccetto la radice, ha un unico padre
Es gerarchia delle classi
Definizione ricorsiva
- Struttura vuota
- Un nodo cui sono associati $k>=0$ alberi

Grado di un nodo= Numero figli
Grado dell'albero= max grado figli

Rappresentazione:
- Vettori dei padri
Array con i valori contenuti nei nodi
Array con la posizione del padre

Problema: difficile risalire da padre a figlio

- Vettore dei figli
Uso:
- Array con i valori contenuti nei nodi
- d array contenenti le posizioni dei figli di ogni nodo

- Puntatori ai figli
SE so il grado dell'albero è n
Posso avere nodi con n puntatori
Problema di memoria per puntatori a null

- Lista dei fratelli
Permette di convertire gli alberi in binari
Per ogni nodo considerare un puntatore che uso per puntare al primo figlio, il cui secondo puntatore punterà ai fratelli

Problema: accesso ai figli diventa sequenziale non piu diretto sapendo il padre

Ricerca in profondità con albero visto come indice del libro, ottengo effettivamente l'indice


Consideriamo alberi binari con $n$ nodi e di altezza $h$
Numero minimo di nodi per alberi di altezza $h= h+1$
Albero completo di altezza $h$ (Numero massimo di nodi) = $\sum_{i=0}^{h} 2^i= 2^{h+1} -1$
QUINDI $h+1 <= n <= 2^{h+1} -1$
QUINDI $h <= n-1$ e $2^{h+1} >= n+1$ --> $h+1>= \log_2 n+1$ --> $h>= \log_2{n+1} -1$
$\log_2(n+1) -1 <= h <= n-1$

Alberi quasi completi sono tali quando sono completi almeno fino al penultimo livello
Proprietà: un albero binario di altezza h è quasi completo SE E SOLO SE ogni nodo di profondità $<h-1$ possiede entrambi i figli
$2h <= n < 2h+1$
$h <= \log_2 n < h+1$
$h= \lfloor\log_2 n\rfloor$ 