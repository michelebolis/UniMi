Approccio `deterministico`

Viene eletto una stazione a `master`, (es con un algoritmo distribuito): essa conosce la composizione della rete e ne fa parte.
Il master genera un token e lo invia attraverso un anello logico (es prima A poi B poi C) passando il token con round-robin
Ogni stazione è istruita in modo tale che invii i suoi frame solo se ha il token. 
SE una stazione con il token ha frame da inviare nel buffer, lo invia sul canale passando anche il token alla stazione successiva

La rete deve essere configurata nel caso si aggiungano nuovi nodi alla rete in modo da includerli nell'anello logico.

Problemi
- fairness: evitare che chiunque prenda il controllo del canale non ne approfitti
- Girando il token in modo sistematico, esso arriva a tutte le stazioni, incluse quelle che non hanno frame da inviare, perdendo cosi tempo.
- Caricando nel master la funzione centrale di generazione del token, nel momento in cui crasha la rete smette di funzionare e sarà necessario un reset