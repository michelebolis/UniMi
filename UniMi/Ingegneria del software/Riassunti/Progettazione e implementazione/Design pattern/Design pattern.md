E' uno strumento concettuale che cattura la soluzione per una famiglia di problemi e che esprime architetture vincenti

Terminologia
- Antipattern: denuncia di una soluzione sbagliata anche se ragionevole ad un problema
- Idioma: un modo di risolvere il pattern dipendente dal linguaggio
- [[Meta pattern]]

Ad ogni pattern sono quindi associati una serie di idiomi

Gang of Four Patterns: definisce 23 patter e li classifica in tre categorie
- Creazionali: creazione degli oggetti
- Comportamentali: interazioni tra gli oggetti
- Strutturali: composizioni di classi e oggetti

- [[Singleton]]

- [[Iterator]] 

Nullability
ad una variabile che indica un riferimento a un oggetto allora possiamo assegnarci un valore null
Problema: quando proviamo a deferenziare la variabile e non puntando a nulla, riceviamo un errore

...

come implementare attributi diversi da null: 
assert attributo!=null;

modalita sviluppo: faccio un if --> segnalo io l errore dell utilizzatore, programmazione difensiva
modalita produzione: assert o notazione --> assumo l utilizzo corretto, programmazione con contratto