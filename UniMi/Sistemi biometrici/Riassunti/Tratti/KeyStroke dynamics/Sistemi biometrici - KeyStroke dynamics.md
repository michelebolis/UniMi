KeyStroke dynamics
Si tratta di sistemi di identificazione basati sulla dinamica della battitura alla tastiera e si basano sull'ipotesi che persone diverse battono in modo diverso.

L'analisi della digitazione e firma online sono simi :
- Tratti biometrici comportamentali
- Sono variabili nel tempo, dipendono dalle condizioni dell'individuo
- Buona privacy, poco invasivi
- Acquisibili da sensori economici
- Gli algoritmi di matching hanno bisogno di allineamenti temporali

Altre tecniche simili riguardano il tipo di swaping sullo schermo, oppure come l'utente utilizza il mouse. Si tratta di metodi che vanno ad identificare una persona in base al comportamento in un ambiente software o come interagisce con il Sistema operativo.

Con il solo comportamento non è sempre possibile verificare una identità all'atto del login sul sitema ( troppo poca informazione).  Tutta via possono essere utilizzati per identificare se la persona che sta usando il terminale è quella autorizzata, autorizzazione continua dell'utente.

KeyStroke dynamics  -> two factor authentication :
La possibilità di estratte il template direttamente mentre si scrive la password, di fatto rende possibile una istantanea verifica a due fattori. Se aggiungiamo anche le tecniche OTP al login, allora avremo una verifica a 3 fattori.

Estrazione delle feature :
Le tecniche di keyStroke dynamic si impiegano a regolare gli accesi ad un terminale, in quanto non serve nessun altro sensore se non la tastiera stessa del terminale.

Le feauture locali che possono essere estratte sono le seguenti :
- Latenza fra due pressioni
- Tempo di battitura del taso ( tempo per il quale il tasto rimane premuto)

 utilizzabili per controllo login.

Alcune feature, meno interessanti ( se non combinate con le altre possono essere) :
- Tempo globale di battitura
- Frequenza di errori
- Forza applicata nella battitura di un tasto
- L'uso di tasti non query

Esistono anche qui delle feature globali calcolabili quando la sessione di battitura è terminata :
- Associazioni tra tasti, le quali possono essere statiche ( numero di volte che è stata usata la coppia alt + tab) o dinamiche ( tempo che intercorre tra la battitura della coppia di tasti alt tab)

Non utilizzabili per il login, come tutte le feature globali.

Vantaggi :
- Sitemi di tipo software, oltre alla tastiera del terminale di cui si vuole regolare l'accesso non c'è bisogno di sensori
- Sono molto ben accetti dagli utenti, poco invasivi
- Possono essere utilizzati senza che l'utente se ne accorga. L'utente quindi può non essere collaborativo.

Svantaggi :
- Bassa accuratezza
- Informazioni utilizzate per rompere le password
- Cambiando la tastiera spesso i tempi cambiano
- Ferite sulle mani o traumi possono influenzare la battitura.

Attacchi ai sistemi keyword dynamics :
Attacco sul canale SSH, è possibile in quanto tale protocollo trasmette immediatamente un pacchetto non appena viene premuto un tasto. DI conseguenza è possibile intercettare la password in base ai tempi di latenza rispecchiati fedelmente dalla LAN.

I tempi di latenza da soli non riescono a dare abbastanza informazioni per recuperare una password immediatamente, ma restituiscono delle probabilità sule coppie di lettere che permettono ai generatori di password di ridurre il tempo di computazione necessario ad effettuare un attacco di tipo brute force.

Biometria Less-constrained e Uncostrained

Less - Constrained biometry :
- Senza contatto
- Elevata distanza
- Condizioni di luce naturale
- Serve un minimo di cooperazione da parte dell'utente

Uncostreined biometry :
- Soggetti non cooperativi
- Scenari non controllati

Contactless fingerprint :
Si tratta di un sistema biometrico less-constrined, a differenza dei "classici" sistemi biometrici con pressione delle impronte sui sensori, abbiamo i seguenti vantaggi :
- Assenza delle distorsioni elastiche della pelle nelle immagini delle dita
- Più resistente alla polvere e allo sporco
- Maggiore accettazione da parte degli utenti
- Possibilità di usare telecamere standard come sensori

Svantaggi :
- Parzialmente compatibile con i vari AFIS
- Sfondi complessi da gestire
- Sensibile all'illuminazione e alla posizione / distanza.  L'illuminazione deve essere controllata.
- I sistemi 2D possono essere vulnerabili a distorsioni di tipo prospettico dell'impronta
- Tempo di calcolo più lungo

Esistono ad oggi dei sensori 3d contactless per le impronte, dai quali si può ricavare molte informazioni 2D e 3D.