ad una variabile che indica un riferimento a un oggetto allora possiamo assegnarci un valore null
Problema: quando proviamo a deferenziare la variabile e non puntando a nulla, riceviamo un errore

...

come implementare attributi diversi da null: 
assert attributo!=null;


modalita sviluppo: faccio un if --> segnalo io l errore dell utilizzatore, programmazione difensiva
modalita produzione: assert o notazione --> assumo l utilizzo corretto, programmazione con contratto