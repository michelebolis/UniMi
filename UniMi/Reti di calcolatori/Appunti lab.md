CISCO Packet Tracer è uno strumento per imparare a configurare reti

Quest'anno ci sono i seminari tecnici. All'esame c è la documentazione

Obiettivi Packet Tracer:
- Calcolare parametri per subnetting
- Configurare switch e router per servizi fondamentali

Obiettivi Java: (sono 6 classi)
- apprendere a progettare considerando protocollo e struttura PDU, programmazione asincrona e concorrente, gestione errori, prestazioni client

Always show port labels 
Miscellaneus --> auto clear event list


Spanning Tree Protocol: 

Bridge collegano SOLO reti omogenee con stesse spec

Noi usiamo SOLO PT-Router o PT-Empty
CE Copper Ethernet 10Mb
CFE Copper Fast Ethernet 100Mb
CGE 1G
FFE Fiber Fast Ethernet 100 Mb
FGE 1Gb

PT-Empty vuol dire che la struttura è vuota

Per le connessioni
Copper Straight: colori nello stesso ordine da entrambi i terminali. Tra apparati diversi in funzione del livello che implementano
Copper Cross: l'ordine agli estremi è diverso. Servono per collegare apparati uguali
Fiber

es hub, bridge e switch sono allo stesso livello perche il livello 1 e 2 di OSI sono implementati nella scheda di rete
nella realta alcuni device sono auto crossing

ATT connection automatico NON funziona spesso

Triangolo verde: pronto
Cerchio arancione: si sta configurando, imparando

---

command prompt: ping è un comando di shell che ci da l interfaccia per una funzione del protocollo di rete 
www.unimi.it è un alias

content delivery network: specificare il contenuto che vogliamo visualizzare

nella rete devo esplicitamente dire con chi devo parlare
i sistemi distribuiti sono costruiti sopra la rete, nascondendola
Applicazioni non devono quindi specificare con chi devo parlare

Appenda accendo un interfaccia di rete, il dispositivo manda un segnale di portante per segnalare che il dispositivo è accesso

freccia rossa verso il basso --> cavo sbagliato

FastEthernet e Ethernet vanno bene perche sono protocolli compatibili

Hub c è solo un numero nel nome
Switch invece ha 2 numeri nel nome in quanto il primo numero è della scheda mentre il secondo l identificatore della porta sulla scheda
Si contano le interfacce da dx a sx

il router implementa il livello 3: il router esigono che ognuno delle interfacce sia su una rete differente. 
il router resta rosso perche gli dobbiamo dire esplicitamente di usare l interfaccia: config --> portStatus on

---

In automatico mettendo l indirizzo nel router, viene messo la netmask che equivale ad una classe C
Nel PX -> Setting -> Default gateway deve essere settato all indirizzo del router

Simulazione : mi permette di visualizzare gli eventi dei vari protocolli
ICMP affianca IP per il servizio ping
per fare la simulazione devo prima fare un ping (icona busta chiusa tra pc e server)

Ci sono in realta due buste:
- Uno ICMP 
- Uno ARP

cliccando sulla busta ho i dettagli della PDU Protocol Data Unit
in OSI model posso vedere ogni passaggio che viene effettuato

Croce rossa sulla busta perche il ruoter non sa dove sia (guardare ARP table usando la lente di ingrandimento sul router)
pero mentre il router ha imparato l indirizzo del server, ICMP è stato buttato
Quando faccio il ping, il primo fallisce

![[Pasted image 20231027143014.png]]

simulazione di 2 ping contemporanei tra due coppie di computer collegati da uno hub tra i 4 dispositivi

dominio di broadcast: SE indirizzo a livello Ethernet, tutti gli endsystem lo ricevono
dominio di collisione: 

Collisione tra i due ping nell hub

Usando 4 bridge con i 4 endsystem e un hub collegato ai 4 bridge, viene fatta pulizia evitando collisioni

![[Pasted image 20231027150227.png]]

Quando un dispositivo si accende, viene fatta un ARP request sul proprio indirizzo per verificare l unicita del proprio ip e per mettere nelle ARP table degli altri dispositivi la mia corrispondenza ip-MAC

ATT SE due PC hanno lo stesso IP, il ping ha successo 
![[Pasted image 20231027155658.png]]

1 switch = bridge per ogni endsystem + 1 hub
![[Pasted image 20231027155933.png]]

Protocollo di Spanning Tree (livello 2): durante la fase di leaning dei bridge, viene imposta una struttura ad albero capiscono la topologia tanto da tagliare i loop 
Un triangolo di bridge non fa diventare tutti i cavi verdi, ma volontariamente viene disattivata un interfaccia di un bridge per evitare il loop

La stessa cosa accade anche con gli switch

Posso mettere lo ip in due reti diverse e se poi collego gli switch non si accorge dell errore
Quando provo la simulazione tra i pc con i due indirizzi uguali, il ping funziona ma perche arriva a se stesso

NON posso usare un solo cavo tra due switch che collegano pc di due vlan, devo avere un cavo collegato tra gli switch per ogni VLAN
Il nome delle VLAN non è solo un colore, ma con un numero 
Nello switch --> config --> VLAN database

---

CLI di Cisco
Noi lavoreremo senza password
modalita 
- privilegiata/root
- utente

Modalita privilegiata SE termina col segno \#
Modalità utente SE termina col segno >

se devi fare qualcosa come root, fai quello che devi fare e poi torna utente normale

comand ?: permette di avere i comandi possibili
comando clean: 
comando connect: servizio connection-oriented dice che i dati inviati alla destinazione devono arrivare in ordine 
comando disconnect fa il contrario di connect


comando telnet: permette di collegarsi ad un terminale remoto e di operare come se stessimo lavorando in presenza
Apre una shell con il terminale i cui comandi vengono ridirezionati verso il terminale reale 
ATT non è sicura perche tutto viaggia in chiaro

Bisognerebbe usare SSH 

comando traceroute: interfaccia del protocollo ICMP (lavora insieme a IP che notifica condizioni di errore), traccia il percorso verso un alias di un indirizzo per un massimo di 30 hop

\* in traceroute vuol dire che ci siano degli errori o per nascondere il route se i dispositivi di rete sono stati settati per cio

comando show: 
- arp table
- interfaces (le da tutte)
	- interfaces tipo nome es (interfaces fastethernet 1/1)
- mac-address-table

comando enable: passa nella modalita privilegiata
- copia, cancellazione di un file 
- disable o exit per uscire dal root

La configurazione da GUI in realta è in RAM, quindi se resetto il device perdo tutto
Serve usare il comando write per far diventare la configurazione di boot


documento su ariel



nslookup aliasIndirzzo ci restituisce l indirizzo 

CTRL SHIFT 6 per fermare CLI


Come si configura uno switch via CLI
- Configurare il VLAN database
comando vlan database è deprecato quindi 
Si usa invece configure 
Si puo eseguire un comando non disponibile nel set di comando attuali con do ...
per tornare a una situazione precedente dopo aver fatto un comando, no ...

vlan 100 entro in config-vlan
name rosa100

- Configurare la VLAN dell interface
in modalita config, interface nomeInterfaccia 
ora siamo in config-if

switchport mode access vlan 100
in realta access come mode di default

switchport trunk allowed vlan add 100


