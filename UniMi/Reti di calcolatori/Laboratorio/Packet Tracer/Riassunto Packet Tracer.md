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

