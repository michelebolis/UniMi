Viene generato un insieme di programma $\Pi$ simili al programma P in esame
Su di essi viene eseguito lo stesso test T previsto per il programma P
- SE P è corrotto, allora i programmi in $\Pi$ DEVONO essere sbagliati
- Per almeno un caso di test devono produrre un risultato diverso

Un test T soddisfa il criterio di copertura dei mutanti SE e SOLO SE per ogni mutante $\pi \in \Pi$ esiste almeno un caso di test in T la cui esecuzione produca per $\pi$ un risultato diverso da quello prodotto da P

La metrica è la frazione di mutanti riconosciuta come diversa da P sul totale di mutanti generati

Aspetti da considerare
- [[Analisi mutazionale - Generazione dei mutanti]]
- [[Analisi mutazionale - Operatori mutanti]]
- [[Analisi mutazione - Schema]]