Traffico est-ovest: all'interno del data center, quindi tra i server
Traffico nord-sud: con l'esterno, quindi tra il data center e i client

Il server deve esistere a un indirizzo facilmente determinabile 
Il client si presenta con il proprio indirizzo al server nel momento in cui lo contatta

socket definita da una quintupla 
`<protocollo, IP(src), porta(src), IP(dest), port(dest)>`

Il protocollo viene definito alla creazione della socket

Indirizzo host
`InetAddresses` è una classe di libreria standard di Java

Metodi utili
- conversione da nome simbolico a indirizzo numerico
```java
InetAddress InetAddress.getByName(hostName)
```
- Conversione da nome simbolico a tutti gli indirizzi associati
```java
InetAddress[] InetAddress.getAllByName(hostName)
```
- Indirizzo del local host
```java
InetAddress InetAddress.getLocalHost()
```
- estrarre l'indirizzo IP
```java
byte[] ia.getAddress()
```
- estrarre l'indirizzo IP decimale puntato dalla struttura
```java
String InetAddress.getHostAddress()
```

OSS InetAddress netAddress.getByName("localhost")  127.0.0.X indirizzo di loopback usato in fase di bootstrap (NON USARE perche non arriva mai al livello 3 ma torna indietro)

es 
```java
System.out.println("Un indirizzo di " + name);

InetAddress ia = InetAddress.getByName(name);

byte[] address = ia.getAddress();

System.out.println((address[0] & 0xff) + "." + (address[1] & 0xff) + "." + (address[2] & 0xff) + "." + (address[3] & 0xff));

for (InetAddress ia : ias) {
	System.out.println(ia.getHostAddress());
}
```

Costruzione dell'indirizzo per la socket
Oltre all'indirizzo host abbiamo bisogno del numero di porta 
- per il server il numero di porta è noto
- per il client è scelto dal SO

classe InetSocketAddress ha come costruttori
- `InetSocketAddress(InetAddress a, int port)`
- `InetSocketAddress(String hostname, int port)`
- `InetSocketAddress(int port)`
Getter associati:
- `InetAddress InetSocketAddress.getAddress()`
- `String InetSocketAddress,getHostName()`
- `int InetSocketAddress.getPort()`

Tipo di servizio
- connection-oriented: trasferimento di stream di byte. Caratteristiche
	- garanzia di ordine all'arrivo dei byte
	- non viene preservato il confine dei messaggi
	- PUO anche essere affidabile, SE uso TCP
- connection-less: trasferimento di datagram
	- best-efford MA preservo il confine dei messaggi: UDP/IP
	- PUO anche essere affidabile

Primitive di servizio TCP
Per ogni connessione TCO ricorda un connection record
lato src client: connect (active open)
lato dst server: listen (passive open) e accept

Fasi connection-oriented
![[Pasted image 20240114104112.png]]
Per server concorrente, interleaving
Per server multi-processo: delega a server secondari

1. creazione della socket: cioè creazione di una struttura del processo per gestire il punto terminale del canale di comunicazione
```java
Socket sClient = new Socket();
```
2. binding: gestione indirizzi host+porta client/server
```java
Socket sClient = new Socket();
try {
	InetAddress ia = InetAddress.getLocalHost();
	InetSocketAddress isa = new InetSocketAddress(ia, 0);
	sClient.bind(isa);
	System.out.println("Porta allocata: " + sClient.getLocalPort());
} catch (Exception e) {
	e.printStackTrace();
}
```
SE il numero di porta è a 0, in realtà viene scelta dal SO (non va bene chiaramente per il server)
Lo stato della socket può essere mostrato con `netstat` o `lsof`
3. connessione client e server
Il metodo `socket.connect(socketAddressServer)` esegue three-way handshake e anche il bind implicito

4. scambio dati come byte stream
La rete memorizza i byte come big endian cioe dal byte piu significativo al meno significativo
La rete ha solo conoscenza dei byte e poi il programmatore dovra convertirli in numeri, struct...
Caso byte stream: programmatore deve gestire il formato PDU
- SE PDU di taglia costante, lettura di un numero fisso di byte
- SE PDU di taglia variabile: lettura dei byte dell'header e successivamente dei dati per la lunghezza indicata nell'header

TUTTI i dati devono essere convertiti a/da sequenza di byte
- caratteri: cast a tipo byte
- stringhe: fare `String.replace()` per sostituire `\r` o `\n`
- numeri: formato dipendente dall'architettura quindi si usa il toString delle varie classi es `Double.toString(num)` e analogamente `Double.parseDouble(stringa)`
- dati strutturati: conversione dei singoli campi o `Serializable`

Metodi utili
- `String trim()`: elimina gli spazi iniziali e finali in una stringa
- `String split(String regex, int limit)`: spezza la stringa eliminando il separatore
- classe `StringTokenizer`: costruttore per sottostringhe delimitate da separatore con metodo `nextToken()`

Getter dei due stream (unidirezionali)
- `InputStream socket.getInputStream()`
- `OutputStream socket.getOutputStream()`

Metodi associati:
- `write(s)` passa i dati al livello di Trasporto
- `read()`, primitive bloccante finche non legge dei byte
	- SE il canale è chiuso dal peer read() si sblocca tornando <0

5. chiusura
metodo `close()` non permette un ulteriore utilizzo del canale
ATT nel server considerare QUALE socket si vuole chiudere
Per garantire che tutte le socket siano chiuse, si può usare `close` in blocco

Fasi connection-less
   1-2. Creazione socket lato client
```java
sClient = new DatagramSocket(); //esegue anche binding implicito
```
In questo caso client e server sono simmetrici, non ci sono due classi diverse
3. Scambio di dati
Invio dati
```java
DatagramPacket(byte[] buf, int offset, int length, InetAddress address, int port);
DatagramSocket.send(DatagramPacket dp);
```
Ricezione dati: bloccante finche non ricevo l'intero datagram
```java
DatagramSocket.receive(DatagramPacket dp);
```

In generale
1. Lanciare server cosi da vedere la porta assegnata dal SO
2. Lanciare il client passando come argomento la porta


Il server deve gestire piu client efficientemente
- Server iterativo
	- SE il server è libero, il client può entrare in servizio immediatamente
	- SE il server è occupato, 
		- SE la coda è piena, il servizio viene rifiutato
		- ALTRIMENTI si mette in coda e aspetta
	Problemi associati:
	- gestione della coda
	- attesa indefinita, starvation
	- attacchi Denial of Service DoS
	L'associazione è completamente definita alla costruzione della socket e non puo associarsi ad altri client
- Server concorrente; sfrutta tempi morti di un client (I/O bound) per servirne altri
	Su socket con associazione parzialmente definita si possono accettare altre richieste di connessione
	Problemi associati: gestione difficile e non scalabile
- Server multiprocesso: piu entita distinte e contemporanemanete attive quindi piu flussi paralleli per la fornitura del servizio
	Problemi associati:
	- gestione limitatezza e carico di ogni thread
	- ogni thread gestisce in modo iterativo o concorrente
