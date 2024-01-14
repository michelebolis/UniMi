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
Lato server

Lato client

1. scambio dati come byte stream
2. chiusura