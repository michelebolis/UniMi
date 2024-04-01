Liste di collisione o concatenamento esterno
Posizione $i$: contiene ogni record la cui chiave $x$ ha valore hash i $h(x)=i$

Operazioni:
- Inserimento(elemento e, chiave k): $O(1)$ SE inserisco all inizio della lista
- Ricerca(chiave k) --> elemento: caso peggiore $\Theta(n)$
- Cancellazione(chiave k)

In media lunghezza della lista $\frac{n}{m} = \alpha$
$T_{avg}(n)= O(max(1, \frac{n}{m})) = O(1+ \frac{n}{m})$ //1 perche potrei avere liste vuote

Tempo dipende da quanto è piena la tabella
Importante che ci sia sparpagliamento

OSS $\alpha$ puo essere >1

SE la funzione hash NON sparpaglia bene si potrebbero formare alcune liste molto lunghe
Agglomerazione è la presenza di zone in cui si concentrano molti dati