Fornisce una interfaccia unificata e semplificata a un insieme di interfaccia separate

Situazione: definire una serie di interfacce molto specifiche e dettagliate per i propri componenti 
Problema: quando un Client, dovendo accedere al sistema, si ritrova costretto a dover interagire direttamente con i sottosistemi che lo compongono, cosa che lo obbliga a sviscerare i funzionamenti interni dello stesso per ottenere un comportamento tutto sommato semplice.

Scopo: **fornire un’interfaccia unificata e semplificata a un insieme di interfacce separate**
Spesso infatti l’uso comune di un sistema si riduce un paio di operazioni ottenibili combinando varie funzionalità fornite dal package; invece di richiedere al Client di operare tale composizione facciamo ricadere sulle nostre spalle tale compito costruendo una _classe_ che faccia da _interfaccia standard_ al sistema.

![[Pasted image 20231109093716.png]]

Questo non impedisce al Client di usare anche le funzionalità più complesse, ma metta solo ulteriormente a disposizione un’interfaccia che gli permetta di sfruttare facilmente quelle più frequentemente utilizzate. 
Volendo fornire un esempio nella vita reale, un telecomando fornisce un’interfaccia semplice ai controlli della televisione, permettendo di regolare il volume e cambiare canale con semplicità: aprendo però uno sportellino ecco che ci vengono forniti tutti i comandi più specifici.