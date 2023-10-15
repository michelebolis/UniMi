- Information hiding: 
Incapsulare le informazioni rendendole disponibili solo attraverso delle interfacce. Nascondere anche il funzionamento del sistema ai livelli superiori

- Stratificazione della rete (semplice)
Mappatura 1:1 tra i 2 host che devono usare gli stessi protocolli
A livello piu alto abbiamo i nostri utenti
Mittente:
- La richiesta viene incapsulata nel livello 5. Utilizza un protocollo di livello 5 (i due livelli sono peer) per aggiungere alla richiesta un header di livello 5. Passa al livello sottostante il messaggio
- Il livello 4 espone delle interfacce/primitive al livello 5 (o un servizio affidabile o un servizio veloce ma non affidabile) che sceglie. Nell'header aggiunge quale servizio ha scelto il livello 5 
- Il livello 3 è in grado di fare l'instradamento, capire se c è un percorso di consegnare il messaggio 
- Il livello 2 offro anch esso un servizio affidabile e uno non affidabile, che sceglie il livello 3
- Il livello 1 richiede a che velocita vuole il trasferimento e aggiunge anche informazioni in coda
Ricevente:
- Accordo tra i 2 livello 1 è la forma d onda per capire quando il bit è 1 o 0. Il livello 1 utilizza l head del livello 1, che contiene informazioni di interesse per quel livello (es interpretazione codifica). Passa quindi al livello superiore il resto del messaggio
- Livello 2 controlla la correttezza
- Livello 3 controlla se l indirizzo è corretto
- Livello 4 controlla il servizio richiesto e se è stato rispettato 
- Livello 5 la richiesta viene processata e passata all applicativo del destinatario. Qui si torna ad avere il pacchetto originario

NIC Network Interface Card
Mittente dal livello 5 a 1 aggiunge gli header ai payload, mentre lato destinatario dal livello 1 a 5 viene usato e tolto gli header


Due modalita di utilizzo di protocollo
- Servizi orientati alla connessione: fare una connessione significare istaurare un canale (setup), il dialogo e infine una fase di rilascio. 
- Servizi senza connessione: appena ho il dato lo mando, senza contrattare i QoS

Standard:
- [[Reti di calcolatori/Riassunti/ISO-OSI|ISO-OSI]]
- [[Reti di calcolatori/Riassunti/TCP-IP|TCP-IP]]

Trasporto e Internet implementato nel SO
Ente di standardizzazione IEEE 802.
802.3 LAN
802.11 WiFi
802.15 Bluethoot
SE cambiano i protocolli, NON devono cambiare le interfacce tra i livelli