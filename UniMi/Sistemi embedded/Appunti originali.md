## Intro: tutto, in dettaglio

* ### Definizione di sistema embedded

 Un **Sistema Embedded** è l'insieme composto da hw e sw (firmware ovvero sw direttamente integrato in un componente elettronico) dedicato a specifici scopi i cui elementi siano integrati e incorporati.  
 Il suo vantaggio è la sua capacita di interfacciarsi con il mondo esterno attraverso i GPIO.

* ### Panoramica generale sui sistemi embedded, classi di device, caratteristiche, ordini di grandezza (dimensioni, potenze, consumi, ecc.), ambiti di utilizzo

 (A) Alcuni esempi per capire i settori di utilizzo e sviluppo di tali sistemi sono:

* Avionica, aeronautica, sistemi di volo;
* POS e Bancomat;
* Elettrodomestici;
* Smart TV o IoT.

* ### Descrivere PLC

 Un **PLC** (Programmable Logic Controller) è un dispositivo semplice solitamente pensato per l'automazione ma non su larga scala. E' dotato di una buona connettività input/output per interagire con vari sensori ed attuatori. Sono programmabili con 4 linguaggi, ma spesso questi prodotti non sono interscambiabili o compatibili tra loro.

* ### Componenti interni di un MCU

 Un **microcontrollore o MCU** (MicroController Unit) consiste in un sistema hw completo in un singolo chip. Hanno una potenza di calcolo limitata (dai 200Mhz in giù), ottimi consumi energetici (meno di 1W) e ottima efficienza termica. Può contenere:

* Unità di elaborazione
* memoria dati (RAM o EPROM)
* oscillatore (circuito elettronico che genera forme d’onda di frequenza, utilizzato come sorgente di clock.)
* Memoria programma (ROM, EPROM, FLASH)
* GPIO (General Prurpose Input Output)
* porte di comunicazione base (USART, I2S, SPI, I2C, USB),
* porte di comunicazione analogiche (DAC, ADC, PWM).
* Nei modelli avanzati anche Wifi, Touch Screen, ecc.

* ### Definire SoC, cosa contiene, come si "combina" per la realizzazione dei vari prodotti reali

 un SoC (System On Chip) è una singola unità con più potenza computazionale che possono contenere quasi tutte le componenti del sistema. Può contendere: CPU, GPU, ISP (Image Signal Processor), Decoder/Encoder video, WiFi, Bluetooth, Display controller, Audio Controller, seriali, USB, ADC/DAC, Sensori, GPS, Modem, RAM, FLASH, ecc.
 Sono usati praticamente ovunque: automotive, militare, domotica, Set Top Box (lettori multimediali, sistemi tipo chrome cast ecc), navigatori satellitari e telefonia mobile.

## Concetti: tutto, in dettaglio

* ### Sistemi monoprogrammati e multiprogrammati, differenze, caratteristiche, cosa c'entra la MdT?

 In un sistema monoprogrammato viene eseguito un solo programma alla volta senza parallelismi mentre in un sistema multiprogrammato si possono eseguire più programmi "contemporaneamente" (o con il time sharing).  
 La MdT, Macchina di Turing, è una macchina a stati dotata di piu testine che leggono/scrivono simboli su uno o piu nastri, prendendo le decisioni in base al simbolo sul nastro.  
 E' possibile effettuare un paragone con la MdT considerando, il caso dei sistemi monoprogrammati una signola macchina a stati (unità di calcolo) che interpreta i simboli (istruzioni) su un singolo nastro (programma), mentre nel caso dei sistemi multiprogrammati più MdT che lavorano in contemporanea o una che interpreta un simbolo alla volta su più nastri (programmi) diversi.

* ### Conversione AD e DA, caratteristiche, pregi e difetti, considerazioni sul flusso di dati campionati

 La conversione AD trasforma un segnale analogico che varia nel tempo continuo in una serie discreta di rilevazioni che rappresentano il segnale.
 La conversione DA trasforma una sequenza di valori in un segnale continuo. (Come faccio variare la tensione in uscita)  
 Il **campionamento** è il processo con il quale stabilisco ogni quanto effettuare la misurazione.
 La **frequenza di campionamento** è la velocità con cui si fanno le misutazioni (*numero_letture/tempo*) mentre il tempo di campionamento è il tempo tra le misurazioni.  
 Se un evento dura meno del tempo di campionamento può non essere percepito, mentre uno che dura più della metà del tempo di campionamento rischia di produrre errori poichè più segnali potrebbero sovrapporsi (es [ruota auto](https://web.archive.org/web/20220830075514/https://fisicisenzapalestra.com/perche-in-accelerazione-le-ruote-girano-al-contrario.html))
 [Teorema Nyquist-Shannon](https://web.archive.org/web/20220830075514/https://fisicisenzapalestra.com/perche-in-accelerazione-le-ruote-girano-al-contrario.html): La frequanza di campionamento dev'essere pari o superiore al doppio della frequenza massima del segnale

* ### Spiegare tecniche di multiplexing (divisione tempo, frequenza), shift register

 Per **Multiplexing** si intende condividere un canale per trasportare più flussi informativi contemporaneamente.
 Tecniche:

* **Divisione di frequenza**: I segnali usano fequenze diverse e il ricevente si sintonizza su quella desiderata (es frequenze telefoni, radio). Se sono troppo vicine c'è interferenza.
* **Divisioni dei tempo**: i segnali vengono inviati sul canale in alternaza veloce, il ricevente smista i segnali.
 [Shift register](https://www.logicaprogrammabile.it/shift-register-arduino-74595/): componente esterno che permette di aumentare le uscite es SN74LS595. Per farlo bisogna necessita ad un pin che faccia da clock, uno che abiliti o meno la scrittura e un'altro per il dato il quale determini quali pin di uscita mettere a 1 o meno.

* ### Differenza fra controllo a loop chiuso e aperto, problemi del loop aperto

 Modello per rappresentare il funzionamento del sistema definisce una funzione di trasferimento *f(U(t), C(t), A(t))* con:

* U vettore delle variabili di uscita
* C vettore delle variabili di controllo
* A vettore delle variabili d'ambiente  

per **controllo a loop chiuso** ( f(C(t),A(t),U(t)) ) intendiamo un sistema la cui variazione di stato nel tempo dipende dalle variabili di ingresso(C), dalle variabili ambientali(A) (es umidità) e dalle variabili di uscita precedenti(U). (Esempio PIR: variazione di calore perciò deve conoscere la rilevazione precedente)  
per **controllo a loop aperto** ( f(C(t),A(t)) ) intendiamo un sistema la cui variazione di stato nel tempo dipende solo dalle variabili di ingresso e da quelle ambientali. (Esempio: LED)  
Il problema del controllo a loop aperto è che non c'è nessun controllo dell'efficacia dell'azione. (es con motore step non siamo sicuri che mantenga una velocità stabilita poichè se aggiungessimo un carico, questa rallenterebbe a fronte di un input invariato)

* ### Spiegare tecnica PID per controllo a loop chiuso

 E' un modello di controllo e per PID si intende Proporzionale-Integrativa-Derivativa ovvero:

* **Proporzionale**: la distanza assoluta dallo stato desiderato utilizzando lo stato attuale per valutare quanto sia distante dall'obiettivo.
* **Integrativa**: la storia dell'evoluzione dello stato del sistema calcolata in una finestra temporale (es media dell'errore).
* **Derivativa**: la velocità di variazione dello stato dall'obiettivo.

 Una volta calcolati i valori vanno stabiliti dei coefficienti per pesare la funzione P*(distanza) + I*(media errore) + D*(velocità variazione - può corrispondere alla distanza). È importate avere una funzione che definisca l'errore. Nel caso del motore e(t)= RegimeDesiderato - GiriMotore
 esempio:
 Ipotizzando che vogliamo un motore che vada ad un regime di 1400 giri

 Istante Regime Errore
 t-3:  1170 230
 t-2:  1200 200
 t-1:  1250 150
  t:  1300 100

 P: (1400 - 1300) = 100
 I: (230 + 200 + 150 + 100)/4 = 170
 D: (1400 - 1300) = 100
 pesando P=I=D=0.5 otteniamo 0.5*100 + 0.5*170 + 0.5*100 = 50+85+50 = 185

 Potremmo usare 185 come valore da aggiungere alla tensione data al motore. Dovremmo calcolaro cosa accadrebbe ora al tempo t+1 dopo la modifica e nel caso aggiustate i pesi attribuiti a P,I,D.
 Se mal calcolata si richierebbe di non raggiungere mai l'obiettivo (se correzione troppo debole) o oscillare intorno l'obiettivo (se correzione troppo forte).

* ### Considerazioni sull'uso della memoria in un Arduino, rispetto ai tipi di dati disponibili

 Essedo la memoria di Arduino (e in generale dei dispositivi embedded) molto limitata  (intorno ai 2 KB) è bene gestire con cura le tipologie di variabili dichiarate.
 es: se necessito di un numero che va da 1 a 10 è inutile dichiarare una variabile di tipo long(4B) e neanche un int(2B), ma basterebbe un byte(1B # da 0 a 255) o un char(1B)
 Dato che anche i record di arrivazione delle chiamate di funzioni occupano stack, è utile cercare di ridurle evistando lo stack overflow.

 Se si usano diverse stringhe preformate si può ridurre l'uso della RAM usando la funzione F() per leggere direttamente dalla Flash le stringhe.
 Anzichè scrivere;

 ```c
 Serial.print("Stringa");
 ```

 Si scriverà:

 ```c
 Serial.print(F("Stringa"))
 ```

 Ciò vale per qualsiasi stringa predefinita.
 La strinfa verrà presa direttamente dalla flash quando necessaria anzichè ricopiarla prima in RAM.

* ### Architettura Von Neumann vs. Harvard

 L'architettura di **Von Neumann** è presente negli attuali pc. Questa consiste in una Macchina di Turing in cui il nastro è unico e contiene sia dati che programma.  
 L'architettura **Harvard**, invece, è una MdT in cui i nastri rappresentanti la memeria dati e programma sono separati (es Arduino)

* ### Argomentare validità della ricorsione in ambito embedded, vantaggi e svantaggi

 L'uso della ricorsione permette spesso di scrivere codice più leggibile e semplice, ma il record di attivazione delle chiamate di funzione occupa spazio nello stack.  
 L'ambito dei sistemi embedded è costellato da architetture con poca memoria ram pertando le chiamate ricorsive potrebbero portare ad uno stack overflow potenzialmente non segnalato, portando effetti poco prevedibili.

* ### Descrivere la gestione della memoria in un sistema embedded

 Nella maggior parte non è presente l'MMU, pertando gli accessi a memoria non sono controllati e la loro gestione è demandata allo sviluppatore. Se l'indice di lettura/scrittura di un array sfora la sua size, si leggeranno o scriveranno altre locazioni di memoria. Stessa cosa per uno stack overflow, non si avranno messaggi di errore, ma si scriverà su altre locazioni.

* ### Spiegare meccanismo dell'interrupt

 Un HW **interrupt** non è altro che un modo che una periferica di qualsiasi tipo ha per segnalare al processore di eseguire azioni spefifiche fermandosi, salvano ciò che stava facendo (tipicamente nello stack) e, infine, riprenderlo una volta completata l'azione richiesta inizialmente dalla periferica.
 si può adibire un pin a segnale di interrupt associato ad una funzione. Nel caso in cui si verifichi l'evento definito su quel pin (es arduino: LOW, HIGH, CHANGE, RISING, FALLING) viene stoppata l'esecuzione del loop ed eseguita la funzione designata.

 ```c
 attachInterrupt(digitalPinToInterrupt(pin), ISR, mode) //ISR puntatore alla funzione di risposta
 ```

* ### Definire categorie "real time"

 Sono sistemi HW e SW capaci di fornire una **risposta in un determinato tempo o in un tempo deterministico**. Si dividono in:

* **hard real time**: lo sforamento della deadline si traduce in un intero fallimento del sistema.
* **soft real time**: lo sforamento della deadline si traduce in un degradamento del sistema (prestazionistico o di qualità del servizio).
* **firm real time**: lo sforamento di un determinato numero di deadline consiste in un fallimento.
 HW e SW sono progettati appositamente per lo scopo e mirando a garantire innanzi tutto l'affidabilità.

* ### Spiegare licenza proprietaria vs. libera

Licenza proprietaria:

* divieto di eseguzione su più dispositivi
* divieto di rivendere il programma
* divieto di analisi del codice (reverse engineering)
* divieto di studiarne le prestazioni e pubblicare confronti
* divieto di modifica
* divieto di esportazioni
* divieto di fare copie di sicurezza (non per la legislazione italiana)
* possibile scadenza a termine

Licenza libera:

* L0: libertà di esecuzione per qualsiasi scopo
* L1: libertà di studiarne il funzionamento e apportare modifiche (accesso al codice sorgente necessario)
* L2: libertà di ridistribuire copie
* L3: libertà di migliorare il programma e pubblicare il codice con i miglioramenti. La comunità ne trae beneficio (accesso al codice sorgente necessario)
  
* ### Fare esempio di licenza software libera, descrivendone le caratteristiche salienti

 (A) **GNU** General Public License (o più comunemente indicata con l'acronimo GPL). Si tratta di una licenza fortemente copyleft (ovvero con libertà di utilizzare, copiare, modificare e distribuire un prodotto dell'ingegno) per SW libero. Molto particolare poiché col susseguirsi delle modifiche deve continuare a garantire le cosiddette quattro libertà citate sopra (da L0 a L3).  
 L'editor di testo Emcs ed il kernel Linux sono esempi di SW diffusi che per primi adottarono questa licenza.
 La caratteristica principale è rappresentata dal fatto che il GNU GPL non è liberamente modificabile, ma solo la copia e la distribuzione sono permesse.  
 Progettata inoltre per essere facilmente applicata ai programmi se si è titolari dei relativi diritti.

* ### Descrivere il concetto di watchdog

 (A) Per '**watchdog**' si intende un meccanismo che permette il monitoraggio grossolano di un device. Tipicamente è un circuito elettronico esterno che viene opportunamente stimolato tramite segnale di un apposito GPIO.
 In assenza di segnale sul GPIO viene resettato il device. Semantica del segnale: "sono vivo, tutto bene". La ratio è che un reboot risolva i problemi.

## Richiami: tutto, in dettaglio

* ### cos'è la tensione?  

 La **tensione o potenziale elettrico** è la forza di attrazione applicata allo spostamento degli elettroni tra due poli. Si minura in **Volt V**.

* ### cos'è l'intensità?  

 L'**intensità** è la quantità di elettroni (Culomb) spostati in un secondo. Si misura in **Ampere A**.

* ### cos'è un segnale?  

 Un **segnale** elettrico è un informazione associata a grandezze di tensione e corrente su conduttori.

* ### descrivere leggi di Ohm e loro significato

  Indice:
  * I= intensita (A)
  * V= tensione (V)
  * R= resistenza (ohm)  

Leggi:  

* $I=\frac{V}{R}$: indica che l'intensità è direttamente proporzionale alla tensione e inversamente alla resistenza.
* $P=R*I^2$: indica che la potenza (intesa anche come calore dissipato), misurata in Watt, è proporzionale alla resistenza per il quadrato dell'intensità (Perciò ridurre l'intensità ha un effetto maggiore sulla riduzione del calore dissipato)
* Dalle prime due si può derivare $P=V*I$

* ### descrivere leggi di Kirchhoff  

* delle **correnti**: in un nodo la somma delle correnti entranti e quelle uscenti si bilanciano. Quindi non si creano o perdono elettroni. $\sum_{k archi}I_k=0$
* delle **tensioni**: in un circuito la somma delle tensioni è pari a 0. Quindi non si creano o perdono tensioni. $\sum_{k tratti}V_k=0$

* ### differenza fra corrente alternata e continua  

* **produzione**: alternata/induzione meccanicamente o elettronicamente (inverter), mentre la corrente continua chimicamente, per accumulo elettrostatico o meccanica (dinamo)
* **immagazzinamento**: alternata NON accumulabine senza trasformarla in altra energia, continua è accumulabile con accumulatori chimici (batterie) o condensatori
* **trasformabilità**: alternata facilmente trasformabile con un trasformatore, continua non facilmente trasformabile
* **trasportabilità**: alternadola trasformandola semplifica la trasportabilità e con le leggi di Ohm capiamo che aiuta alzare la tensione a scapito dell'intensità per portare più potenza senza disperdere troppo calore. $P=V*I$ e $P=R*I^2$

* ### cos'è la potenza elettrica?  

  La **potenza** è intendibile come la capacità di produrre lavoro

* ### panoramica delle unità di misura (elettricità/elettronica) e loro significato  

* Volt: associato alla tensione
* Ampere: associato all'intensità (corrente)
* Ohm: associato alle resistenze
* Watt: associato alla potenza
* Herz: associato ad un segnale sinuisale indica quanti cicli completi (da picco a picco) vengono effettuati in un secondo (es 100 Hz sono 100 cicli in un secondo)

* ### cosa si intende con "forma d'onda"?  

 La **forma d'onda** è una rappresentazione cartesiana di una grandezza elettrica (Tensione o corrente) rispetto al tempo

* ### spiegare Veff (efficace)  

 $V_{eff}=\frac{V_{picco}}{\sqrt{2}}$ Indica il valore che dovrebbe avere una tensione continua per avere la stessa potenza, quindi per essere efficiente

* ### descrivere a grandi linee il funzionamento di un resistore/condensatore/transistor/etc./... citare utilizzi  

* **interruttore**: apertura/chiusura di un circuito azionato a mano, interrompendo il flusso di corrente
* **pulsante**: interruttore con molla di ritorno alla posizione iniziale
* **relè**: pulsante o deviatore comandato elettricamente attarverso un segnale elettrico. Si usa per comandare flussi elettrici importati (in intensità o tensione) con flussi meno importanti. (nucleo ferromagnetico avvolto in una bobina di filo elettrico.
 Se passa corrente nella bobina, il nucleo diventa magnetico e cambia lo stato)
* **resistenza** (o resistore): riduce la tensione di un flusso di corrente che la attraversa dissipando la potenza in calore. Utilizzata per generare calore (phone) negli elettrodomestici, per ridurre la tensione $V=R*I$ o per limitare la corrente massima in un circuito $I=\frac{V}{R}$
* **condensatore**: accumulatore temporaneo di elettroni. Formato da due piastre conduttive vicine separate da un materiale più isolante dell'aria. Si carica applicandogli una tensione e si scarica applicandovi un carico. La velocità di scarica diminuisce nel tempo poichè nel mentre diminuisce anche la tensione.
* **semi-conduttori**: condicono o meno corrente in base a varie condizioni di contorno
* **diodo**: semi-conduttore che fa passare la corrente in un unica direzione. Dando tensione positiva all'anodo la corrente scorre, altrimenti è come un interruttore aperto. Il led è un tipo di diodo che come caratteristica secondaria emette luce.
* **transistor**: un semiconduttore che si comporta come un relè. Una piccola corrente definisce il passaggio tra due punti dove passa grande corrente. Se quella di pilotaggio varia nel tempo la corrente in uscita avrà la stessa forma d'onda, ma con intensità maggiore. Esistono transinsor che anziche usare flussi di corrente per pilotare usano campi elettrici diminuendo la dispersione di calore.

* ### spiegare i collegamenti serie e parallelo per resistori e condensatori  

* resistenze:
  * **in serie** i loro effetti si sommano
  * **in parallelo** seguono la formula $R_{tot}=\frac{R_1*R_2}{R_1+R_2}$. Il flusso di corrente si distribuisce proporzionalmente al valore delle resistenze
* condensatori:
  * **in serie** la capacità totale si comporta come le resistenze in parallelo $C_{tot}=\frac{C_1*C_2}{C_1+C_2}$
  * **in parallelo** la capacità totale è data dalla somma dei componenti

* ### spiegare costante di tempo RC  

 La **costante di tempo RC** è il tempo impiegato dal condensatore per caricare il 63,2% della capacità restante da caricare.
 $t=R*C$ (esempio un condensatore scarico impiegherà t tempo per caricare il 63,2% della sua capacità totale, un altro t tempo per caricare il 53,2% della 36,8% della capacità mancante e così via)

* ### descrivere un filtro passa alto/basso, elencare utilizzi  

 Consideriamo un circuito composto da una sola resistenza e da un solo condensatore.  

* Un filtro **passa alto** è formato da un **condensatore** in serie e in parallelo abbiamo la resistenza. In questo modo fa passare solo i segnali ad alta frequenza
* Un filtro **passa basso** invece è formato da una resistenza in serie e da un condensatore in parallelo. In questo modo non fa passare i segnali che superano una certa frequenza.

* ### quale effetto ha un condensatore su un segnale variabile?  

 SE viene applicata una tensione variabile, in uscita si avranno forme d'onda diverse dall'originale in base a quale dei due filtri si è utilizzato.

* ### descrivere integratore (passa basso) e differenziatore (passa alto) RC  

 I nomi dei circuiti del passo basso e alto diventano rispettivamente integratore e differenziatore quando applico una tensione variabile in ingresso.  

* L'**integratore** avra una forma d'onda con una dolce salita, data dalla costante RC necessaria per caricare. (peggiora all'*aumentare* della frequenza)  
* Il **differenziale** invece durante la fase alta dell'onda quadrata, il condensatore si carica mentre durante la fase 0 si scarica sulla resistenza con una descrescita dolce. (peggiora al *decrescere* della frequenza)

* ### spiegare PWM e utilizzi  

 Un Pulse With Modulation è un segnale con una forma d'onda quadrata con un periodo fisso ma non simmetrico. Solitamente la semi-onda alta corrisponde all'1 logico e quella bassa 0 logico.  
 Usi:

* passaggio di informazioni allungando o diminuendo la durata del segnale alto rispetto a quello basso. La durata si misura in percentuale rispetto quello basso. L'attrezzo che misura il segnale ne determina la semantica.
* pilotare carichi attivi es motori per dare un effetto di regolazione. Se ad un motore avviato stacca l'alimentazione continua a girare per inerzia, ma diminuisce la sua velocià.

* ### panoramica strumenti di misura e loro uso, problemi possibili  

* **lampadina attaccata a coppia di fili collegati a dei moresetti**: si collega un morsetto a masse e l'altro lo si attacca nelle varie parti del circuito. Se arriva tensione la lampadina ci accenderà. La lampadina deve essere scelta in modo che possa accendersi alla tensione desiderata.
 Nell'ambito embedded si una il led anzichè la lampadina, nel caso munito di resistenze se la tensione è troppo alta.  
 Se la lampadina è collegata in serie ad una batteria allora la si può usare per testare la continuità. Es su un cavi interrato, senza dissotterrarlo, cortocircuito i capi inserendoci in mezzo il "tester". Se la lampadina si accende il cavo è a posto.
* **voltmetro**: strumento che misura la tensione tra di punti di un circuito. Lavora in parallelo. Serve a capire se ci sono parti insufficientemente alimentate o non alimentate.
* **amperometro**: strumento che si inserisce in serie e misura l'intensità di corrente passante. Serve per misurare l'intensità, stimare il consumo e per valutare la potenza impiegata con la legge di Ohm $P=R*I^2$. Ha resisteza bassissima per interferire il meno coppibile con le misurazioni. Se collegato ad una funte di alimentazione saltano le protezioni (se le ha) o si fondono i cavi,
* **pinza amperomentrica**: tipo di amperometro usabile in parallelo. Le due ganasce della pinza si chiudono su un file e minurano per induzione elettromagnetica su correnti alternate.
* **ohmometro**: misura i valori di resistenza e lo si può usare per valutare la condizione di una giunzione (diodi e transistor):
  * giunzione interrotta: resistenza infinita in entrambi i sensi
  * giunzione in corto: resistenza zero in entrambi i sensi
  * giunzione possibilmente a posto: resistenza infinita in un senso e zero nell'altro
 è uno stromento attivo composto da un amperometro e una pila che fornisce tensione. Viene immessa la tensione di regime al componente da valutare e misurando la corrente (intensità) che scorre nel circuito e usato la legge di Ohm $R_{incognita}=\frac{V_{immessa}}{I_{misurata}}$
* **multimetro**: strumento che integra i vari strumenti di misura.
* **oscilloscopio**: misura le forme d'onda. se collegato a due punti di un circuito plota su un display il grafico dell'andamento della tensione. Solitamente hanno più ingressi per poter confrontare più forme d'onda contemporaneamente.

## Sensori: dispositivi che cambiano le proprie proprietà elettriche (es resistenza) al variare delle condizioni ambientali

* ### panoramica generale su sensori "fisici", esempi  

 Sensori relativamente semplici che cambiano le proprietà in funzione di qualche semplice principio fisico diretto e forniscono come output una grandezza elettrica.  
 es:

* sensore di rumore a condensatore: una delle due piastre del condensatore è strutturata in modo da muoversi quando colpita da onde sonore e, quindi, si ottiene che in caso di rumore cambia la capacità del condensatore.

* interruttore a mercurio: bulbo di vetro contenete una goccia di mercuri al suo interno e due elettrodi. Muovendo il bulbo si muove la goccia che, in base a come è orientato il bulbo, potrebbe chiudere il contatto elettrico degli elettrodi. Si ottiene così un sesore di pendenza fisico  

* ### panoramica generale su sensori "numerici", esempi  

 Sensori più complessi che forniscono un output numerico.  
 es:

* sonar: due buzzer emettono degli ultrasuoni che rimbalzando vengono catturati da un microfono. Il tempo tra l'emissione e la ricezione aiuta a stabilire la presenza di ostacoli e la loro distanza.

* ### panoramica generale su attuatori, esempi

 Un **attuatore** è un dispositivo che cambia le proprie proprietà meccanica in funzione di segnali elettrici in input.
 es:

* motori
* relè

* panoramica generale su motori, esempi  
* servomotore: riceve in input una tensione che definisce la rotazione.
* step (passo a passo): riceve in un segnale che deficisce uno spostamento angolare.

## Architetture: tutto, in dettaglio

* ### cos'è un ISA?  

 Un **ISA**, Instruction Set Architecture, è un modello astratto di una architettura che descrive tipologia di dati utilizzabili, registri, come devono essere fatti input e output e le instruzioni macchina.

* ### differenze fra CISC, RISC, VLIW, EPIC  

* **CISC** (Complex Istruction Set Computing): architetture con tante instruzioni low-level di dimensione variabile che possono rischiedere diversi cicli di clock per essere completate.  
 Vantaggi: le instruzioni possono avvicinarsi a quelle di alto livello  
 Svantaggi: la complessità computazione ne aumenta i costi di realizzazione (servono più componenti).
* **RISC** (Reduced Istruction Set Computing): architettura con poche, semplici e ottimizzate istruzioni completabili in pochi cicli di clock.
 Vantaggio: basso costo in silicio, grande efficienza  
 Svantaggio: difficoltà di programmazione per il basso livello. È fondamentale avere compilatori efficienti.
* **VLIW** (Very Long Instruction Word): architettura obsoleta di processori, che fu sviluppata basandosi sul concetto di parallelismo di istruzione (uso di pipeline di dati). Tutte le tecniche di miglioria apportate hannno il difetto principale di aumentare eccessivamente la complessità del microporocessore.
* **EPIC** (Explicitly Parallel Instruction Computing): tipo di architettura di microprocessori sviluppata a fine anni '90 (da Intel e HP), che aveva lo scopo di eseguire efficientemente codice parallelo senza l'ausilio di strutture HW complesse.

* ### esempi CISC e RISC  

 CISC: Intel 8080, x86 (in realtà aveva una sezione interna che traduceva le istruzioni CISC in microistruzioni simili alle RISC)
 RISC: ARM, MIPS

* ### cosa si intende con "endianness"?  

 Si intende l'ordine di memorizzazione dei **byte** nella memoria.  

* Little Endian: I byte sono memorizzati a partire dal byte MENO significativo (più popolare) (es 0x AB CD -> CD AB)
* Big Endian: I byete sono memorizzati a partire dal byte PIÙ significativo (es 0x AB CD -> AB CD)

* ### cos'è un FPGA?  

 Un **FPGA** (Field-Programmable Gate Array) è un insieme di blocchi formati, a loro volta da insiemi di porte logiche (es flip-flop) raggruppati in base alla funzionalità necessarie e sono programmabili tramite appositi "linguaggi". Sono molto più costosi di MCU o SoC, e solitamente vengono utilizzati per la costruzione di prototipi e in fase di progettazione.

* ### descrivere architettura AVR con esempi  

 Le **MCU AVR** sono state le prime ad utilizzare una memoria Flash On-Chip anzichè ROM/EEPROM esterne. Sono utilizzate nelle applicazioni embedded a bassa richiesta compitazionale, Sono diventate più popolari con la nascita di Arduino che le implementava (casa madre delle AVR: **Atmel**). L'architettura AVR32 è stata progetta per entrare in competizione con ARM per gli embedded di fascia media.
  
* ### descrivere architettura Xtensa con esempi  

 E' un **microcontrollore RISC** ad elevate prestazioni con bassi consumi. L'architettura puntava sulla flessibilità ed estendibilità e l'ISA, nonostante a 32 bit, era capace di eseguire istruzioni a 16 o 24 bit riducendo così le dimensioni del codice. (mercato audio e WiFi ESP)
  
* ### cosa si intende con SoC/demo board/eval board/validation board?

* **eval board (o demo board)**: un PCB con il chip di riferimento e i collegamenti fisichi per ad altri dispositivi HW (bus, video, rete, video, JTAG(debug)) al fine di mostrare le sue potenzialità. (es RaspberryPI ha avuto successo tramite la sua eval board) Il tutto facilita anche lo sviluppo di HW e SW basato su quel chip.
* **validation board**: board di grandi dimensioni con lo scopo di effettuare "silicon validation" ovvero una verifica per evidenziare errori di progettazione o di strutturazione del chip.

* ### storia e architettura Arduino  

 Arduino nasce in Italia come dispositivo a basso costo a scopo didattico. I progetti hardware sono stati rilasciati in modalità open SW e HW e sul mercato sono approdati molti kit per la personalizzazione. Arduino è diventato molto noto nel mercato obbistico ed amatoriale. Oltre al dispositivo è stato creato l'IDE che rendeva molto semplice l'upload degli sketch.

* ### descrivere piattaforma STM32  

 Famiglia di MCU (microcontrollori) con architetture semplici, facilmente personalizzabili e con la possibilità di lavorare facilmente con sistemi senza OS. Sono utilizzate in campi dove è richiesto di superare rigidi protocolli di certificazione come l'ambito medico, automotive e militare.

* ### descrivere piattaforma ESP8266/ESP32  

 **SoC** con un rapporto prestazioni/prezzo ottimo. È dotato di WiFi on board. Utilizzato estensivamente nell'ambito amatoriale e in quello professionale.

* ### cos'è NodeMCU?  

 **Firmware** da caricare sull'ESP8266 per poter effettuare l'esecuzione anche interattiva di script LUA. LUA è un linguaggio interpretato leggero ed efficiente che supporta paradigmi procedurali, ad oggetti e funzionali. È dinamicamente tipato e ha un garbage collector.

* ### cosa si intende con PCB?  

 Il **PCB "Printed Circuit Board"** è il circuito stampato. Solitamente è uno strato di rame ricoperto dove vengono incise le piste per le connessioni dei vari component che verrano poi saldati sulla basetta.

## Mem e I/O: tutto, in dettaglio

* ### differenze fra i vari tipi di memoria (RAM/ROM/flash/EPROM/sequenziale/casuale/SDRAM/DRAM/DDR/etc.)  

Memoria di sistema:  

* **RAM**: memoria ad accesso casuale. Tipicamente voltatile, stesso tempo per accedere a qualsiasi porzione memoria, costo alto.
* **SRAM**: Static RAM. Memorie RAM che non necessitano di refresh del dato. Molto veloce, molto costosa, ottime prestazioni energetiche e termiche. Usata solitamente nelle cache.
* **DRAM**: Dynamic RAM. Memorie RAM che necessitano di recresh del dato non necessariamente sincronizzate con il clock del sistema. Meno costose ed economiche delle SRAM.
* **SDRAM**: Syncronous Dynamic RAM. DRAM sincronizzate con il clock del sistema.
* **DDR**: tipo di SDRAM.

 Memoria di massa:  

* **ROM**: Nate come memorie non riscrivibili. I dati venivano codificati direttamente su silicio. Si sono poi evolute integrando la possibilità di riscrittura.
* **PROM**: "Programmable Read-Only Memory" memorie programmabili una sola volta tramite corrente ad alto potenziale (da qui *burn the ROM*)
* **EPROM**: "Erasabla PROM" memorie riscrivibili un numero limitato di volte (~1000). La programmazione avvene dopo aver azzerato i dati tramite l'esposizione a luce ultravioletta.
* **EEPROM**: "Elettrically Erasable PROM" memorie cancellabili e riscrivibili elettricamente un numero limitato di volte. (Veloce in lettura, ma molto lenta in scrittura) Usata solitamente in fase di bootstrap e per funzioni di base del sistema.
* **Flash Memory**: deriva dalle EEPROM ma ha la capacità di essere cancellata e riscritta a blocchi o unità inferiori e non iteramente. Un blocco può essere riscritto un numero limitato di volte. In base al tipo di collegamento tra le celle si dividono in:
  * **NAND Memory**: i transisor sono collegati in modo da collegare in serie le celle. Meno spazio su sulicio. Struttura a pagine (512-4096 Byte) riunite in blocchi da 32-128 pagine. Usate in dispositivo removibili. (es. chiavette USB, schede SD)
  * **NOR Memory**: celle collegate a massa e in parallelo alla bit line (linea di informazione). ongi cella è leggibile e scrivibile singolarmente. Occupa più spazio nelle NAND. Nate come sostituto delle EEPROM mirano ha ottimizzare la lettura (fequente) a scapito della scrittura (rara). Il codice oggetto contentuto nelle memorie NOR può essere eseguito sul posto senza essere caricato su una memoria esterna => ideale  per il boot dove la memoria potrebbe non essere accessibile
* Supporto magnetico: HDD
* Supporto ottico: CD, Blueray, ...
* Memoria ad accesso sequenziale: Molto lenta, non costosa. Usata per i sistemi di backup a nastro.

* ### cos'è e cosa fa una MMU?  

 L'**MMU (Memory Management Unit)** è un componente che si occupa della gestione della memoria effettuando:

* traduzione degli indirizzai virtuali in fisici
* protezione della memoria
* gestione della cache
  
* ### cos'è il "wear leveling"?  

 Sistema per evitare che venga riscritto sempre lo stesso blocco ed evitare il suo cessato funzionamento prematuro

* ### panoramica supporti memoria di massa nell'embedded, pregi e difetti  

 Solitamente vengono utilizzate memorie NAND per lo storage principale e le NOR per le funzioni di basso livello e il boot.

* ### quali tipi di filesystem vengono usati nell'embedded? pregi e difetti  

 Se vengono rimossi i controller che permettono di utilizzare i classici filesystem a blocchi (es FAT, NTFS, ext) è necessario utilizzare filesystem spaciali come:

* **jffs**: "Log Structured Filesystem" che lavora con le NAND, ma necessita fasi di clean agni volta che viene montato.
* **yaffs**: Simile a jffs, utilizzato dai primi produttori Android
* **ubifs**: ottimizzazioni del "wear level" e minori tempi di accesso in fase di mount.

* ### cosa si intende con XIP? pregi e difetti?  

 (A) Per **XIP** si intende "execution in place", che è una caratteristica fondamentale delle porte NOR nei processori che le supportano; sostanzialmente non c'è il bisogno di caricare il codice oggetto contenuto sulle porte NOR su un'eventuale memoria esterna.  
 Il pregio principale è rappresentato dal fatto che è ideale nelle fasi di "boot" in cui la memoria di sistema potrebbe non essere ancora accessibile.

* ### cos'è una RS232? che caratteristiche ha?  

 Protocollo standard per la comunicazione seriale. I dati sono trasmessi un bit alla volta e il valore è definito dalla differenza di potenziale rispetto la massa (GND):

* da +3V a +15V bit di valore 0.
* tra -3V e +3V segnale non valido usato per eliminare il rumore (necessità per le cablature e circuiti del passato)
* da -3V a -15V bit di valore 1.
 Spesso si usano sistemi a "3 fili" TxD (Trasmitted Data), RxD (Recived Data) e GND.
 Oggi i seriali standard sono sostituiti da i seriali TTL che utilizzano valori più bassi di differenza di potenziale. Si collegano all'USB tramite adattatori.
 I seriali sono rimasti in ambito embedded e server in quanto il terminale grafico non è sempre necessario o possibile. Nell'ambito desktop sono stati sostituiti dall'USB.

* ### descrivere NMEA0183  

 è uno standard

* sia elettrico: descrive un bus seriale RS-422 => due cavi per TxD e due per RxD risultando insensibile al rumore e arrivando a distanze maggiori
* sia di protocollo: dati trasmessi in ASCII e organizzate in stringhe dove il formato ha significato.
 Usato in ambito nautico e per il GPS.

* ### descrivere I2C  

 **I2C (Inter-Integrated Circuit)** bus seriale per comunicazioni a breve distanza. Solitamente usato all'interno dello stesso sistema.  
 È un bus "multi-master" dove i nodi possono essere:

* master: genera il serial clock (SCL - attivo-basso) che abilita l'invio di informazione e fa partire la comunicazione.
* slave: riceve il segnale di clock e risponde quando indirizzato dal master.
 Processo:

 1. Il master abilita il serial clock SCL
 2. il master disattiva il passaggio dati SDA per settare la condizione di start (SCL attivo, SDA disattivo)
 3. il master pecifica l'indirizzo dello slave di destinazione (7 bit) e 1 bit per il tipo di operazione (read/write)
 4. il master attende il segnale di ACK dello slave
 5. lo slave manda pacchetti da 8 bit seguiti da un segnale di ACK
 6. lo slave manda il segnale di fine trasmissione (stop condition) effettuando l'inverso dela condizione di start

* ### descrivere I2S  

 **I2S (Inter-Integrated circuit Sound)** è un bus per il trasporto di dati audio.  
 linee bus:

* Continuous Serial Clock (SCK): Ad ogni colpo di clock corrisponde un bit di informazione su la linea dati SD
* Word Select (WS): in base al valore selezione il canale (destri/sinistro)
* Serial Data (SD): linea dati multiplexed in base a WS e frequenza di clock

* ### descrivere SPI  

 **SPI (Serial Peripheral Interface)** è la specifica di un bus per la comunicazione seriale sincrona master/slave e non multi-master.
 Linee bus:

* SCLK (Serial CLoK): segnale attivo-alto inviato dal master che controlla lo spostamento dei vit tra master e slave
* MISO (Master Input Slave Output) attivo-alto
* MOSI (Master Output Slave Input) attivo-alto
* CS (Chip Select): seleziona quale slave abilitare per la comunicazione con il master (abilitato/disabilitato molto distante dalla trasmissione)
 Quando il clock viene abilitato dal master, vengono trasmessi i dati in seriale.
 Solitamente non vi è altra condizione di inizio/fine trasmissione.

* ### vantaggi e svantaggi del "chip select"

 (M) Per apprezzarne  la variazione dovremmo prevederne l'attivazione e la disattivazione molto prima e molto dopo allla trasmizzione. Tuttavia cosi non sarebbe permesso vedere altri segnali distintamente.

* ### descrivere CAN-BUS  

 CAN è uno standard di comunicazione master-slave (può essere anche multi-master) basato sui piccoli messaggi usato nell'ambito automotove e insustriale per la sua semplicità di implementazione e alta affidabitlità.

 1. Ogni nodo deve aspettare un tempo prestabilito per inviare il proprio messaggio
 2. Vengono rilevate potenziali collisioni tra i frame e, in base alla priorità degli ID, viene stabilito quale messaggio far arrivare.

* ### Tipi di frame

  * Data Frame: passaggio dati
  * Error Frame: invianto dai nodi che ricevono frame malformati
  * Overload Frame: inviato dai nodi che necessitano di prendere tempo tra un frame e l'altro
  * Remore Frame: inviato per sollecitare l'invio di frame

* ### descrivere Ethernet  

 Standard per le connessione con la presa RJ-45.
 Scheda di rete composta da due elementi HW che possono essere forniti da due produttori diversi:

* MAC (Media Access Control): livello 2 della pila ISO/OSI
* PHY (Physical Layer): livello 1 della pila  ISO/OSI
 Spesso il MAC si trova all'interno del SoC e il PHY all'esterno, sulla board. Ciò consente di poterlo rimuovere dopo le fasi di sviluppo se non si intende utilizzarlo.

* ### a cosa serve una linea di CLOCK? se ne può fare a meno?  

 Può servire per:

* abilitare la trasmissione di dati
* sincronizzare i dispositivi

* ### cosa si intende con GPIO? come viene usato?  

 Un **GPIO (General Purpose Input/Output)** è la rappresentazione di un pin e del suo segnale digitale transitante. L'informazione passata dipende dalle tensione transitate su di esso alta/bassa.
 Spesso è possibile scegliere se configurarli tramite software per associarli a qualche Intellectual Property o destinarlo come GPIO.

* ### pullup e pulldown

 (M) Le resistenza di pullup e pulldown sono utilizzate per leggere correttamente lo stato di un pulsante collegato ad un GPIO.  

* La resistenza è **pullup** quando si inserisce una resistenza tra il GPIO e l'alimentazione. Con questa tecnica SE il pulsante non è premuto lo stato logico è stabile a 1 in modo permanente. Lo si cambia premendo il pulsante.
* La resistenza è **pulldown** quando si inserisce una resistenza tra il GPIO e la massa

* ### cos'è il "bit banging"? vantaggi e svantaggi  

 Il **bit banging** è una tecnica per implementare comunicazioni seriali generando via software treni di impulsi in modo da emulare un circuito apposito.
 Bisogna essere sicuri che il ciclo venfa eseguito con una velocità nota e stabile altrimenti si rischano errori di trasmissione.  
 Vantaggi:  

* economico
* flessibile rispetto al protocollo di comunicazione. Basa aggiornamenti software per introdurre nuovi protocolli.
 Svantaggi
* minor robustezza: la stabilità è influenzata da costa viene eseguito sull'hardware. Se arrivano tanti input si richia di perdere dati.

* ### cos'è il JTAG?  

 Il **JTAG (Join Test Action Group)** è uno strumento per il testing e la validazione hardware e software di basso livello (es driver) delle board.
 Semplificando è come una liena di celle interconnesse tutte intorno alla logica I/O del chip. Le celle possono raccogliere le infromrazione sullo stato complessivo di tutti i registri e della memoria permettendo un controllo completo su quello che viene eseguito all'interno dell'elaboratore. Viene gestrito tramite connettori JTAG. Sono solitamente rimossi per specifiche di sicurezza e per evitare reverse ingineering sulla board di produzione.

* ### perchè negli alimentatori switching non riesco a notare le oscillazioni di corrente?

## S.O.: overview

* ### cos'è un S.O.?  

 (M) SW di base per la gestione dell HW e del SW, garantendo servizi e funzionalità all'utente.

* ### descrivere architettura monolitica/microkernel/etc  

 struttura kernel:

* **monolitica**: il nucleo comprende driver, strutture di multiplexing dell'hw e servizio per la gestione dei processi e della comunicazione (es. linux, freeBSD)
* **microkernel**:  kernel con il minor codice possibile eseguito in modalità supervisore. Gli altri componenti vengono estratti in moduli (es driver) comunicano con il nucleo tramite componenti software detti "server".
  * Vantaggi: sicurezze e robustezza.
  * Svantaggi: complessità di sviluppo e rigidità comportamenteale compessiva (es freeRTOS)
* ibridi (es kernel di mecOS)

* ### cosa si intende con "preemptive multitasking"?  

 Multitasking gestito tramite il rilascio forzato della CPU da parte del task in esecuzione.

* ### cos'è un filesystem?  

 È un astrazione delle informazioni nei dispositivi fisici e del loro trasferimento.
 Composto da:

* strutture dati: per organizzare dati (i blocchi dei file) e metadati
* metodi di accesso: mapping delle chiamate dei processi (es: open(), read(), write(), ...) nelle strutture dati e come sono implementati

* ### cos'è il "root filesystem"?  

 il root filesystem è la partizione del filesystem consente gli elementi necessari al boot del sistema (libc, shell o altro interprete di comandi, altri tool ...).
 Viene convenzionalmente montata come primo nodo dell'albero delle cartelle "/".

* ### cos'è un "init system"?  

 Insieme degli strumenti software (incluso il processo init) e le configurazioni che permettono l'avvio di tutti gli applicativi e i demoni del sistema

* ### cos'è una shell?  

 È un software che permette l'interpretazione di comanti definiti in un proprio linguaggio (di "scripting") durante l'esecuzione.

* ### cos'è e cosa serve un bootloader?  

 Programma necessario per avviare il sistema. Carica kernel e parametri d'avvio prelevandoli dallo storage.  
 Se presenti il BIOS/UEFI (firmware in flash o eeprom) saranno questi ad effettuare parte delle configurazioni (es clock, rilevamento storage, inizializzazione dispositivi di comunicazione, GPU, ...) semplificando il lavoro del bootloader.

## Linux: overview

* ### cos'è una toolchain?  

 strumenti per la compilazione del codice sogente (librerie, linker, compilatore, debugger).  
 La toolchain è compilata per l'architettura su cui lavora, quindi non sono intercambiabili.

* nativa: compilata da un sistema con la medesima architettura di quella target (comune in ambienti desktop)
* cross-toolchain: compilata da un sisema con una architettura differente produce binari per architetture differenti (comune in ambienti embedded)

* ### cos'è un build system? citarne qualcuno e descrivere  

 L'insieme dei software per effettuare la compilazione dei pacchetti del sistema embedded finale.  
 es

* Buildroot: per generare OS Linux per dispositivi embedded. Può generare: cross-toolchain, root filesystem, immagini kernel e dei vari bootloader.
* Open embedded: basato su layer conteneti recipes che rappresentano in forma testuale i parametri e le istruzioni che compilare i vari elementi del sistema.

* ### cosa sono le partizioni? che tipi puoi citare e descrivere?

 (M) Le **partizioni** sono porzioni di memoria utilizzate dal SO per il boot (partizione di boot) contenendo tutti i file necessari all'avvio e il kernel. Vi sono poi la partizione di rott (la home dell'utente root) e la partizione di SWAP per lo swapping delle pagine.  
 Le partizioni sono dividono in

* **Primarie**: (al massimo 4)  contiene il SO e i dati accessibili dalla partizione quando è attiva
* **Logiche**: puo contenere dati del SO o di altro tipo
* **Estese**: (al massimo 1) nata con lo scopo di ovviare alla limitazione delle 4 partizioni primarie

## FreeRTOS: overview

* ### descrivere cos'è FreeRTOS e come viene utilizzato  

 **FreeRTOS (Free Real Time Operating System)** è un sistema operativo semplice e veloce che ha lo scopo di offrire prestazioni real-time.
 Non comprende driver nè API complesse ma solo il necessario per la gestrione di thread, task, mutex, semafori e timer.
 Un prodotto finale FreeRTOS unisce il codice sorgente dei sistema a  quello per il supporto dell MCU relativa e al codice dell'applicazione.

* ### cos'è un task in FreeRTOS?  

 I task sono dei programmi all'interno del programma principali (ricordano i processi). Effettivamente sono funzioni conteneti un loop infinito nel quale sono presenti le istruzioni di funzionamento.  
 Può essere eseguito un solo task alla volta. Possono avere stati diversi come:

* Running: in esecuzione
* Ready: eseguibile da un momento all'altro
* Suspended: esplicitamente fermato e in attesa di esplicita riattivazioni
* Blocked: fermato e in attesa di un evento

* ### cos'è e a cosa serve un semaforo?  

 Sistema per la gerstione della concorrenza.

## Arduino: tutto, in dettaglio

* origine di Arduino  

* ### pro e contro della piattaforma  

 Vantaggi:

* licenze libere
* architettura KISS sia hw (processore 8bit, poca ram/rom, no MMU, no OS) che sw (linguaggio semplice e processi di sviluppo nascosa dall'intefaccia utente)
* linguaggio di programmazione con sintassi simile a C e Java
* molte librerie  

Svantaggi:  

* prodotti a basso costo con qualità basse
* presenza di troppo librerie alternative

* ### spiegare meccanismo di boot di un Arduino (classico: UNO)  

 Durante l'accessione o a seguito del reset, il bootloader controlla il pin di ricezione seriale per qualche secondo.
 Se riceve una sequanza di byte predefinita allora il bootloader risponde con un ACK e l'IDE invia il codice e lo scrive sulla flash.
 Altrimenti esegue il codice già presente sulla flash.

* ### spiegare il funzionamento di setup() e loop()  

 (M)  

* setup() è una funzione eseguita una sola volta durante quando lo sketch inizia quindi al powerup o reset della board.
* loop() è una funzione eseguita appunto in loop in maniera indefinita.

* ### panoramica tipi di dato  

* boolean 1 Byte
* char 1 Byte
* unsigned char 1 Byte
* byte 1 byte
* int 16 bit = 2 Byte
* unsigned int
* word = int
* long 32 bit = 4 Byte
* unsigned long
* short 16 bit = 2 Byte
* float 32 bit = 4 Byte
* double 64 bit = 8 Byte
* array: vettori di variabili dello stesso tipo accedibili tramite la posizione (attenzione all'index overflow non controllato)
* string: array di char
* String (oggetto)

* panoramica operatori
* aritmetici
* confronto
* booleani: && || !
* puntatori
* manipolaizone dei bit: shift:<< XOR:^ ...
* composti: ++ += *= -- -=

* ### spiegare direttive compilatore  

 le direttive al precompilatore:

* #"include: il precompilatore le sostituisce con il reale contenduto del file incluso prima di passare il tutto al compilatore
* #"define: il precompilarore sostituisce nel codice tutti le variabili definire con il loro reale contenuto

* ### panoramica costrutti di controllo di flusso  

* if, for, while ...

* ### cos'è una funzione?  

 È un meccanismo per associare un insieme di istruzioni ad una signature in modo da evitare ripetizioni.

* ### descrivere il meccanismo di gestione degli interrupt facendo esempi di codice  

 si può adibire un pin a segnale di interrupt associato ad una funzione. Nel caso in cui si verifichi l'evento definito su quel pin (es arduino: LOW, HIGH, CHANGE, RISING, FALLING) viene stoppata l'esecuzione del loop ed eseguita la funzione designata.

 ```c
 attachInterrupt(digitalPinToInterrupt(pin), ISR, mode)
 ```

 Si possono anche definire sezioni critiche iniziando con la disabilitazione degli interrupt con noInterrupts() e la riabilitazione alla fine interrupts()

* ### spiegare differenza fra GPIO digitale e analogico  

* **digitali**: accettano 2 valori: 1 HIGH, 0 LOW
* **analogici**: gestiscono diversi livelli di tensione (256 o 1024) tra 0V e 5V

* ### descrivere funzionalità del piedino AREF/VIN/D0-1-2-...-N/GND/A0-1-2-...-N/RX/TX/SDA/SCL/... di Arduino/Wemos/

* PWD (Pulse With Modulation): è possibile fornire una tenzione variabile
* AREF (Analog REFerence): pin per fornire in input la tensione da usare come riferimento per l'analog input

## Rete: overview (tranne i temi *embedded* come MQTT)

* ### spiegare livelli ISO/OSI e TCP/IP  

* Standard ISO-OSI: regolamenta la struttura globale del sottosistema completo di comunicazione. ISO adotta un modello a strati ciascuno dei quali esegue una funzione predefinita.  
  Gli strati dell'ISO/OSI possono essere separati in due categorie
  * Media layer: funzioni dipendenti dalla rete
  * Host layer: funzioni orientate applicazione

  Livelli:

  * Applicazione: fornisce all'interfaccia verso l'utente una gamma di servizi distribuiti sulla rete. Protocolli: HTTP, SMTP, FTP, SNMP, DNS…
  * Presentazione: riguarda la rappresentazione dei dati durante il trasferimento. Negozia e seleziona la rappresentazione di trasferimento appropriata eseguendo la necessaria conversione
  * Sessione: consente a due entita di organizzare e sincronizzare il loro dialogo. Responsabile della creazione e terminazione di un canale di comunicazione
  * Trasporto: funge da interfaccia tra gli stati superiori e gli altri
   ○ Fornisce un sistema di trasferimento dei messaggi indipendente dal tipo di rete
   ○ Controllo dell'integrita
   ○ Si occupa di riordinare i pacchetti
   ○ Garantisce il trasporto senza errori, in sequenza, nessuna perdita, nessun duplicato, qualita del servizio
   ○ Protocolli: TCP, UDP
  * Rete: è responsabile dell'apertura e della chiusura di una connessione
    * Offre l'inoltro sulla rete, l'indirizzamento e il controllo del flusso
    * Si occupa di armonizzare le diverse reti
  * Data link: si basa sulla connessione fisica fornita dal tipo di rete per garantire un sistema affidabile di trasferimento
    * Raggruppa i bit ricevuti dallo strato superiore e li spedisce in frame
    * Permette di individuare gli errori e dell'eventuale ritrasmissione
    * Permette di connettersi e recapitare dati a un nodo adiacente nella rete
  * Fisico

* TCP/IP: definisce solo 4 dei livelli dell'ISO OSI
  * Livello network (fisico+data link)
  * Livello internet (rete)
  * Livello trasporto
  * Livello applicativo (sessione + presentazione + applicazione)

* ### citare protocolli "normali" e "IoT", differenze, pro e contro

* **MQTT (Message Queuing Telemetry Transport)**: protocollo del tipo publisher/subscriver (obesrver/observee) basato su messaggi. I messaggi fomrati da *topic* (parole separate da "/") e *payload* (stringa UTF-8) sono inviati da un nodo *client*  ad un *broker* al quale sono connessi. Il *broker* broadcasta il messaggio a tutti i nodi che si sono iscritti a quel *topic*. I nodi che ricevono il messaggio eseguiranno una funzione callback definita da loro.
 Funzioni da nodo connesso a broker

 ```c++
 Subscribe(String subTopic, Function callback)
 
 Publish(String topic, String message)
 ```

 IoT  

* LoRa (LOng RAnge): standard a livello fisico di rete wireless che definisce le modalità di trasmissione (modulazione) e le frequenze utilizzate.
* LoRaWAN (LOng RAnge Wild Area Network): standard che definisce lo strato MAC cioè il protocollo di trasmissione, indirizzamento, crittografia, formato dati, .. Lo standard mira a sostituire quello iFi per la supportare la comunicazione tra sensori e gatway (che instradano verso nodi terminali o verso reti tradizionali) in contesti a basso consumo e lunghe portare.  
Vantaggi:
* conunicazioni bidirezionali
* buona robustezza alle interferenze
* consumi ridotti
* lungo raggio (anche Km)
* crittografia
* funzionamento indoor/outdoor
* bassi costi
 nodi di 3 classi:
* Classe A: nodi bidirezionali che possono ricevere messaggi dopo aver inviato un messaggio
* Casse B: nodi bidirezionali come A in clui si possono anche definire finestre temporali di ricezione (necessitano sincronizzazione tra sorgente e ricevente)
* Classe C: nodi bidirezionali a ricezione continua (massimo consumo)