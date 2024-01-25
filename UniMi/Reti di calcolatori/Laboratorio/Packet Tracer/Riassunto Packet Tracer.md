 ## PT - Introduzione
Cablature:
- Copper Straight: servono per collegare apparati diversi in funzione del livello che implementano
- Copper Cross: servono per collegare apparati uguali

es hub, bridge e switch sono allo stesso livello perché il livello 1 e 2 di OSI sono implementati nella scheda di rete

| Devices | Hub | Switch | Router | PC/Server |
| ---- | ---- | ---- | ---- | ---- |
| Hub | Cross | Cross | Straight | Straight |
| Switch | Cross | Cross | Straight | Straight |
| Router | Straight | Straight | Cross | Cross |
| PC/Server | Straight | Straight | Cross | Cross |

ATT connection automatico NON funziona spesso

Significato simboli PT:
- Triangolo verde: pronto
- Cerchio arancione: si sta configurando/sta imparando
- Rosso: è presente un errore

## Ping
Il link del router inizialmente resta rosso in quanto dobbiamo accendere esplicitamente la scheda di rete (`config` --> `portStatus on`)

Test di ping: `Simulation` --> Icona lettera chiusa `Add Simple PDU` 
In `Simulation`: `Show all/none` --> `Edit` filters per selezionare solo lo stretto necessario
Per resettare la simulazione: sotto `Scenario 0`, `Delete`
ATT inizialmente il ping potrebbe fallire perché le MAC table potrebbero essere vuote

Quando un dispositivo si accende, viene fatta un ARP request sul proprio indirizzo per verificare l unicità del proprio IP e per mettere nelle ARP table degli altri dispositivi la mia corrispondenza IP-MAC

ATT SE due PC hanno lo stesso IP, il ping ha successo 
![[Pasted image 20231027155658.png]]

1 switch = bridge per ogni endsystem + 1 hub
![[Pasted image 20231027155933.png]]

Perché alcune vote un cavo resta arancione?
Protocollo di Spanning Tree (livello 2): durante la fase di leaning dei bridge, viene imposta una struttura ad albero che permette di capire la topologia in modo da tagliare i loop 
Un triangolo di bridge non fa diventare tutti i cavi verdi, ma volontariamente viene disattivata un interfaccia di un bridge per evitare il loop
La stessa cosa accade anche con gli switch

Posso mettere IP in due reti diverse e se poi collego gli switch non si accorge dell'errore
Quando provo la simulazione tra i pc con i due indirizzi uguali, il ping funziona ma perché arriva a se stesso

## VLAN
- Configurazione VLAN da interfaccia:

Ad ogni LAN viene associato un nome e un numero
Aggiungere una nuova VLAN
1. Nello `Switch` --> `Config` --> `VLAN database`
2. Nello `Switch` --> `Config` --> nell'interfaccia che collega la VLAN allo switch, selezionare la VLAN inserita e mettere `on` l'interfaccia

ATT NON posso usare un solo cavo tra due switch che collegano PC di due VLAN, devo avere un cavo collegato tra gli switch per ogni VLAN

![[Pasted image 20240112113310.png]]

- Configurazione VLAN da CLI

Noi lavoreremo senza password
## Modalità CLI
Command Line Interface ha due livelli di accesso
- privilegiata/root SE termina col segno `#` es `Router#`
- utente SE termina col segno `>` es `Router>`

Se devi fare qualcosa come root, successivamente torna in modalità utente

Comandi utili

| Segnatura | Descrizione |
| ---- | ---- |
| `TAB` | suggerisce e completa |
| `?` | permette di avere i comandi/parametri possibili |
| `clean` | pulisce CLI |
| `no comandoEseguito` | rollback del comando eseguito |
| `exit` | tornare una "dir" sopra |
| `enable` | passa alla modalità privilegiata |
| `disable` | uscire dalla modalità privilegiata |
| `CTRL-SHIFT-6` | per fermare CLI (nel caso di commando errato entra in un loop) |
| `telnet` | permette di collegarsi ad un terminale remoto e di operare come se stessimo lavorando in presenza |
| `traceroute` | interfaccia del protocollo ICMP (lavora insieme a IP che notifica condizioni di errore), traccia il percorso verso un alias di un indirizzo per un massimo di 30 hop. `*` in traceroute vuol dire che ci siano degli errori o per nascondere il route se i dispositivi di rete sono stati settati per ciò |

| `show ?` in uno switch           | Descrizione                           |
| -------------------------------- | ------------------------------------- |
| `arp`                            | mostra l'arp table                    |
| `interfaces`                     | mostra le info di TUTTE le interfacce |
| `interfaces nomeInterfaccia n/k` | mostra le info dell'interfaccia       |
| `mac-address-table`                                 | mostra la tabella con i mac address e le VLAN                                      |

Aggiungere la VLAN nel database
1. Nella CLI come `#` --> `configure terminal` 
2. Ora siamo in `Device(config)#`, `vlan numeroVLAN`
3. Ora siamo in `Device(config-vlan)#`, `name NomeVLAN`

Configurare la VLAN dell interface
1. Nella CLI come `#` --> `configure terminal` 
2. Ora siamo in `Device(config)#`, `interface nomeInterfaccia n/k` 
3. Ora siamo in `Device(config-if)#`,  `switchport trunk allowed vlan add numeroVLAN`


## Subnetting
IPv4: 32bit unsigned long con dotted notation
Ogni ottetto non puo superare 255

Modo di assegnazione indirizzi
- classi vs CIDR
- subnetting

Class-based

| Indirizzi speciali | Significato |
| ---- | ---- |
| hostID = 0 | indirizzo base della rete |
| netID = 0 | indirizzo della stessa rete della sorgente |
| tutti 1 | broadcast sulla rete sorgente |
| hostID a tutti 1 | broadcast sulla rete destinataria |

| Classe | min       | max             | netID  | hostID |
| ------ | --------- | --------------- | ------ | ------ |
| A      | 1.0.0.0   | 127.255.255.255 | 7 bit  | 24 bit |
| B      | 128.0.0.0 | 191.255.255.255 | 14 bit | 16 bit |
| C       | 192.0.0.0          | 223.255.255.255                | 21 bit       | 8 bit       |

Usando $x$ bit per il netID avrò $32-x$ bit per l'hostID
MA cosi per percorrere la tabella di instradamento ci impiegherei in media $2^{32}/2 = 2^{31}$

L'indirizzo destinazione viene messo in AND bit a bit con la netmask: cancello bit a destra trovando il netID

Ricorda potenze di 2

| $2^7$   | $2^6$   | $2^5$   | $2^4$   | $2^3$   | $2^2$   | $2^1$   | $2^0$   |
| --- | --- | --- | --- | --- | --- | --- | --- |
|    128 | 64  | 32 | 16 | 8 | 4 | 2 | 1     |

ES Class 
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

CIDR
Indirizzo x.y.w.z/n con n il numero di bit usati per il netID
Per ogni subnet bisogna scegliere una potenza di 2 minima per indirizzare tutti i dispositivi, cioe end system + gateway + 1 broadcast + 1 base address

Best practice: il gateway ha sempre il primo o l'ultimo indirizzo usabile

Subnetting
Subnet mask: tutti bit a 1 in corrispondenza di network e subnet address e tutti 0 per l'host address

es ho una rete da /16, voglio suddividere in subnet ognuna da 100 host
Per l hostID ho bisogno di 7 bit --> 128 host circa
Per il netID restano 16-7 = 9 bit

es rete 192.168.20.96/27 
Rete verde: 4 host + 1 router + broadcast + base = 7 indirizzi 
3 bit -> rete /29 (32-3) -> netmask 255.255.255.11111000
Indirizzo base: 192.168.20.96 (.011 00000)
Broadcast: 192.168.20.103 (.01100 | 111)
Indirizzo min: 192.168.20.97
Indirizzo max: 192.168.20.102

Rete arancione: 2 host + 1 router + broadcast + base = 5 indirizzi 
3 bit -> rete /29 (32-3) -> netmask 255.255.255.11111000
Indirizzo base: 192.168.20.104
Broadcast: 192.168.20.111 (Indirizzo base + $2^n-1$)
Indirizzo min: 192.168.20.105
Indirizzo max: 192.168.20.110


Il campo CRC è il resto della divisione tra due polinomi rappresentanti dai dati/polinomioComunePerCRC 
10110 = $x^4 + x^2 + x$
SE i due resti non sono uguali, allora c è stata un errore


Proprietà aritmetica binaria
- Allineamento
Una rete di dimensione $2^n$ può iniziare solo a intervalli regolari multipli di $2^n$, cioè a posizioni pari a $k * 2^n$, 
Il primo indirizzo disponibile nello host address range deve essere composto da tutti 0 negli ultimi $n$ bit per qualsiasi sottorete

es n = 64 (taglia è il massimo numero di dispositivi)
può iniziare a 0, 64, 128, 192
n = 32
può iniziare a 0, 32, 64, 96, 128, 160, 192, 224

Double check:
- indirizzo base e l'indirizzo max DEVE essere pari
- indirizzo broadcast e l'indirizzo min DEVE essere dispari
- i netID delle diverse sottoreti sono sempre differenti in binario

es rete 192.168.20.96/27
- S1: 5 device + broadcast + base = 7 indirizzi = 3 bit

Posso partire da 96 perché è multiplo di 8 
netmask: 255.255.255. (.111|11|000)
indirizzo base: 192.168.20.96/29
broadcast: 192.168.20.103
indirizzo min: 192.168.20.97
indirizzo max: 192.168.20.102
Verifica min e max siano sulla stessa rete: 01100|001 e 01100|110 sono sulla stessa rete
Double check: 103 è dispari e 96 pari

- S2: 14 device + broadcast + base = 16 indirizzi = 4 bit
104 non è multiplo di 16 --> 112 è il primo multiplo di 16
netmask: 255.255.255.240 (.111|1|0000)
indirizzo base: 192.168.20.112/28
broadcast: 192.168.20.127
indirizzo min: 192.168.20.113
indirizzo max: 192.168.20.126
Verifica min e max siano sulla stessa rete: 011|1|0001 e 011|1|1110 sono sulla stessa rete

- Euristica

Si inizia dalla subnet piu grande e via via procedendo in ordine decrescente

es rete 192.168.20.96/27, prima S2 e POI S1 (14 > 5)
- S2: 14 device + broadcast + base = 16 indirizzi = 4 bit

netmask: 255.255.255.240
indirizzo base: 192.168.20.96/28
broadcast: 192.168.20.111
indirizzo min: 192.168.20.97
indirizzo max: 192.168.20.110

- S1: 5 device + broadcast + base = 7 indirizzi = 3 bit

netmask: 255.255.255.248
indirizzo base: 192.168.20.112/29
broadcast: 192.168.20.119
indirizzo min: 192.168.20.113
indirizzo max: 192.168.20.118


es riassuntivo
indirizzo base 10.11.160.0/24; 5 subnet collegate da un router
A 25 host
G 14 host
K 28 host
M 9 host
R 58 host

Usare la regola dell'euristica
- R 58 + base + broadcast + gateway = 61 -> 6 bit
Netmask: 255.255.255.192 (1100000)
indirizzo base: 10.11.160.0/26
indirizzo broadcast: 10.11.160.63
indirizzo min: 10.11.160.1
indirizzo max: 10.11.160.62

- K 28 + 3 = 31 -> 5 bit
Netmask: 255.255.255.224 (1110000)
indirizzo base: 10.11.160.64
indirizzo broadcast: 10.11.160.95/27
indirizzo min: 10.11.160.65
indirizzo max: 10.11.160.94

- A 25 + 3 = 28 -> 5 bit
Netmask: 255.255.255.224
indirizzo base: 10.11.160.96/27
broadcast: 10.11.160.127
indirizzo min: 10.11.160.97
indirizzo max: 10.11.160.126

- G 14 + 3 = 17 -> 5 bit
Netmask: 255.225.255.224
indirizzo base: 10.11.160.128/27
broadcast: 10.11.160.159
indirizzo min: 10.11.160.129
indirizzo max: 10.11.160.158

- M 9 + 3 = 12 -> 4 bit
Netmask: 255.255.255.240
indirizzo base: 10.11.160.160/28
broadcast: 10.11.160.175
indirizzo min: 10.11.160.161
indirizzo max: 10.11.160.174


## Configurazione router
NON collegare router direttamente con gli end system
Comandi CLI base

| Comando                | Descrizione                                           |
| ---------------------- | ----------------------------------------------------- |
| `traceroute x.y.z.w`   | consente di verificare il path verso una destinazione |
| `show ip bgp/ospf/rip` | mostra le tabelle di instradamento                    |
| `show dhcp`                        | mostra il range di indirizzi assegnabili da DHCP server                                                      |

Comandi CLI in `(config)`

| Comando         | Descrizione                            |
| --------------- | -------------------------------------- |
| `hostname Name` | permette di cambiare il nome dell host |
| `ip name x.y.z.w`                | permette di cambiare IP                                       |
I cambiamenti sono operativi quando premo `CTRL-Z`

Connessione VLAN con un router
![[Pasted image 20240113094049.png]]

Assumendo che lo switch abbia gia il VLAN database settato e i collegamenti con le subnet corretti, il collegamento tra switch e router deve avere tutte le VLAN a cui è collegato lo switch in trunk mode

![[Pasted image 20240113094256.png]]

Ora è necessario configurare il router, in particolare l'interfaccia collegata allo switch (Fa0/0)
In CLI
1. `enable`
2. `configure terminal`
3. Ora sono in `(config)`, eseguo `interface nomeInterfaccian/k.IDVLAN`
4. Ora sono in `(config-subif)`, eseguo `encapsulation dot1Q IDVLAN`
5. Eseguo `ip address indirizzoDaAssegnare subNetMask`
6. `CTRL-Z`

Risultato:
![[Pasted image 20240113094621.png]]

L'indirizzo da assegnare al router deve appartenere alla VLAN 20 e dovrà essere specificato come default gateway in ogni end system della VLAN
La subnet mask è presente in automatico in ogni end system delle VLAN in una loro interfaccia di rete

![[Pasted image 20240113095015.png]]

## DHCP
Aggiungiamo un end system con DHCP
Appena si collega ad una rete già esistente, si da un indirizzo casuale controllando se non sia già presente con un ARP request 
MA non appena compare un DHCP server, questo indirizzo casuale viene sostituito con quello dato dal server

Per farsi assegnare un IP da un DHCP
![[Pasted image 20240113100438.png]]

I server tipicamente non hanno indirizzi dinamici
Come settare il servizio DHCP:
Andare sul server -> `Services` -> `DHCP` -> ...
Parametri sbagliati da correggere:
- Default gateway
- Start IP address
- maximum number of users
OSS lo spazio di indirizzi per la VLAN in realtà questo contiene sia gli indirizzi statici che dinamici

![[Pasted image 20240113095919.png]]

Un DHCP è proxy quando non c è un server DCHCP in una rete, e quindi fa da DHCP server anche per quella rete 

Semplicemente si aggiunge un altro pool al DHCP server
Ora serve configurare il router con CLI configurando l'interfaccia della VLAN dove non c è il server

1. `enable`
2. `configure terminal`
3. Ora sono in `(config)`, eseguo `interface nomeInterfaccian/k.IDVLAN`
4. Ora sono in `(config-subif)`, eseguo `ip helper-address indirizzoDHCPServer`
5. `CTRL-Z`

## Configurazione Routing
- Rotte statiche

Per ogni router e per ogni destinazione nella rete non direttamente collegata al router

1. `enable`
2. Ora sono in `(config)`, eseguo `ip route IPDest netmask IPNextHop`

Per visualizzare routing table di un router, $lente$ -> `routing table`

- Rotte dinamiche

- RIP v1 (NON lo chiede)
- RIP v2

E' classless
ATT bisogna esplicitare di voler usare le v2
1. `enable`
2. `config term`
3. Ora sono in `(config)`, eseguo `router rip`
4. Ora sono in `(config-router)`, eseguo `version 2` (ATT NON si vede quale sia la version)
5. `network IPAdiacente` (non gli dico la netmask perche è collegato direttamente alla LAN e quindi conosco la netmask)

OGNI router deve avere la stessa versione
ATT in realta tra due router c è una rete, che richiedendo 2 dispositivi + base + broadcast, sara una /30 
quindi nelle interfacce dei due router dovro mettere l IP di questa sottorete
Per definire una /30, prima metto la netmask (quindi 255.255.255.252) e POI l IP

- OSPF

Passi
1. `enable`
2. `config term`
3. Ora sono in `(config)`, eseguo `router ospf 1`
4. Ora sono in `(config-router)`, eseguo `area 1 stub`
5. Eseguo `network indirizzoBase wildcard area 1`

Con wildcard = negazione della netmask
Per evitare flooding di pkt di link state (es nella mia VLAN o NAT):
1. `enable`
2. `config term`
3. Ora sono in `(config)`, eseguo `router ospf 1`
4. Ora sono in `(config-router)`, eseguo `passive interface nomeInterfaccian/k`

Stessa cosa da fare in RIP per evitare inoltre di DV (SE esistono subif per VLAN bisogna farle se quelle NON su l'interfaccia fisica)


## Access Control List
Sul router esiste la possibilità di limitare il traffico in ingresso/in uscita a/da una rete

- ACL standard ID 1-99: si puo solo selezionare lo IP sorgente dei pacchetti da NON far passare
- ACL extended ID 100-199: si possono selezionare
	- protocollo di livello nerwork o trasporto
	- indirizzo sorgente e/o destinazione (any come wildcard)
	- insiemi di porte
	- modalità permit/deny
	- established: segmenti TCP con ACK flag = 1
- ACL named extended ID 100-199: possibilità di modifica successiva

1. Creazione ACL

Paradigma
`access-list IDACL permit|deny protocolName`
`sourceIP|wildcard [eq|lt|gt|neq|range IDPorta]` `destinationIP|wildcard [eq|lt|gt|neq|range IDPorta] [established] [log]`

es 
access-list 110 permit TCP any host 192.168.200.200 eq 80
"ACL 110 permette segmenti TCP da qualsiasi sorgente con destinazione 192.168.200.200 e porta uguale a 80"

access-list 110 deny ICMP any any
"ACL 110 nega pacchetti ICMP da qualsiasi host a qualunque altro"

ATT le regole vengono analizzate in ordine, se non fa match allora vale l implicita deny IP any any

2. Applicazione ACL a interfaccia

Entro nella configurazione dell interface: interface nomeInterfaccian/k
Eseguo `ip access-group IDACL out|in`

Double check:
- `show ip access-lists`: mostra le regole della access list 
- `show ip interface NomeInterfaccian/k.VLAN`: mostra le informazioni dell interfaccia tra cui `Outgoing/Inbound access lists is...`

es 
`ip access-list extended 100`
`permit TCP any host 192.168.0.1 eq www`
`deny IP any any`
`exit`
`interface fastEthernet 0/0`
`ip access-group 100 in`

"ACL 100 permette l’ingresso dall’interfaccia fastEthernet 0/0 di tutti i segmenti TCP generati da qualunque sorgente, e destinati allo host 192.168.0.1 su porta 80"
"ACL 100 non accetta alcun altro tipo di traffico IP"
nessuno degli end system della VLAN può accedere ad un server web pubblico a causa dell `in`

Soluzione: 
`ip access-list extended 100`
`15 permit TCP any any established`

## NAT
Per la traduzione degli indirizzi è necessario
1. configurare le interfacce di ingresso e uscita alla rete abilitando il servizio NAT 
	1. `enable`
	2. `config term`
	3. `interface nomeInterfaccia n/k`
	4. `ip nat inside`
	5. `exit`
	6. `interface nomeInterfaccia a/b`
	7. `ip nat outside`
	8. `exit`
2. creare una ACL che determini quali indirizzi devono essere tradotti
	`access-list IDACL permit ip any any`
3. configurare il router stabilendo per quale traffico devono essere tradotti gli indirizzi e quale è l'indirizzo presentato all'esterno
	`ip nat inside source list IDACL interface nomeInterfacciaIN n/k`

es 
![[Pasted image 20240114094235.png]]
`ip nat inside source list 110 interface fastEthernet 0/0`
"Quando si fa NAT degli indirizzi interni si usa come criterio degli indirizzi da tradurre nella ACL 110 e si traducono gli indirizzi usando l'indirizzo IP dell'interfaccia fastEterhent 0/0"
Ora il ping da interno a esterno funziona MA il server web pubblico non è accessibile da Internet

es accesso a servizi interni pubblici
port forwarding: mapping tra (indirizzo esterno e porta) e (indirizzo interno e porta servizio) all'interno del router gateway
`ip nat inside source static tcp IPInterno portaInterna IPEsterno portaEsterna`
`ip nat inside source static tcp 192.168.0.1 80 10.0.0.254 80`