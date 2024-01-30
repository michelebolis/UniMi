La `Noun Extraction` è una tecnica basata sulle specificazioni in cui vengono estratti tutti i sostantivi o frasi sostantivizzate.

1. Si considerano tutti i candidati e si incomincia a sfoltire

Criterio di sfoltimento
- Ridondanza dello stesso concetto data anche da sinonimi, nomi simili o concetti. 
- Vaghezza o nomi generici potrebbero esserci una classe comune astratta
- Nomi di eventi o operazioni che non hanno un concetto di stato
- Metalinguaggio: parti statiche che fanno parte della logica del controllo 
- Esterno al sistema cioè concetti assoluti (es la settimana ha 7 giorni)
- Attributi dei vari candidati

2. Poi si cercano le relazioni, solitamente date dai verbi

Si collegano le linee senza specificare le direzione dell'associazione (associazioni NON attributi)
Si specificano ora le cardinalità tra le relazioni
Si cercano generalizzazioni e fattorizzazioni (eventualmente rimuovendo una generalizzazione)