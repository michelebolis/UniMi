Gradle è uno strumento di build automation che utilizza le repository Maven come punto di accesso alle librerie di terze parti. 
Maven è una piattaforma di gestione delle dipendenze e della build automation per il linguaggio di programmazione Java. Le repository Maven sono archivi online che contengono librerie Java, plugin e altri componenti utilizzati nella build di progetti Java.
Gradle utilizza queste repository per cercare e scaricare le librerie di cui ha bisogno per eseguire la build del progetto.

Gradle, che supporta Groovy o Kotlin come linguaggi di scripting, adotta un approccio dichiarativo e fortemente basato su convenzioni. 
Ciò significa che tutto ciò che è già stato definito come standard non deve essere ridichiarato. 
Inoltre, Gradle definisce un linguaggio specifico per la gestione delle dipendenze e permette di creare build multi-progetto.

Gradle scala bene in complessità: permette di fare cose semplici senza usare le funzioni complesse. È estendibile tramite plugin che servono per trattare tool, situazioni, linguaggi definendo task e regole per lavorare più facilmente.

Il plugin _Java_ definisce:
- una serie di **sourceSet**, ovvero dove è presente il codice e le risorse. Principalmente sono:
    - `src/main/java`: sorgenti Java di produzione;
    - `src/main/resources`: risorse di produzione;
    - `src/test/java`: sorgenti Java di test;
    - `src/test/resources`: risorse di test.
- dei **task**, anche con dipendenze tra loro.