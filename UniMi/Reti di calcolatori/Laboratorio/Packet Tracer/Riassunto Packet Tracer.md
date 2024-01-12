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
- indirizzo base DEVE essere pari
- indirizzo broadcast DEVE essere dispari

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

