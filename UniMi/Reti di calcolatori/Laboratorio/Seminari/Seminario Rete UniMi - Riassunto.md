GARR B3, B5, B6

Indispensabile l'infrastruttura fisica: noleggio delle fibre ottiche spente (che prendono in gare (aste))

## Rete precedente
- Fibre ottiche spente aggiudicate nel 14 fino al 23 sviluppo fino a 640km per un totale di 2000km
- 4 sedi principali in doppia via, 2 campus in doppia via (Sesto e via mercalli)
- Criterio geografico e ambientale (uniche dotate di disaster recovery, 1 datacenter (anche DNS) in Noto e 1 un Colombo) per scegliere le sedi principali 
- 27 sedi in singola via con almeno due coppie (singola via non considera ridondanza fisica)
- 5 sedi in singola via con singola coppia

Veniva utilizzata una `struttura a triangolo`: dalla sedi alle due sedi principali formando un triangolo
4 sedi principali magliate tra loro con doppio collegamento

Anello da 144 fibre dedicato con diramazioni verso le sedi da minimo 24 fibre anche se ne usavano 4, perché `la parte onerosa è la posa del cavo NON il mantenimento` 
Le tratte di una stessa sede erano ritagliate in modo differenziato sulla struttura con almeno nel 75% (eccezione crema e lodi perché )

in 9 anni 2 volte sono caduti il 50% delle linee (rottura dell anello e incendio in un bar random)

## 1. Infrastruttura logica
NON è una rete carrier (indipendente) cioè una rete di reti MA è `enterpraise una rete unica estesa`. Per far funzionare una rete unica bisogna usare protocolli specifici
Connettività basata su collegamenti punto punto illuminata in tecnologia 10Gb Ethernet
I collegamenti tra i 4 core a 2x10Gb 
I collegamenti verso i centri stella con doppio link 10Gb
Per ottimizzare i costi, si è messo un apparato in ogni sede con link geogradici e porte edge di CS
La ridondanza era garantita dall'infrastruttura fisica MA era anche limitata (nelle sedi in singola via)

## 2. Connettività locale
Distribuzione verticale (verso i vari piani) in fibra 
Distribuzione orizzontale in rame (CAT 7 MA ci sono sedi anche in CAT 5)
Sedi di medie dimensioni 
- Apparato di centro Stella L3 modulare che faceva connettivita WAN e distribuzione rame
- Apparati L2 alla distribuzione con doppio link fibra 1Gb o 10Gb aggregato (con protocollo LACP in modo che sia dinamico, se ho bisogno di aggiungere o togliere dei canali, posso) con Centro Stella
Sedi piccole
- Apparato di centro Stella L3 fixed (magari un unica unita) che faceva connettività WAN e distribuzione rame
- Apparato L2 alla distribuzione con singolo (se non c è disponibilità di fibra) o doppio link gigabit sul CS


## 3. Infrastrutture logica locale
`VLAN configurate localmente` (VLAN 50 di informatica, VLAN 50 di matematica...)
Ragionata geograficamente, la numerazione non era coerente, infatti era scelta con algoritmi locali (es 2000 tutte le VLAN delle stampanti)
Vantaggi: semplice dal punto di vista locale
Usi locali: Media Gateway fonia, VOIP

`VLAN anche gestite globalmente` in quanto alcune tipologie di oggetti devono essere gestiti globalmente (es servizi generali dell'ateneo: access point Wireless, Unicloud)
Unicloud ha 2 VLAN definite per ogni aula: 1 per le macchine fisiche e 1 per le macchine virtuali
Problema: trasporto VLAN a livello geografico o ti basi sulla Spanning Tree o fai un percorso fisso o usi protocollo livello superiore con tunneling 

## 4. Livello IP e routing
2 tipi di reti
- Reti pubbliche
Rete di classe B
Rete pubblica per indirizzare gli indirizzamenti privati es PC del docente nell'ufficio
Vantaggio: SE faccio qualcosa con l indirizzo pubblico, è facile da tracciare chi e quando viene usato. 
I server invece tipicamente danno indirizzi privati. 

`NAT si cerca di evitarlo`, e di farlo eventualmente statico in modo da avere una mappatura statica e coerente della history

Indirizzi 10.0.0.0/16 usato per i link punto-punto L3

Indirizzi 172.16.31.0/16 utilizzate per servizi gestiti centralemnte (es Unicloud)

- Reti private 192.168.0.0/16 in cui ci sono server (quando hanno bisogno di uscire NO NAT MA proxy in modo che all esterno non sapranno mai l IP reale del server)
Se ho un server web, non pubblico il server intero, ma la porta con cui espongo il servizio
Secure by design: ci sono firewall PaloAlto

## 5. Routing e instradamento
`Protocollo di routing primario OSPF`
indirizzamento diviso in backbone e singole sedi in modo da sapere gia la sede
Metriche per l ottimizzazione della convergenza con peso 1 = 40 Gb (NON 10 di standard)
in alcuni casi venivano dati pesi fissi soprattutto per datacenter e in citta studi (perche complesso)
Vantaggio OSPF: `multipath forwarding` posso trasferire tra due punti su piu canali di trasmissione 

`Sottostrutture con rotte statiche e/o RIP`
traffico a flusso per fare forwarding dei servizi
traffico a pacchetto per traffico pesante
avrò quindi nella tabella di instradamento sia info arrivate sia da OSPF che RIP: impossibile fisicamente che dispositivi di una rete (es di informatica) possano raggiungere il server web di un altra rete protetta (perché non sa neanche che esiste). 
RIP gestisce solo in base alla distanza non alla velocita il che va bene se ci sono link paretetici (stessa velocita) quindi instradamento ottimizzato
Vantaggi: garantiscono connettività in caso di blocco o guasto alla sovrastruttura OSPF (limitati negli LSA, cioè nella compilazione della tabella di routing)
Sui router di bordo si usa black hole, tutto cio che è una rete inesistente viene buttato
Gestiva delle zone a instradamento privato


## Rete di adesso in evoluzione
Problemi: cambiare qualcosa in produzione, non posso mai spegnere niente
Occasione per il cambiamento è stato la `scadenza della concessione delle fibre`
`Struttura pentangolare`, 5 poli dell università: Mind, citta studi, centro, lodi, edolo 
sviluppo fino a 1880km su 150 tratte ciascuna formata da una coppia (gia presenti tratte di raccordo per poi migrare da sacco a MIND)
3 sedi core (limite: ci deve essere presente un gruppo elettrogeno)

Struttura a triangoli
...

Connettivita Geografica
`ORA rete geografica puramente di L2`: idea è da` tramutare rete basata sulla posizione geografica a rete basata sull'utilizzo della rete` (es dip info, dip agraria) per esempio per dip in piu aree geografiche
SPB trasporta qualsiasi oggetto END-END lavorando ai bordi etichettando (come MPLS)

Apparati L2: SPB con firmware FabricEngine
Vengono utilizzati in tutte le sedi
SOLO 4 tipi di switch: modello Ryanair permette di diminuire i costi, ma rischio del problema generalizzato 
Aumento del throughtput nei link
- collegamenti tra le sedi di core: 100Gb (in realta 4 canali da 25Gb)
- collegamenti tra core e sedi: 25Gb (alcune tratte >400km a 10Gb ZR (tecnologia che raggiunge anche 80km) )
- A breve tra core e campus a 40Gb (in realta sono 4 canali a 10Gb)
SE 1Gb il RTT 0,5ms, su 10Gb è di 0,025ms
Diminuisce Jitter e RTT

VSP7400 con 4Tbps di capacita, una latenza di 800ns, forwarding rate di 2 Miliardi di pacchetti al secondo
48 porte SFP 
8 port QSFP
Sono usate nelle sedi core e nelle sedi campus

Apparati L3: router con firmware SwitchEngine
SOLO 3 apparati nelle 3 sedi di core
Collegati all'infrastruttura 2x100Gb 
Vantaggi: convergenza delle tabelle di routing immediata e è possibile posizionare dei firewall nord-sud e est-ovest 

X870 ...,
Possono gestire tabelle MAC di 136k, e ARP table di 192k entry (ARP > MAC, perche dato un MAC potrei associagli piu IP) (Rete IPv6 da /56 MA `servizi non maturi, cioe ancora in IPv4`)
Sono usate SOLO nelle sedi core

Eduroam fa cagare perché `le macchine che fanno NAT tra reti interni e esterne hanno delle tabelle ARP di 16k MA nei momenti di punti ci sono almeno 20/30k`. La tabella continua a riaggiornarsi e quindi deve mandare un ARP request in broadcast, quindi ci sono moltissimi messaggi in broadcast

Sedi
...


Costo nelle sedi è un po' alto
Vantaggio: non interrompo mai la rete anche quando aggiorno il firmware 
Nelle macchine delle sedi ci sono anche porte in rame 

Sede Fabric Extend (es Edolo o sedi temporanee mentre altre vengono ristrutturate)
`Dove non posso posare la fibra, compro un collegamento di tipo commerciale `
Difetto macchine: hanno un MTU inferiore (900) rispetto ai 1500 che quindi necessitano di fare frammentazione e deframmentazione che NON puo essere fatto in HW, quindi è necessario lavorare sulla CPU
macchine CPU based che creano un tunneling 

Nelle sedi di core sugli switch faccio girare VM per la terminazione delle sedi fabric


Connettività locale
SOLO apparati L2
...

Distribuzione geografica VLAN
`Basata L2 in multipath tramite SPB`
Semplicità di configurazione con un sistema di labeling che utilizza label a 24 bit
Gestione eventuali VLAN duplicati dando lo stesso label a ID diversi in diverse sedi (per trasportare il backend di CTU in citta studi)
SE tra L2 e L3 voglio un firewall, mettere il firewall sul link facendo ispection sul cavo

Inoltro e gestione delle interconnessioni completamente automatico 
Supporto di IEEE 802.3ad anche sul link full fabric. SE posso fare aggregazione è meglio e ci da ridondanza


Livello IP e routing
`Routing concentrato nelle tre sedi core`
...

Utilizzo di VRRP estensivo in modo che sia tutto ridondato 2 volte a livello geografico
...
Possibilita di controllo tramite Firewall del ...



Migrazione in produzione 
Connettivita geografica
Migrazione core
1. Installazione degli apparati fabri
2. ...
3. ...
4. ...
5. aumento del peso OSPF del link in migrazione cosicche tutto il traffico va sull altro link
6. Spostiamo la fibra spenta da L3 ad apparato fabric
7. ...
8. riconfigurazione del peso OSPF

Migrazione VLAN
1. configurazione del trasporto VLAN su apparato fabric
2. connessione degli apparati edge al nuovo apparato fabric (comporta interruzione di qualche secondo sull'edge)
3. trasporto VLAN verso i nuovi router

Migrazione IP 
...

