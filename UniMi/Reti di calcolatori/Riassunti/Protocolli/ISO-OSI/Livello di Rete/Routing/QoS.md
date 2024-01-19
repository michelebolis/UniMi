I router devono rispettare i `QoS - Quality of Service`
Estratto il packet classifier (`TOS bit`) dall header, viene fatto uno scheduling sulla coda in base alla politica di scheduling
Le code di I/O per ogni porta di I/O sono diverse in base alla qualità di servizio che vogliono offrire, in particolare un router ha tante code quanti sono i servizi che puo offrire

Una `congestione` avviene quando la domanda per una risorsa della rete eccede il livello che concede.
SE un burst di pacchetti arriva al router su un numero differenziato di linee di input, l'output si congestionerà SE il rate d'arrivo è maggiore di quello di uscita
Soluzione: [[Tecnica Token Bucket]]

| Tipo di traffico - Esigenze  | Affidabilita | Delay | Jitter | Banda |
| ------------------ | ------------ | ----- | ------ | ----- |
| email              | Alta         | Basso | Basso  | Basso |
| web (come FTP)     | Alta         | Basso | Basso  | Medio |
| FTP                | Alto         | Basso | Basso  | Medio |
| audio streaming    | Basso        | Medio | Alto   | Basso |
| video streaming    | Basso        | Alto      | Alto       | Alto      |
| Internet telephone | Basso        |       |        |       |
| video conference   | Basso        | Alto      | Alto       | Alto      |

Jitter: tempo da quando il messaggio parte a quando arriva al destinatario
NON tutti i pacchetti hanno lo stesso ritardo

[[Audio streaming]]

La coda di output dei router è gestita con due blocchi
- Servizio affidabile: solitamente pacchetti generati dal [[QoS (L3) da TCP]]
- Servizio sensibile al delay, [[QoS (L3) da UDP]]

[[Differentiated services]]