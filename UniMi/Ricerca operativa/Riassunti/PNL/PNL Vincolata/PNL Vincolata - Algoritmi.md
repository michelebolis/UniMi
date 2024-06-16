Per ogni dato sottoinsieme di vincoli attivi, `working/active set`, è possibile risolvere un problema di PNL non vincolata
TUTTAVIA questo metodo soffre per l'`esplosione combinatoria` nel numero di sottoinsiemi che è necessario considerare

I metodi active set eseguono una ricerca intelligente, `scartando a priori alcuni sottoinsiemi`
I metodi del punto interno / `metodi a barriera` producono sequenze di punti che non rendono attivo alcun vincolo di disuguaglianza, bensì si `avvicinano asintoticamente al contorno della regione ammissibile`

Vediamo come rilassare i vincoli per passare da un problema vincolato ad uno non vincolato
In generale gli algoritmi di PNL devono bilanciare due effetti di ogni passo
- `il miglioramento della funzione obiettivo`
- `il peggioramento nella violazione di alcuni vincoli`

[[PNL Vincolata - Metodi basati sulla funzione di merito]]
[[PNL Vincolata - Derivate direzionali]]
[[PNL Vincolata - Metodi basati sui filtri]]