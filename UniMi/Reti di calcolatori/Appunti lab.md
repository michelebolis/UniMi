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

---

IPv4
32bit unsigned long con dotted notation

ogni ottetto non puo superare 255

Modo di assegnazione indirizzi
- classi vs CIDR
- subnetting

Class-based
indirizzo base della rete: hostID = 0
indirizzo che riguarda la rete locale: netID = 0
tutti 1: broadcast sulla rete
broadcast sulla rete destinataria: hostID tutti 1

classe A 
da 1.0.0.0
a 127.255.255.255

Classe B
da 128.0.0.0
a 191.255.255.255

Classe C
da 192.0.0.0
a 223.255.255.255


Usando x bit per il netID avro 32-x bit per l hostID
MA cosi per percorrere la tabella di instradamento ci impiegherei in media 2^32/2 = 2^31

tutti bit 1 a sx e tutti bit 0 a dx con in mezzo un punto di taglio dove inizia l hostID

l indirizzi destinazione AND bit a bit con la netmask: cancello bit a destra trovando il netID
tra i flag dello header c è anche un flag per nascondere amministrativamente una rotta, ICMP non ritorna niente ma \*

Ricorda
1111111
128 64 32 16 8 4 2 1
es
127.128.129.192
01111111.1000000.1000001.11000000

218.160.179.60
11011010.1010000.10110011.00111100

20.148.67.123
00010100.10010100.01000011.01111011

87.194.104.77
01010111.11000010.01101000.01001101

01011011.01110110.00101111.10011111
64+16+8+2+1 = 91
64+32+16+4+2 = 118
32+8+4+2+1 = 47
128+16+8+4+2+1 = 159

10011011.00011011.01010001.00100010
128+16+8+2+1 = 155
16+8+2+1 = 27
64+16+1 = 81
32+2= 34

Indirizzo broadcast, netmask e 2 indirizzi accettabili
15.0.0.0 Classe A -> 8
00001111.00000000.00000000.00000000
Netmask
11111111.00000000.00000000.00000000
255.0.0.0
Broadcast
00001111.11111111.11111111.11111111
15.255.255.255
2 indirizzi accettabili (minimo; massimo)
00001111.00000000.00000000.00000001 MIN 15.0.0.1
00001111.11111111.11111111.11111110 MAX 15.255.255.254

137.149.0.0 Classe B -> 16
10001001.10010101.00000000.00000000
Netmask
11111111.11111111.00000000.00000000
Broadcast
10001001.10010101.11111111.11111111
137.149.255.255
2 indirizzi accettabili (minimo; massimo)
10001001.10010101.00000000.00000001 MIN 137.149.0.1
10001001.10010101.11111111.11111110 MAX 137.149.255.254

215.151.59.0 Classe C -> 24
11010011.10010111.00111011.00000000
Netmask
11111111.11111111.11111111.00000000
Broadcast
11010011.10010111.00111011.11111111
215.151.59.255
2 indirizzi accettabili (minimo; massimo)
11010011.10010111.00111011.00000001 MIN 215.151.59.1
11010011.10010111.00111011.11111110 MAX 215.151.59.254

---

lezione 10/11

---

Per controllare che i calcoli siano corretti, converto l ultimo ottetto del min e del max range di indirizzi
per essere corretto devono avere i numeri di netid e subnetid uguali tranne l ultimo

in caso errato il subnetid sara diverso
Il router se il pacchetto non è nei subnet, dara un segnale di errore

Il campo CRC è il resto della divisione tra due polinomi rappresentanti dai dati/polinomioComunePerCRC 
10110 = $x^4 + x^2 + x$
SE i due resti non sono uguali, allora c è stata un errore


Proprieta aritmetica binaria
- Allineamento
Una rete di dimensione 2^n puo iniziare solo a intervalli regolari multipli di 2^n, cioe a posizioni pari a k * 2^n, 
Il primo indirizzo disponibile nello host addres range deve essere composto da tutti 0 negli ultimi n bit per qualsiasi sottorete

es n = 64 (taglia è il massimo numero di dispositivi)
puo iniziare a 0, 64, 128, 192
n = 32
puo iniziare a 0, 32, 64, 96, 128, 160, 192, 224


indirizzo base: pari
indirizzo broadcast: dispari


Alternativa: euristica
Dandomi l indirizzo base, mi sta anche dando l indirizzo massimo
da 011 | 00000 = 96 
a 011 | 11111 = 127

Si inizia dalla subnet piu grande fino alla piu piccola
S2 con 14 apparati + broadcast + base = 16 indirizzi -> 4 bit (n=16)
base rete 192.168.20.96/28
netmask 255.255.255.240
broadcast 192.168.20.11
range 192.168.20.97 - 192.168.20.110
97 = 011 | 0 | 0001
110 = 011 | 0 | 1110

S1 con 5 apparati + broadcast + base = 7 indirizzi -> 3 bit (n=8)
Base 192.168.20.112/29
netmask 255.255.255.248
Broadcast 192.168.20.119
range 192.168.20.113 -  192.168.20.118
113 = 011 | 10 | 001
118 = 011 | 10 | 110

OSS S2 e S1 non sono sovrapponibili, come le classi di indirizzi infatti S2 ha solo 1 bit per il subnet mentre S2 ha 2 bit

...

ATT seguire la tecnica che chiede all esame in quanto seno le reti non vanno bene 

es
indirizzo base 10.11.260.0/24
A 25 host
G 14 host
K 28 host
M 9 host
R 58 host

Usare la regola dell allineamento nell ordine alfabetico
- A 25+1+1 = 27 indirizzi -> (bit=5, n=32)
base 10.11.260.0/
broadcast 10.11.260.27
range 10.11.260.1 - 10.11.260.26
1 = 00000001
26 = 00011010

- G 14+1+1 = 16 indirizzi -> (bit=4, n=16)
base 10.11.260.32/
broadcast 10.11.260.48
range 10.11.260.33 - 10.11.260.47
33 = 00010001
47 = 00010111

- K 28+1+1 = 30 indirizzi -> (bit=5, n=32)
base 10.11.260.64
broadcast 10.11.260.94
range 10.11.260.65 - 10.11.260.93
65 = 01000001
93 = 01011101

- M 9+1+1 = 11 indirizzi -> (bit=4, n=16)
base 10.11.260.96
broadcast 10.11.260.107
range 10.11.260.97 - 10.11.260.106
97 = 
106 = 

- R 58+1+1 = 60 indirizzi -> (bit=6, n=64)
base 10.11.260.128
broadcast 10.11.260.188
range 10.11.260.129 - 10.11.260.187
129 = 10000001
187 = 