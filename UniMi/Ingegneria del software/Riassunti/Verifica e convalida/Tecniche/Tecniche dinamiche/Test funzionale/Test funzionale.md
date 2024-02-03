Il test funzionale si concentra sulla verifica del comportamento del programma dal punto di vista dell'utente finale, non sfruttando quindi la conoscenza del codice (black box)
Puo essere l unico approccio possibile (es test di validazione del lavoro dal committente esterno)
I dati di test possono essere derivati dalle specifiche, concentrandosi quindi sul dominio delle informazioni e NON sulla struttura di controllo

Permette di identificare errori non sintetizzabili con criteri strutturali es funzionalità non implementata o cammino di flusso dimenticato
Obiettivo: trovare errori di interfaccia e di prestazioni

Raggruppamento tecniche:
- metodi basati su grafi es su Sequence Diagram e copertura dei thread dei messaggi
- [[Test funzionale - Testing delle interfacce]]
- suddivisioni del dominio in [[Test funzionale - Classi di equivalenza]] in modo da testare tutti i comportamenti distinti
- analisi dei valori limite / [[Test di frontiera]]
- collaudo per confronto verificando che non ci siano regressioni tra una versione e la precedente

Problemi nella fase di integrazione (in OO) difatti non esiste la struttura gerarchica che possa guidare l'integrazione delle unità

