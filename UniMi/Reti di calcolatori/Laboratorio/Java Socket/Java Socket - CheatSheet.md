UDP 

| Fasi | Classe/metodi |
| ---- | ---- |
| Connessione | Server: `DatagramSocket(N)`; Client: `DatagramSocket()` |
| Init Destinazione | `InetSocketAddress isa = new InetSocketAddress("localhost", 1000);` `packet.setSocketAddress(isa);` |
| Input | `InputStreamReader tastiera = new InputStreamReader(System.in);`<br>`BufferedReader reader = new BufferedReader(tastiera);` |
| Inviare | `DatagramPacket(buffer, buffer.length)`; `socket.send(packet)` |
| Ricevere | `socket.receive(buffer)` |
| Parsare | `String(buffer, 0, packet.getLength())` |
| Mittente | `packet.getSocketAddress() ` |

TCP iterativo

| Fasi | Classe/metodi |
| ---- | ---- |
| Creazione Server | `ServerSocket socket = new ServerSocket(portaServer);`<br>`Socket fromClient;` `fromClient = socket.accept();` |
| Creazione Client | `Socket socket = new Socket();`<br>`InetAddress host = InetAddress.getLocalHost();`<br>`InetSocketAddress isa = new InetSocketAddress(host, portaServer);`<br>`InetSocketAddress myisa = new InetSocketAddress(host, 0);`<br>`socket.bind(myisa);`<br>`socket.connect(isa);` |
| Input | `InputStreamReader tastiera = new InputStreamReader(System.in);`<br>`BufferedReader reader = new BufferedReader(tastiera);` |
| Inviare | `OutputStream toSend = socket.getOutputStream();`<br>`toSend.write(buffer, 0, buffer.length);` |
| Ricevere | int letti = 0;<br>`InputStream fromCl = socket.getInputStream();`<br>`letti = fromCl.read(rec_buffer);` |
| Parsare | `String(buffer, 0, buffer.length)` |
Struttura:
```java
try{
	socket = new ServerSocket();
	while(true){
		fromClient = socket.accept();
		while(true){
			...
		}
		fromClient.close()
	}
}catch(...){
	...
}finally {
	try {
		socket.close();
	} catch (Exception e) {
		e.printStackTrace();
	}
}
```

TCP concorrente

Struttura:
```java
ArrayList<Socket> sClient = new ArrayList<Socket>(max);
try{
	socket = new ServerSocket();
	int clientTimeout = 1000;
	int i = 0;
	int index = 0;
	while(true){
		try {
			sServer.setSoTimeout(10000);
			while (index < max) {
				sClient.add(sServer.accept());
				index++;
			}
		} catch (SocketTimeoutException e) {
			System.out.println("Timeout");
		} catch (IOException e) {
			e.printStackTrace();
		}
		while(index > 0){
			try{
				sClient.get(i).setSoTimeout(clientTimeout);
				while(true){
					...
				}
			}catch(SocketTimeoutException e){
				...
			}catch(Exception e){
				sClient.get(i).close();
				sClient.remove(i);
				index--;
				break;
			}
		}
		i = index != 0 ? (i + 1) % index : 0;

	}
}catch(...){
	...
}finally {
	try {
		socket.close();
	} catch (Exception e) {
		e.printStackTrace();
	}
}
```